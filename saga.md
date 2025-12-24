
This guide provides essential instructions for team members working on the Saga HPC cluster at SIGMA2. Follow these best practices to ensure efficient use of shared computational resources.

## 1. SSH Login and Connection Setup

### Initial Login

Connect to Saga using SSH with two-factor authentication:

```bash
ssh {your_username}@saga.sigma2.no
```

You'll be prompted for your password followed by a 2FA code from your authenticator app.

### Persistent SSH Connection Configuration

To avoid entering 2FA codes repeatedly, configure SSH connection multiplexing by adding this to your `~/.ssh/config` file:

```bash
Host saga
    HostName saga.sigma2.no
    User {your_username}
    ControlMaster auto
    ControlPath ~/.ssh/%r@%h:%p
    ControlPersist 8h

# or newer syntax

Host saga
    HostName saga.sigma2.no
    User {your_username}
    ControlMaster auto
    ControlPath ~/.ssh/controlmasters/%r@%h:%p
    ControlPersist 8h

```

This configuration maintains a master connection that subsequent SSH sessions can reuse for 8 hours without re-authentication. Note: You'll need to create the control masters directory first with `mkdir -p ~/.ssh/controlmasters`. After this, simply connect using:

```bash
ssh saga
```

## 2. Project Directory Structure

Our project is located at `/cluster/projects/nn9780k`. Each team member should create and maintain their own personal directory:

```bash
# Navigate to project directory
cd /cluster/projects/nn9780k

# For example create your personal directory (if it doesn't exist)
mkdir -p dat    # For Dat Nguyen
mkdir -p binh   # For Binh Le
```

**Important**: Keep all your work, datasets, and results within your personal directory to maintain organization and avoid conflicts.

## 3. Conda Environment Setup

### Installing Conda

Since `$HOME` has only a 20 GB quota, install conda in your project directory to avoid space issues:

```bash
# Download Miniconda installer
cd /cluster/projects/nn9780k/<your_name>
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh

# Install Miniconda
bash Miniconda3-latest-Linux-x86_64.sh -b -p /cluster/projects/nn9780k/<your_name>/miniconda3

# Initialize conda
source /cluster/projects/nn9780k/<your_name>/miniconda3/etc/profile.d/conda.sh
conda init bash

# Clean up installer
rm Miniconda3-latest-Linux-x86_64.sh

```

### Configure Conda Cache Location

Redirect conda's package cache to your project directory:

```bash
# Create conda cache directory
mkdir -p /cluster/projects/nn9780k/<your_name>/.conda_cache

# Configure conda to use this cache
# Conda cache and env locations
export CONDA_PKGS_DIRS=/cluster/projects/nn9780k/<your_name>/.conda_cache
export CONDA_ENVS_PATH=/cluster/projects/nn9780k/<your_name>/miniconda3/envs
```

### Example of Creating Environments

Create isolated environments for different projects:

```bash
# Create a new environment
conda create -n {your_env} python={python_version}

# Activate environment
conda activate {your_env}

# Install packages
pip install numpy pandas

```

## File Transfer

### Recommended Method: SFTP

SFTP is recommended for its ease of use and straightforward interface. If you've configured your SSH config file as shown above, file transfers are simple:

```bash
# Connect to Saga via SFTP
sftp saga

# Upload a single file
put /local/path/to/file.txt /cluster/projects/nn9780k/<your_name>/

# Upload an entire directory recursively
put -r /local/path/to/directory /cluster/projects/nn9780k/<your_name>/

# Download a single file
get /cluster/projects/nn9780k/<your_name>/results.csv /local/download/path/

# Download an entire directory recursively
get -r /cluster/projects/nn9780k/<your_name>/output_dir /local/download/path/

# Exit SFTP session
bye
```

**Why SFTP:**
- Simple and intuitive commands
- Works seamlessly with SSH config
- No complex syntax to remember
- Widely supported across all platforms

### Alternative: rsync

For advanced users, `rsync` offers additional features like incremental transfers:

```bash
# Upload a file to Saga
rsync --info=progress2 -a /local/path/to/file.txt {your_username}@saga.sigma2.no:/cluster/projects/nn9780k/<your_name>/

# Upload a directory to Saga (note the trailing slash)
rsync --info=progress2 -a /local/path/to/directory/ {your_username}@saga.sigma2.no:/cluster/projects/nn9780k/<your_name>/directory/

# Download from Saga to your local machine
rsync --info=progress2 -a {your_username}@saga.sigma2.no:/cluster/projects/nn9780k/<your_name>/results/ /local/download/path/
```

**rsync advantages:**
- Skips files that already exist and haven't changed
- Can resume interrupted transfers
- Faster for many small files

### Transferring Between Clusters

