# Xyzrender Styles and Presets

`xyzrender` provides several built-in styles to quickly achieve different visual looks.

## Common Presets

- **default**: Standard ball-and-stick model with CPK colors.
- **flat**: 2D-like appearance with flat colors and no gradients. Good for diagrams.
- **paton**: PyMOL-inspired style with glossy spheres and cylinders. Highly recommended for publications.
- **skeletal**: Thin bonds and small atoms, focusing on the molecular framework.
- **bubble**: Large, overlapping atoms with no bonds shown (space-filling).
- **tube**: Cylindrical bonds with no spheres for atoms.
- **wire**: Simple line representation of bonds.
- **graph**: Mathematical graph representation (nodes and edges).

## Usage
Apply a preset using the `--config` flag:
```bash
xyzrender molecule.xyz --config paton
```

## Customization via Flags
- `--hy`: Include hydrogens (often hidden by default in some styles).
- `--no-bonds`: Hide bonds.
- `--no-atoms`: Hide atom spheres.
- `--rad-scale <float>`: Scale all atom radii.
- `--bond-scale <float>`: Scale all bond widths.
- `--color-scheme <name>`: Use predefined color palettes (e.g., `jmol`, `cpk`, `qualitative`).
