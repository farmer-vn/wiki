---
hide:
  - navigation
  - toc
---

<style>
.md-content {
  padding: 0 !important;
}

/* Hero Banner Styling - Material Design Style */
.hero-banner {
  position: relative;
  width: 100vw;
  margin-left: calc(-50vw + 50%);
  min-height: 70vh;
  background-image: url('figures/hero-background.png');
  background-size: cover;
  background-position: center center;
  background-repeat: no-repeat;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 6rem 2rem;
  overflow: hidden;
}

.hero-banner::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: linear-gradient(to bottom, rgba(0, 0, 0, 0.4), rgba(0, 0, 0, 0.5));
}

.hero-content {
  position: relative;
  z-index: 1;
  text-align: center;
  color: white;
  max-width: 52rem;
}

.hero-content h1 {
  font-size: 3.8rem;
  font-weight: 700;
  margin-bottom: 1.5rem;
  line-height: 1.1;
  color: white !important;
  letter-spacing: -0.01em;
}

.hero-content p {
  font-size: 1.5rem;
  margin-bottom: 2.5rem;
  opacity: 0.95;
  line-height: 1.5;
  color: white;
}
.hero-buttons {
  display: flex;
  gap: 1rem;
  justify-content: center;
  flex-wrap: wrap;
}
.hero-buttons a {
  display: inline-block;
  padding: 0.9rem 2.2rem;
  font-size: 1.1rem;
  font-weight: 600;
  text-decoration: none;
  border-radius: 0.3rem;
  transition: all 0.2s;
}
.hero-buttons .button-primary {
  background-color: white;
  color: var(--md-primary-fg-color);
}
.hero-buttons .button-primary:hover {
  transform: translateY(-2px);
  box-shadow: 0 4px 12px rgba(0,0,0,0.3);
}
.hero-buttons .button-secondary {
  border: 2px solid white;
  color: white;
  background: transparent;
}
.hero-buttons .button-secondary:hover {
  background: rgba(255,255,255,0.1);
}
.md-typeset h2 {
  text-align: center;
  font-size: 2.2rem;
  margin-bottom: 3rem;
  opacity: 0.95;
  line-height: 1.6;
  color: white;
}

.hero-buttons {
  display: flex;
  gap: 1rem;
  justify-content: center;
  flex-wrap: wrap;
}

.hero-buttons a {
  display: inline-block;
  padding: 1rem 2.5rem;
  font-size: 1.1rem;
  font-weight: 600;
  text-decoration: none;
  border-radius: 0.3rem;
  transition: all 0.2s ease;
}

.hero-buttons .button-primary {
  background-color: white;
  color: #1a1a1a;
  box-shadow: 0 2px 8px rgba(0,0,0,0.2);
}

.hero-buttons .button-primary:hover {
  transform: translateY(-2px);
  box-shadow: 0 4px 16px rgba(0,0,0,0.3);
}

.hero-buttons .button-secondary {
  border: 2px solid white;
  color: white;
  background: transparent;
}

.hero-buttons .button-secondary:hover {
  background: rgba(255,255,255,0.15);
  transform: translateY(-2px);
}

.md-typeset h2 {
  text-align: center;
  font-size: 2.2rem;
  font-weight: 700;
  margin: 3rem 0 2rem;
}

.content-wrapper {
  max-width: 60rem;
  margin: 0 auto;
  padding: 2rem 1rem;
}
</style>

<div class="hero-banner">
  <div class="hero-content">
    <h1>Farmer Wiki</h1>
    <p>Computational research leveraging high-performance computing infrastructure for genomics and bioinformatics</p>
    <div class="hero-buttons">
      <a href="guides/saga/" class="button-primary">Get Started →</a>
      <a href="https://github.com/farmer-vn" class="button-secondary">View on GitHub</a>
    </div>
  </div>
</div>

<div class="content-wrapper" markdown>

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

</div>