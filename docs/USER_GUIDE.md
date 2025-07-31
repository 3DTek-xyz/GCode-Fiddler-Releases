# GCode-Fiddler User Guide

## Overview

GCode-Fiddler optimizes CNC G-code files by intelligently adjusting feed rates for corner smoothing and helical entry operations, helping to reduce machine vibration and improve surface finish quality.

## Getting Started

### Installation

1. Download the appropriate version for your operating system from the [releases page](https://github.com/3DTek-xyz/GCode-Fiddler-Releases/releases)
2. Extract the archive to your preferred location
3. Run the executable (no installation required)

### Basic Usage

#### GUI Mode

1. **Launch** GCode-Fiddler
2. **File → Open** to load your G-code file
3. **View** the toolpath in the preview window
4. **Configure** optimization parameters in the Quick Options section
5. **Enable** Corner Smoothing and/or Helical Entry Slowdown as needed
6. **Optimize** using the optimize button
7. **Review** the results in the comparison view
8. **Save** the optimized G-code

#### Command Line Mode

```bash
# Basic optimization with corner smoothing
./GCodeFiddler-CLI input.nc --corner-smoothing

# With custom parameters
./GCodeFiddler-CLI input.nc --corner-smoothing --corner-speed 1500 --corner-angle 25

# Analysis only (no modifications)
./GCodeFiddler-CLI input.nc --analyze-only

# With endpoint validation
./GCodeFiddler-CLI input.nc --corner-smoothing --validate-endpoints
```

## Optimization Parameters

### Corner Smoothing
- **Corner Angle Threshold**: Minimum angle (degrees) to trigger slowdown (default: 45°)
- **Corner Speed**: Feed rate for approaching corners (mm/min, default: 2000)
- **Approach Distance**: Distance before corner to start slowing (mm, default: 20)

### Helical Entry Slowdown
- **Min Diameter**: Minimum diameter to trigger slowdown (mm, default: 5)
- **Max Diameter**: Maximum diameter to apply slowdown (mm, default: 30)
- **Min Speed**: Minimum speed for small diameter operations (mm/min, default: 2000)
- **Max Speed**: Maximum speed for large diameter operations (mm/min, default: 4000)

### General Options
- **Feed Rate Override**: Set specific feed rate (mm/min)
- **Max Speed Limit**: Maximum speed limit for safety (mm/min)
- **Endpoint Validation**: Verify dimensional accuracy is preserved (tolerance in mm)

## Best Practices

1. **Always preview** optimizations before saving
2. **Use endpoint validation** to ensure accuracy
3. **Start with conservative settings** and adjust based on results
4. **Back up original files** before optimization
5. **Test on simple parts** before production runs

## Understanding the Features

### Corner Smoothing
Detects sharp direction changes in linear G-code moves and applies speed reduction in the approach zone. Most effective for:
- Sharp 90° corners
- Acute angle changes
- Direction reversals

### Helical Entry Slowdown
Identifies circular/spiral machining operations (like helical ramp entries) and applies appropriate speed control based on diameter. Most effective for:
- Helical tool entries
- Small diameter boring operations
- Spiral roughing operations

## Troubleshooting

See [TROUBLESHOOTING.md](TROUBLESHOOTING.md) for common issues and solutions.
