---
name: xyzrender-skill
description: Publication-quality molecular graphics rendering using xyzrender. Use when the user needs to create high-quality figures (SVG, PNG, PDF, GIF) for molecular structures, orbitals, surfaces, or animations from XYZ, PDB, Gaussian, ORCA, and other chemical file formats.
---

# Xyzrender Skill

## Overview
This skill provides a structured approach for using the `xyzrender` tool to create publication-quality molecular graphics. It handles everything from basic ball-and-stick models to complex electronic surfaces and animations.

## Core Capabilities

### 1. Basic Molecule Rendering
For simple visualization of a molecular structure.
```bash
xyzrender molecule.xyz -o output.png
```

### 2. Publication-Quality Figures (Recommended)
Use the `paton` preset for high-quality, glossy molecular models.
```bash
xyzrender molecule.xyz --config paton --hy -o figure.svg
```
*Tip: Use SVG for vector graphics that can be further edited in tools like Inkscape or Illustrator.*

### 3. Transition States and Special Interactions
Render dashed bonds for transition states or non-covalent interactions (NCI).
```bash
# Automated TS bond detection
xyzrender ts_geometry.xyz --ts -o ts_figure.png

# Automated NCI detection
xyzrender complex.xyz --nci -o nci_figure.png
```

### 4. Molecular Surfaces and Orbitals
Render electronic structure data from Gaussian/ORCA output or `.cube` files.
```bash
xyzrender mol.xyz orbital.cube --iso 0.05 --surf-style solid -o orbital.png
```

### 5. High-Quality Animations
Generate rotating GIFs or vibrational modes.
```bash
# Rotation GIF
xyzrender molecule.xyz --gif-rot -go rotation.gif --frames 60

# Vibrational Mode (from QM output)
xyzrender orca.out --mode 1 --gif -go vibration.gif
```

## Detailed Guides
- **Styles & Presets**: See [references/styles.md](references/styles.md) for a list of all visual styles.
- **Advanced Features**: See [references/advanced.md](references/advanced.md) for surfaces, annotations, and high-resolution output.

## Workflow: Creating a Publication-Ready Figure

1. **Identify the Input**: Determine the file type (XYZ, PDB, Gaussian, ORCA, etc.).
2. **Select a Style**: Use `--config paton` for most publications, or `--config flat` for technical diagrams.
3. **Decide on Elements**: Should hydrogens be shown (`--hy`)? Are there lone pairs or NCIs to show?
4. **Choose Format**: Use `.svg` for highest quality vector output or `.png --dpi 300` for high-res raster.
5. **Post-Processing (Optional)**: If you need to add custom arrows or labels not supported by the tool, export to SVG.
