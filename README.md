<p align="center">
  <img src="assets/isologo_white.png" alt="Cyberwheel Logo" height="100"/>
</p>

# CYBERWHEEL

Open-source electric unicycle hardware and firmware.

## 📖 Documentation

Visit our documentation site: **[https://rubenayla.github.io/cyberwheel/](https://rubenayla.github.io/cyberwheel/)**

## Purpose
Make electric unicycles that are reliable for everyday use: waterproof, impact-resistant, durable over time, and easy to repair.

For this, create an open-source community to design both the Hardware and Firmware, so they can be repaired and modified, free of proprietary restrictions.

[Video Pitch: https://youtu.be/mN5FoosNMC0](https://youtu.be/mN5FoosNMC0)

## Repository Structure

```
cyberwheel/
├── docs/              # MkDocs documentation source
├── cad/               # CAD files and designs
├── releases/          # Release versions (cw1.0, cw1.1, etc.)
├── battery/           # Battery design files and images
├── assets/            # Images and media
└── references/        # Reference materials and datasheets
```

## Development

### Build documentation locally

```bash
# Install dependencies with uv
uv sync

# Serve docs locally
uv run mkdocs serve

# Build static site
uv run mkdocs build
```

Documentation is automatically deployed to GitHub Pages on push to main.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
