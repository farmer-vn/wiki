# Farmer Wiki

[![Deploy MkDocs site to Pages](https://github.com/farmer-vn/wiki/actions/workflows/pages.yml/badge.svg)](https://github.com/farmer-vn/wiki/actions/workflows/pages.yml)

A comprehensive documentation hub for computational genomics research using HPC systems, built with MkDocs Material theme.

🌐 **Live Sites**: 
- [https://farmer-vn.github.io/wiki](https://farmer-vn.github.io/wiki)
- [https://wiki.dattn.com](https://wiki.dattn.com) (custom domain)

## About

The Farmer Wiki serves as a centralized knowledge base for team members working on computational research leveraging high-performance computing infrastructure. We focus on:

- Developing deep learning models for genome language tasks
- Sequence-to-function and gene expression prediction
## Contents

All documentation files are in the `docs/` directory:

- **[docs/index.md](docs/index.md)** - Beautiful home page with hero section and feature cards
- **[docs/guides/saga.md](docs/guides/saga.md)** - Saga HPC Cluster comprehensive guide
- **[docs/figures/](docs/figures/)** - Images and logos (including Farmer logo)
- **[docs/CONTRIBUTING.md](docs/CONTRIBUTING.md)** - Contribution guidelines
✅ **Easy editing** - Team members can view and edit files directly  
✅ **Beautiful interface** - Professional design with search, navigation, dark/light mode  
✅ **Icon support** - 10,000+ Material icons, Octicons, and FontAwesome icons  
✅ **Fast** - Static site generation with instant preview  
✅ **Git-friendly** - Track changes, collaborate via PRs

## Contents

All documentation files are in the `docs/` directory:

- **[docs/index.md](docs/index.md)** - Home page (lab mapper & resources)
- **[docs/guides/saga.md](docs/guides/saga.md)** - Saga HPC Cluster Guide
- **[docs/CONTRIBUTING.md](docs/CONTRIBUTING.md)** - Contribution guidelines

## Local Development

### Prerequisites

- Python 3.x (you already have this via conda)

### Quick Start

```bash
# Clone the repository
git clone https://github.com/farmer-vn/wiki.git
cd wiki

# Install MkDocs and dependencies
pip install -r requirements.txt

# Start the development server
./serve-mkdocs.sh
# OR
mkdocs serve

# Open http://localhost:8000 in your browser
```

### Live Reload

MkDocs has built-in live reload! Just edit any `.md` file in the `docs/` directory and your browser will automatically refresh.

## Adding New Pages

1. Create a new Markdown file in the appropriate `docs/` subdirectory:

```bash
# Example: Add a new HPC guide
touch docs/guides/new-cluster.md

# Example: Add a tutorial
mkdir -p docs/tutorials
touch docs/tutorials/my-tutorial.md
```

2. Edit the file with regular Markdown:

## Project Structure

```
wiki/
├── docs/                      # All Markdown documentation files
│   ├── index.md              # Home page with hero section
│   ├── guides/               # HPC guides directory
│   │   └── saga.md           # Saga cluster guide
│   ├── figures/              # Images and logos
│   │   └── farmer_log.jpeg   # Farmer logo
│   └── CONTRIBUTING.md       # Contributing guide
├── mkdocs.yml                # MkDocs configuration
├── requirements.txt          # Python dependencies
├── .github/
│   └── workflows/
│       └── pages.yml         # Auto-deployment workflow
├── serve-mkdocs.sh           # Local server script
└── README.md                 # This file
```entation files
│   ├── index.md              # Home page (lab mapper)
│   ├── guides/               # HPC guides directory
│   │   └── saga.md           # Saga cluster guide
## MkDocs Features

### Material Theme Features

- 🔍 **Instant search** - Fast client-side search
- 🌓 **Dark/Light mode** - Automatic theme switching
- 📱 **Mobile responsive** - Works on all devices
- 📝 **Edit on GitHub** - Direct links to edit pages
- 🔄 **Last updated** - Git revision dates on each page
- 🎨 **Syntax highlighting** - Beautiful code blocks
- 🎯 **Icon support** - 10,000+ Material icons, Octicons, FontAwesome
- 📑 **Tabs** - Organize content in tabs
- 💡 **Admonitions** - Callouts, tips, warnings
- 🎴 **Grid cards** - Beautiful card layouts
- 🖼️ **Custom logo** - Farmer logo in header

### Example Features Usage

**Icons:**
```markdown
:material-rocket-launch: :octicons-arrow-right-24: :fontawesome-brands-github:
```

**Grid Cards:**
**Code blocks with copy button:**
````markdown
```bash
ssh user@saga.sigma2.no
```
````

**Tabs:**
```markdown
=== "macOS"
    Instructions for macOS

=== "Linux"
    Instructions for Linux
```

## Deployment

### GitHub Pages (Automatic)

The site automatically deploys to GitHub Pages when you push to the `main` branch:

1. Make your changes locally
2. Commit and push:
   ```bash
   git add .
   git commit -m "Update documentation"
   git push origin main
   ```
3. GitHub Actions will build and deploy automatically
4. Site will be live at both:
   - https://farmer-vn.github.io/wiki/
   - https://wiki.dattn.com/

### Custom Domain Setup

The site is configured with a custom domain `wiki.dattn.com`:

1. **DNS Configuration** (Porkbun):
   ```
   Type: CNAME
   Host: wiki
   Answer: farmer-vn.github.io
   TTL: 600
   ```

2. **CNAME File**: Already configured in `docs/CNAME`

3. **GitHub Settings**: Custom domain configured in repository settings with HTTPS enabled

## About Saga HPC

Saga is a supercomputer operated by SIGMA2/NRIS, located at NTNU in Trondheim, Norway:

- **Compute Nodes**: 364 nodes
- **CPU Cores**: 16,064 cores  
- **GPUs**: 32 NVIDIA (P100 16GB & A100 80GB)
- **Storage**: 6.5 PB parallel file system
- **Capacity**: ~140 million CPU hours per year
- **Project Account**: nn9780k
brew install ruby@3.3

# Add to your shell profile (~/.zshrc or ~/.bash_profile)
echo 'export PATH="/opt/homebrew/opt/ruby@3.3/bin:$PATH"' >> ~/.zshrc
source ~/.zshrc

# Install Bundler
gem install bundler
```

### Running the Site

```bash
# Clone the repository
git clone https://github.com/farmer-vn/wiki.git
cd wiki

# Install dependencies (first time only)
bundle install

# Start the development server
./serve.sh
# OR
bundle exec jekyll serve

# Open http://localhost:4000/wiki in your browser
```

### Troubleshooting

**Build warnings about layouts**: These are normal when using a remote theme. The layouts are fetched from the Just the Docs theme repository and will work correctly on GitHub Pages.

**Ruby version issues**: Make sure you're using Ruby 3.0+. Check with `ruby -v`. On macOS, the system Ruby is outdated (2.6), so install a newer version via Homebrew.

**"cannot load such file" errors**: Remove `Gemfile.lock` and run `bundle install` again.

### Building for production

```bash
bundle exec jekyll build
```

The site will be generated in the `_site` directory.

## GitHub Pages Deployment

This site is automatically deployed to GitHub Pages using GitHub Actions.

### Setup (First Time)

1. Go to repository **Settings** → **Pages**
2. Under **Build and deployment**, select:
   - Source: **GitHub Actions**
3. Push to `main` branch - the site will auto-deploy

The site will be live at: `https://farmer-vn.github.io/wiki/`

### How It Works

- Push changes to `main` branch
- GitHub Actions runs `mkdocs build`
- Generated `site/` folder deploys to GitHub Pages
- Usually takes 1-2 minutes

## Editing Documentation

### For Team Members

1. **Edit files directly**: All docs are in `docs/*.md`
2. **Use any editor**: VS Code, GitHub web editor, or plain text editor
3. **Regular Markdown**: No special syntax required
4. **Commit and push**: Changes go live automatically

### Workflow

```bash
# Edit a file
vim docs/saga.md

# Preview locally (optional)
mkdocs serve

# Commit and push
git add docs/saga.md
git commit -m "Update Saga guide"
git push
```

## Technology Stack

- **Static Site Generator**: [MkDocs](https://www.mkdocs.org/) 1.6+
- **Theme**: [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/) 9.7+
- **Hosting**: GitHub Pages
- **CI/CD**: GitHub Actions

## Additional Resources

- [MkDocs Documentation](https://www.mkdocs.org/)
- [Material for MkDocs Documentation](https://squidfunk.github.io/mkdocs-material/)
- [SIGMA2/NRIS Official Documentation](https://documentation.sigma2.no/)
- [Saga Technical Details](https://documentation.sigma2.no/hpc_machines/saga.html)

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Support

For HPC cluster support, contact the [NRIS support portal](https://documentation.sigma2.no/getting_help/support_line.html).

For issues with this wiki, please [open an issue](https://github.com/farmer-vn/wiki/issues) on GitHub.
