# Farmer Wiki

Welcome to wiki documentation hub. This wiki serves as a centralized knowledge base for Farmer members working with HPC systems and computational resources.

## 1. About Us

Our group focuses on computational research leveraging high-performance computing infrastructure. We primarily work with the **Saga HPC cluster** at SIGMA2/NRIS for large-scale computational tasks.


### Team Information
- **Project Leads**: Tuyen, Dat
- **Team Members**: Binh, Son, Vy, Ty


### What we do

- Develop and optimize deep learning models for genome language tasks
- Sequence to function prediction using deep learning
- Sequence to gene expression modeling
- Variant impact prediction
- Single cell and multi-omics data modeling
- Bioinformatics tool development

## 2. Lab Resources

### Computing Infrastructure
- **Primary System**: Saga HPC Cluster (SIGMA2/NRIS)
- **Access**: Project account `nn9780k`

### GitHub Repository

- **GitHub Repo**: [farmer-vn](https://github.com/farmer-vn)
- **Wandb**: [wandb account](https://wandb.ai/datngu)

### Quick Links

| Resource | Description | Link |
|----------|-------------|------|
| **Saga Login** | SSH access to cluster | `ssh username@saga.sigma2.no` |
| **Project Directory** | Shared project space | `/cluster/projects/nn9780k` |
| **SIGMA2 Docs** | Official documentation | [documentation.sigma2.no](https://documentation.sigma2.no/) |

## 3. Getting Started

New to the lab? Follow these steps:

### 3.1 Get Access

   - Request Saga account through project leader [Tuyen]
   - Request access to GitHub repo [Dat]

### 3.2 [Saga Setup](guides/saga.md)

   - Set up two-factor authentication
   - Configure SSH keys
   - [Click here to read Saga guide](guides/saga.md) for setup instructions

### 3.3 Start Computing

   - Submit test jobs to familiarize yourself with SLURM
   - Monitor resource usage with `dusage` and `cost`
   - Follow best practices outlined in our guides

## 4. Resources Statistics

!!! info "Current Resources"
    - **Storage Quota**: Check with `dusage -p nn9780k`
    - **CPU Hours**: Check with `cost -p nn9780k`
    - **Active Projects**: [List your current projects]


## 5. External Resources

### Official Documentation
- [SIGMA2/NRIS Documentation](https://documentation.sigma2.no/)
- [Saga Technical Details](https://documentation.sigma2.no/hpc_machines/saga.html)
- [SLURM Documentation](https://slurm.schedmd.com/)

### Useful Tools
- [MkDocs Material](https://squidfunk.github.io/mkdocs-material/) - This wiki's framework
- [Conda Documentation](https://docs.conda.io/)
- [Git Documentation](https://git-scm.com/doc)

---

<small>Last updated: {{ git_revision_date_localized }}</small>
