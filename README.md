# Tips and Tricks Documentation

Welcome to the Tips and Tricks Documentation repository! This is a comprehensive collection of technical documentation, guides, and how-tos for various technologies and systems.

## 📚 Table of Contents

- [About](#about)
- [Documentation Categories](#documentation-categories)
- [Getting Started](#getting-started)
- [Contributing](#contributing)
- [GitHub Pages](#github-pages)

## About

This repository serves as a centralized knowledge base for technical documentation, configuration guides, and troubleshooting tips. All documentation is written in Markdown and automatically published to GitHub Pages using Jekyll.

## Documentation Categories

### 🌐 Network

Network-related configuration guides and documentation for various networking hardware and software.

- **[Netgear SmartSwitch Configuration](Network/Netgear-GS728TP.md)** - Complete guide for Netgear GS728TP series smart switches including SSH setup, key management, and configuration

### 🐧 Linux

Linux system administration guides, tools, and configuration documentation.

- **[Storj Bucket Mount using Goofys](Linux/Storj-Bucket-Mount-using-Goofys.md)** - Step-by-step guide to mount Storj.io S3-compatible buckets on Proxmox using goofys

## Getting Started

### Browsing Documentation

You can browse the documentation in two ways:

1. **GitHub Repository**: Navigate through the folders and files directly on GitHub
2. **GitHub Pages Site**: Visit the published documentation site (see [GitHub Pages](#github-pages) section)

### Local Development

To run this documentation site locally:

```bash
# Clone the repository
git clone https://github.com/mkopnsrc/Tips-and-Tricks-Docs.git
cd Tips-and-Tricks-Docs

# Install Jekyll (if not already installed)
gem install bundler jekyll

# Serve the site locally
jekyll serve

# Visit http://localhost:4000 in your browser
```

## Contributing

Contributions are welcome! If you have tips, tricks, or documentation to share:

1. Fork this repository
2. Create a new branch for your documentation (`git checkout -b add-new-guide`)
3. Add your documentation in the appropriate category folder
4. Use clear, descriptive filenames with `.md` extension
5. Include relevant screenshots, code examples, and links
6. Commit your changes (`git commit -m 'Add guide for XYZ'`)
7. Push to your branch (`git push origin add-new-guide`)
8. Open a Pull Request

### Documentation Guidelines

- Use Markdown format for all documentation
- Include a clear title and description at the top of each document
- Use appropriate heading levels (H1 for title, H2 for major sections)
- Add code blocks with syntax highlighting where applicable
- Include screenshots or diagrams when helpful
- Link to official documentation sources when referencing external resources
- Keep documentation up-to-date and review periodically

## GitHub Pages

This repository is automatically deployed to GitHub Pages using Jekyll. The deployment is handled by a GitHub Actions workflow that:

- Triggers on every push to the `main` branch
- Builds the Jekyll site
- Deploys to GitHub Pages

The published site is available at: `https://mkopnsrc.github.io/Tips-and-Tricks-Docs/`

### How It Works

The deployment uses the [Jekyll GitHub Pages workflow](.github/workflows/jekyll-gh-pages.yml) which:
1. Checks out the repository
2. Configures GitHub Pages
3. Builds the site with Jekyll
4. Uploads the built site as an artifact
5. Deploys to GitHub Pages environment

---

## 📝 License

This documentation repository is provided as-is for informational purposes.

## 🤝 Support

If you have questions or need help with any of the documentation:

- Open an [Issue](https://github.com/mkopnsrc/Tips-and-Tricks-Docs/issues) for questions or clarifications
- Submit a [Pull Request](https://github.com/mkopnsrc/Tips-and-Tricks-Docs/pulls) for corrections or improvements

---

**Last Updated**: 2025-10-16