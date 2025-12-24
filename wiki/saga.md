
This guide provides essential instructions for team members working on the Saga HPC cluster at SIGMA2. Follow these best practices to ensure efficient use of shared computational resources.

## SSH Login and Connection Setup

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
```

This configuration maintains a master connection that subsequent SSH sessions can reuse for 8 hours without re-authentication. After this, simply connect using:

```bash
ssh saga
```

## Project Directory Structure

Our project is located at `/cluster/projects/nn9780k`. Each team member should create and maintain their own personal directory:

```bash
# Navigate to project directory
cd /cluster/projects/nn9780k

# For example create your personal directory (if it doesn't exist)
mkdir -p dat    # For Dat Nguyen
mkdir -p binh   # For Binh Le
```

**Important**: Keep all your work, datasets, and results within your personal directory to maintain organization and avoid conflicts.

## Conda Environment Setup

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
conda install pytorch numpy pandas

```

## File Transfer with SFTP

### Uploading Files to Saga

Use `sftp put` command to upload files:

```bash
# Connect to Saga via SFTP
# Since you have configured ssh config file, you can simply run
sftp saga

# Upload a single file
put /local/path/to/file.txt /cluster/projects/nn9780k/<your_name>/path/to/destination/

# Upload an entire directory recursively
put -r /local/path/to/directory /cluster/projects/nn9780k/<your_name>/path/to/destination/

```

### Downloading Files from Saga

Use `sftp get` command to download files:

```bash
# Connect to Saga via SFTP
sftp saga

# Download a single file
get /cluster/projects/nn9780k/<your_name>/results.csv /local/download/path/

# Download an entire directory recursively
get -r /cluster/projects/nn9780k/<your_name>/output_dir /local/download/path/
```

## Submitting Jobs to Saga

### Understanding Partitions

**CPU Partitions**: Use for non-GPU tasks

- `normal` - Standard CPU jobs
- `bigmem` - High memory requirements (up to 4TB)

**GPU Partitions**:

- `accel` - Intel CPU with 4× Tesla P100 (16GB each)
- `a100` - AMD CPU with 4× A100 (80GB each)

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
#SBATCH --mail-user=your.email@outlook.com
#SBATCH --mail-type=ALL

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

## Resource Monitoring

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

## Best Practices

1. **Always activate your conda environment** before running jobs
2. **Test jobs with short time limits** before submitting long runs
3. **Monitor disk usage regularly** with `dusage` to avoid quota issues
4. **Request appropriate resources** - over-requesting wastes project quota
5. **Use project area for shared data** to avoid duplication across user directories
6. **Clean up completed jobs** - remove unnecessary output files to save space

For additional help, consult the [official Saga documentation](https://documentation.sigma2.no) or contact support@sigma2.no.
