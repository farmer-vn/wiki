---
hide:
  - navigation
  - toc
---

<style>
.md-typeset h1 {
  text-align: center;
  font-size: 3em;
  font-weight: 700;
  margin-bottom: 0.5em;
}
.md-typeset .hero-subtitle {
  text-align: center;
  font-size: 1.5em;
  color: var(--md-default-fg-color--light);
  margin-bottom: 2em;
}
.md-typeset .hero-buttons {
  text-align: center;
  margin: 2em 0 4em 0;
}
.md-typeset .hero-buttons .md-button {
  margin: 0.5em;
  font-size: 1.1em;
  padding: 0.8em 2em;
}
</style>

# Farmer Wiki

<p class="hero-subtitle">
  Computational research leveraging high-performance computing infrastructure for genomics and bioinformatics
</p>

<div class="hero-buttons" markdown>
  [Get Started :octicons-arrow-right-24:](guides/saga.md){ .md-button .md-button--primary }
  [View on GitHub :fontawesome-brands-github:](https://github.com/farmer-vn){ .md-button }
</div>

---

## :material-target: What We Do

<div class="grid cards" markdown>

-   :material-dna:{ .lg .middle } __Genome Language Models__

    ---

    Develop and optimize deep learning models for understanding genomic sequences and their functional implications

-   :material-chart-line:{ .lg .middle } __Function Prediction__

    ---

    Sequence-to-function prediction using state-of-the-art deep learning architectures

-   :material-code-braces:{ .lg .middle } __Gene Expression__

    ---

    Sequence-to-gene expression modeling to understand regulatory mechanisms

-   :material-alert-decagram:{ .lg .middle } __Variant Analysis__

    ---

    Predict and analyze the impact of genetic variants on biological function

-   :material-cellphone:{ .lg .middle } __Multi-Omics__

    ---

    Single cell and multi-omics data integration and modeling

-   :material-tools:{ .lg .middle } __Tool Development__

    ---

    Build bioinformatics tools and pipelines for the research community

</div>

---

## :material-account-group: Our Team

<div class="grid" markdown>

<div markdown>

### The Team

- **Leads**: Tuyen, Dat
- **Core Members**: Binh, Thuan, Son, Vy, Ty

### Infrastructure

- **Primary System**: Saga HPC Cluster (SIGMA2/NRIS)
- **Project Account**: `nn9780k`
- **GitHub**: [farmer-vn](https://github.com/farmer-vn)
- **Weights & Biases**: [wandb.ai/datngu](https://wandb.ai/datngu)

</div>

<div markdown>

### Quick Access

| Resource | Link |
|----------|------|
| **Saga Login** | `ssh username@saga.sigma2.no` |
| **Project Directory** | `/cluster/projects/nn9780k` |
| **Official Docs** | [documentation.sigma2.no](https://documentation.sigma2.no/) |
| **Storage Check** | `dusage -p nn9780k` |
| **CPU Hours** | `cost -p nn9780k` |

</div>

</div>

---

## :material-rocket-launch: Getting Started

<div class="grid cards" markdown>

-   :material-account-key:{ .lg .middle } __1. Get Access__

    ---

    Request Saga account through project leader **Tuyen** and GitHub access through **Dat**

-   :material-server:{ .lg .middle } __2. Setup Environment__

    ---

    Configure SSH keys, two-factor authentication, and follow our [Saga Setup Guide](guides/saga.md)

-   :material-play-circle:{ .lg .middle } __3. Start Computing__

    ---

    Submit test jobs with SLURM, monitor resources, and follow best practices

</div>

---

## :material-bookshelf: Resources

!!! tip "Current Usage Statistics"
    
    Check your resource usage anytime:
    
    ```bash
    # Storage quota
    dusage -p nn9780k
    
    # CPU hours consumed
    cost -p nn9780k
    ```

### External Documentation

<div class="grid cards" markdown>

-   :material-file-document:{ .lg .middle } __HPC Documentation__

    ---

    [:octicons-arrow-right-24: SIGMA2/NRIS Docs](https://documentation.sigma2.no/)
    
    [:octicons-arrow-right-24: Saga Technical Details](https://documentation.sigma2.no/hpc_machines/saga.html)
    
    [:octicons-arrow-right-24: SLURM Documentation](https://slurm.schedmd.com/)

-   :material-application:{ .lg .middle } __Development Tools__

    ---

    [:octicons-arrow-right-24: MkDocs Material](https://squidfunk.github.io/mkdocs-material/)
    
    [:octicons-arrow-right-24: Conda Docs](https://docs.conda.io/)
    
    [:octicons-arrow-right-24: Git Documentation](https://git-scm.com/doc)

</div>

---

<p style="text-align: center; color: var(--md-default-fg-color--light); margin-top: 3em;">
  <small>Last updated: {{ git_revision_date_localized }}</small>
</p>
