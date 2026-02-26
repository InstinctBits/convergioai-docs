# Convergio AI Documentation

Official documentation for [Convergio AI](https://github.com/InstinctBits/convergioai) — architecture, APIs, setup guides, and developer reference.

**Live site:** [docs.instinctbits.com](https://docs.instinctbits.com)

## Development

### Prerequisites

- Python 3.10+
- pip

### Local preview

```bash
pip install -r requirements.txt
mkdocs serve
```

Open [http://localhost:8000](http://localhost:8000) in your browser.

### Build

```bash
mkdocs build
```

### Deployment

The site deploys automatically to GitHub Pages on every push to `main` via GitHub Actions. No manual deployment needed.

## Project structure

```
docs/
├── index.md                 # Landing page
├── getting-started/         # Setup, quickstart, configuration
├── platform/                # Architecture, core concepts
├── api/                     # API reference
├── guides/                  # Deployment, best practices
├── sdks/                    # SDK documentation
├── changelog.md             # Release history
└── assets/                  # Images, CSS, JS
```

## Brand hierarchy

- **Organization:** [Digitech Nomads](https://digitechnomads.com)
- **Project:** Convergio AI
- **Produced by:** [Instinct Bits Lab](https://instinctbits.com)

## License

[MIT](LICENSE)