For transfers between Saga and other NRIS clusters (Betzy, Olivia), set up SSH key pairs between the clusters to avoid needing password + OTP for each transfer. See the [official SSH documentation](https://documentation.sigma2.no/getting_started/ssh.html) for details.

## 4. Submitting Jobs to Saga

### Understanding Partitions

**CPU Partitions**: Use for non-GPU tasks

- `normal` - Standard CPU jobs (192 GiB memory per node)
- `bigmem` - High memory requirements:
  - Medium memory: 384 GiB (28 nodes)
  - Big memory: 3 TiB (8 nodes)
  - Huge memory: 6 TiB (2 nodes)

**GPU Partitions**:

- `accel` - Intel Xeon-Gold 6126 CPU with 4× NVIDIA P100 GPUs (16GB each) and 384 GiB memory
- `a100` - AMD EPYC 7542 CPU with 4× NVIDIA A100 GPUs (80GB each) and 1 TiB memory

### Requesting Resources

- RAM: Specify memory in GB (e.g., `--mem=128G`)
- CPUs: Specify number of CPU cores (e.g., `--cpus-per-task=8`)
- GPUs: Specify number of GPUs (e.g., `--gpus=1`)
- Time: Specify maximum job duration (e.g., `--time=10-00:00:00` for 10 days)
- Nodes: Usually set to 1 unless you need multiple nodes (e.g., `--nodes=1`)
- Job-name: A descriptive name for your job (e.g., `--job-name=training_job`)
- Output: Specify output log file (e.g., `--output=job_log.%j.out`)

When submitting jobs, specify resources based on your needs:

### Job Submission Template

Create a SLURM batch script (e.g., `train_job.sh`):

```bash
#!/bin/bash
#SBATCH --account=nn9780k
#SBATCH --job-name=job_name
#SBATCH --output=job_name_log.%j.out
#SBATCH --nodes=1
#SBATCH --mem=128G
#SBATCH --partition=a100
#SBATCH --gpus=1
#SBATCH --cpus-per-task=8
#SBATCH --time=10-00:00:00
# Note: Email notifications are currently DISABLED on all NRIS clusters
# #SBATCH --mail-user=your.email@outlook.com
# #SBATCH --mail-type=ALL

set -e

# # Activate conda environment
# source /cluster/projects/nn9780k/<your_name>/miniconda3/etc/profile.d/conda.sh
# conda activate {your_env}

# python train_script.py --arg1 value1 --arg2 value2

echo "Training complete!"
```

### Submitting and Managing Jobs

```bash
# Submit job
sbatch train_job.sh

# Check job status
squeue -u $USER

# View job details
scontrol show job <job_id>

# Cancel a job
scancel <job_id>
```

### Choosing CPU vs GPU

**Use CPU partitions** when:

- Running data preprocessing or post-processing
- Performing statistical analysis
- Running jobs that don't benefit from GPU acceleration

**Use GPU partitions** when:

- Training deep learning models
- Running GPU-accelerated computations
- Using frameworks like PyTorch, TensorFlow with CUDA

## 5. Resource Monitoring

### Check Disk Quota

Monitor your disk usage to avoid quota exceeded errors:

```bash
# Check your disk usage across all areas
dusage

# Check specific project quota
dusage -p nn9780k
```

### Understanding Disk Quota Output

The output shows space used, soft quota, hard quota, and file count limits.

- Since **SAGA limit both quota and file counts**, be mindful of the number of files you create, DO NOT create millions of small files, especially with `zarr` or similar formats.

- **DO NOT** keep multiple copies of large datasets (like training data) in your personal directory. The project area is shared, so store common datasets there to save space. You can access data of any team member from the project directory.

### Check CPU Hour Quota

Monitor your computational budget:

```bash
# View quota for all your projects
cost

# View quota for specific project
cost -p nn9780k

# See detailed usage by user
cost --details
```

**Note**: You are billed for requested resources, not actual usage (except time). If you request 5 days but use 2 hours, billing starts immediately but returns unused quota after completion.

### Understanding Billing

On Saga, jobs are billed based on both CPU and memory:

- **Normal partition**: Memory factor is 0.2577031 units per GiB
- **Bigmem partition**: Memory factor is 0.1104972 units per GiB

Always request only what you need to conserve project resources.

### Check Project Access

List all projects you can access:

```bash
projects
```

This returns project IDs like `nn9780k` that you can use in your job submissions.

## 6. Best Practices

1. **Always activate your conda environment** before running jobs
2. **Test jobs with short time limits** before submitting long runs
3. **Monitor disk usage regularly** with `dusage` to avoid quota issues
4. **Request appropriate resources** - over-requesting wastes project quota
5. **Use project area for shared data** to avoid duplication across user directories
6. **Clean up completed jobs** - remove unnecessary output files to save space

## 7. Additional Resources

- [Official Saga Documentation](https://documentation.sigma2.no/hpc_machines/saga.html)
- [Getting Started Guide](https://documentation.sigma2.no/getting_started/getting_started.html)
- [SSH Configuration Guide](https://documentation.sigma2.no/getting_started/ssh.html)
- [File Transfer Guide](https://documentation.sigma2.no/getting_started/file_transfer.html)
- [Job Submission Guide](https://documentation.sigma2.no/jobs/submitting.html)
- [Storage Quota Guide](https://documentation.sigma2.no/files_storage/quota.html)

For additional help, contact support through the [NRIS support portal](https://documentation.sigma2.no/getting_help/support_line.html).
