# GCode-Fiddler User Guide

## Overview

GCode-Fiddler optimizes CNC G-code files by intelligently adjusting feed rates at critical points such as corners and arc transitions, reducing machine vibration and improving surface finish quality.

## Getting Started

### Installation

1. Download the appropriate version for your operating system from the [releases page](https://github.com/3DTek-xyz/GCode-Fiddler-Releases/releases)
2. Extract the archive to your preferred location
3. Run the executable (no installation required)

### Basic Usage

#### GUI Mode

1. **Launch** GCode-Fiddler
2. **File → Open** to load your G-code file
3. **View** the original toolpath in the preview window
4. **Optimize** using the toolbar button or menu
5. **Compare** original vs optimized using the comparison view
6. **Save** the optimized G-code

#### Command Line Mode

```bash
# Basic optimization
./gcode-fiddler input.nc

# With custom parameters
./gcode-fiddler input.nc --corner-smoothing --corner-speed 1500 --corner-angle 25

# Analysis only (no modifications)
./gcode-fiddler input.nc --analyze-only
```

## Optimization Parameters

### Corner Smoothing
- **Corner Angle Threshold**: Minimum angle (degrees) to trigger slowdown
- **Corner Speed**: Feed rate for approaching corners (mm/min)
- **Approach Distance**: Distance before corner to start slowing (mm)

### Arc Processing
- **Min Arc Radius**: Radius threshold for arc speed limiting (mm)
- **Max Arc Speed**: Maximum speed for small radius arcs (mm/min)

## Best Practices

1. **Always preview** optimizations before saving
2. **Use endpoint validation** to ensure accuracy
3. **Start with conservative settings** and adjust based on results
4. **Back up original files** before optimization
5. **Test on simple parts** before production runs

## Troubleshooting

See [TROUBLESHOOTING.md](TROUBLESHOOTING.md) for common issues and solutions.
