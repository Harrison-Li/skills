# Advanced Xyzrender Features

Use these flags and patterns for complex publication-level figures.

## 1. Transition States and NCI
Automatically detects and renders special bond types.
- `--ts`: Renders dashed/dotted lines for bonds that are breaking or forming. Requires a transition state geometry or Gaussian/ORCA output.
- `--nci`: Automatically detects non-covalent interactions (e.g., H-bonds) and renders them as dashed lines.
- `--dashed-bonds <indices>`: Explicitly render specific bonds as dashed (e.g., `--dashed-bonds 1-2,5-8`).

## 2. Molecular Surfaces and Orbitals
Render electronic structure data from `.cube` files.
- **Isosurface**: `xyzrender molecule.xyz orbital.cube --iso 0.05`
- **Color-mapped surface**: Map property (e.g., ESP) from one cube file onto an isosurface of another: `xyzrender molecule.xyz density.cube --esp esp.cube --iso 0.001`
- **Style**: Choose surface style: `--surf-style [solid|mesh|contour|wire|dot]`

## 3. Annotations (Distances, Angles)
Add quantitative data directly to the figure.
- **Distances**: `--dist 1 2` (Distance between atoms 1 and 2).
- **Angles**: `--angle 1 2 3` (Angle 1-2-3).
- **Dihedrals**: `--dihed 1 2 3 4` (Torsion angle).
- **Labels**: `--label 1 "C1" --label 5 "N5"` (Add custom text labels to specific atoms).

## 4. High-Resolution Output
Always specify `-o` with a file extension to determine the format.
- **SVG (Vector)**: Recommended for highest quality and post-processing: `xyzrender mol.xyz -o fig.svg`
- **PNG (Raster)**: Use for quick viewing or presentations: `xyzrender mol.xyz -o fig.png --dpi 300`
- **PDF**: `xyzrender mol.xyz -o fig.pdf`

## 5. Animations
Create GIFs for trajectories or rotations.
- **Rotation GIF**: `xyzrender mol.xyz --gif-rot -go rotation.gif --frames 60`
- **Trajectory GIF**: `xyzrender trajectory.xyz --gif -go trajectory.gif` (Requires multi-frame XYZ).
- **Vibration GIF**: Render a vibrational mode from a QM output file: `xyzrender orca.out --mode 1 --gif -go vib.gif`
