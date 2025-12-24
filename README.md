# HPC Lab Wiki

[![Deploy MkDocs site to Pages](https://github.com/farmer-vn/wiki/actions/workflows/pages.yml/badge.svg)](https://github.com/farmer-vn/wiki/actions/workflows/pages.yml)

A comprehensive documentation site for working with HPC (High-Performance Computing) clusters, built with MkDocs Material theme.

🌐 **Live Site**: [https://farmer-vn.github.io/wiki](https://farmer-vn.github.io/wiki)

## Why MkDocs?

✅ **Simple Markdown files** - All documentation is in `docs/*.md` files  
✅ **Easy editing** - Team members can view and edit files directly  
✅ **Beautiful web interface** - Material theme with search, navigation, dark mode  
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

```markdown
# My New Guide

This is my content...
```

3. Add it to the navigation in `mkdocs.yml`:

```yaml
nav:
  - Home: index.md
  - HPC Guides:
    - Saga Cluster: guides/saga.md
    - New Cluster: guides/new-cluster.md  # Add this line
## Project Structure

```
wiki/
├── docs/                      # All Markdown documentation files
│   ├── index.md              # Home page (lab mapper)
│   ├── guides/               # HPC guides directory
│   │   └── saga.md           # Saga cluster guide
│   └── CONTRIBUTING.md       # Contributing guide
├── mkdocs.yml                # MkDocs configuration
├── requirements.txt          # Python dependencies
├── .github/
│   └── workflows/
│       └── pages.yml         # Auto-deployment workflow
├── serve-mkdocs.sh           # Local server script
└── README.md                 # This file
``` └── workflows/
│       └── pages.yml         # Auto-deployment workflow
├── serve-mkdocs.sh           # Local server script
└── README.md                 # This file
```

## MkDocs Features

### Material Theme Features

- 🔍 **Instant search** - Fast client-side search
- 🌓 **Dark/Light mode** - Automatic theme switching
- 📱 **Mobile responsive** - Works on all devices
- 📝 **Edit on GitHub** - Direct links to edit pages
- 🔄 **Last updated** - Git revision dates on each page
- 🎨 **Syntax highlighting** - Beautiful code blocks
- 📑 **Tabs** - Organize content in tabs
- 💡 **Admonitions** - Callouts, tips, warnings

### Example Features Usage

**Admonitions:**
```markdown
!!! tip "Pro Tip"
    This is a helpful tip for users!

!!! warning
    Be careful with this command!
```

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

## About Saga

Saga is a supercomputer operated by SIGMA2/NRIS, located at NTNU in Trondheim, Norway. It provides approximately 140 million CPU hours per year and features:

- 364 compute nodes
- 16,064 CPU cores
- 32 NVIDIA GPUs (P100 and A100)
- 6.5 PB parallel file system capacity

## Local Development

To build and preview the site locally:

### Prerequisites

- Ruby 3.0 or higher (Ruby 3.3 recommended)
- Bundler

### Quick Setup (macOS with Homebrew)

```bash
# Install Ruby 3.3
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
