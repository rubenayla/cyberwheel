# CYBERWHEEL Project Memory

## Project Overview
Open-source electric unicycle (EUC) hardware and firmware project focused on reliability, safety, and repairability.

## Documentation Setup
- Using MkDocs with Material theme
- Dependencies managed with `uv` and `pyproject.toml`
- Documentation source in `docs/`
- Auto-deploys to GitHub Pages via GitHub Actions on push to main
- Site URL: https://rubenayla.github.io/cyberwheel/

## Repository Structure
```
cyberwheel/
├── docs/                          # MkDocs documentation
│   ├── assets/
│   │   ├── logo/                  # Branding (isologo_black.png)
│   │   ├── images/
│   │   │   ├── battery/           # Battery diagrams
│   │   │   └── prototypes/        # Prototype photos
│   │   └── datasheets/            # PDFs
│   ├── index.md                   # Home page
│   ├── getting-started/
│   │   ├── requirements.md        # Design requirements
│   │   └── testing.md             # Test procedures
│   ├── design/
│   │   └── battery.md             # Battery system design
│   ├── releases/
│   │   ├── cw1.0.md               # Laser cut chassis version
│   │   └── cw1.1.md               # Multi-part chassis
│   └── references.md
├── cad/                           # CAD files (outside docs)
├── battery/                       # Battery source files
├── releases/                      # Release versions with CAD
│   ├── cw0.x/
│   ├── cw1.0 (improved, helmet lid)/  # Has laser cut chassis
│   └── cw1.1 (multi part chassis)/
├── assets/                        # Root assets (for GitHub README)
├── references/                    # Datasheets and references
├── mkdocs.yml                     # MkDocs configuration
├── pyproject.toml                 # Python dependencies (uv)
└── .github/workflows/deploy-docs.yml
```

## Key Design Decisions

### Documentation
- Assets are self-contained in `docs/assets/` (not symlinked)
- Use relative paths for images/files within docs
- Logo: `docs/assets/logo/isologo_black.png` (60px height, black version for visibility)
- Site name: "Cyberwheel" (not "CYBERWHEEL")

### Branding
- Use "Cyberwheel" (not uppercase) in titles
- Logo in header navigation only, not in page content

### Technical Specifications
- **Target wheel size**: 16" rim (actual outer diameter with tire: ~460-470mm, ~18-19")
- **Wheel perimeter**: ~1.48m (with tire)
- **Battery**: 20S2P pack, Molicel INR-21700-P42A cells, 84V, 60-90A
- **Motor**: C38 or C30 hollow bore motor (C38 high torque preferred)
- **Target specs**: 50kmh, 80kg rider, hill climbing, no suspension

### Firmware Choice
- **VESC with Refloat package** (not Balance or Float)
- Refloat is the current best option for EUC self-balancing
- Provides best control for safety features: gradual tiltback, emergency modes

## Project Philosophy
- **No rider blame for cutouts** - Design must prevent cutouts at system level
- Foolproof, weatherproof design
- Sealed electronics and battery
- No BMS discharge cutoff (monitoring + ESC limits only)
- Gradual leanback based on voltage, current, temperature
- State machine: OFF, Balancing, Charging, Emergency

## Release Versions
- **cw1.0 (improved, helmet lid)**: Laser cut steel chassis version
- **cw1.1 (multi part chassis)**: Multi-part design

## Commands
```bash
# Serve docs locally
uv run mkdocs serve

# Build static site
uv run mkdocs build

# Install dependencies
uv sync
```

## Notes
- Prototype image in home page shows early version
- Waiting for laser-cut chassis for next iteration
- Need to tune PID controller after hardware update
