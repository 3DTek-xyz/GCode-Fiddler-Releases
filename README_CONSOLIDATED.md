# GCode-Fiddler

**Advanced CNC G-code Feed Rate Optimizer**

GCode-Fiddler is a professional-grade tool for optimizing CNC machining operations by intelligently adjusting feed rates at corners, arc transitions, and critical path points. Designed for machinists, CNC operators, and manufacturing professionals who demand precision and efficiency.

## 🚀 Quick Start (No Installation Required)

[![Latest Release](https://img.shields.io/github/v/release/3DTek-xyz/GCode-Fiddler-Releases?label=Latest%20Release)](https://github.com/3DTek-xyz/GCode-Fiddler-Releases/releases/latest)
[![Downloads](https://img.shields.io/github/downloads/3DTek-xyz/GCode-Fiddler-Releases/total)](https://github.com/3DTek-xyz/GCode-Fiddler-Releases/releases)

**[➤ Download Latest Release](https://github.com/3DTek-xyz/GCode-Fiddler-Releases/releases/latest)**

### GUI Version (Recommended for most users)
1. **Download** the appropriate executable for your platform:
   - **Windows**: `GCodeFiddler-GUI-Windows.exe`
   - **macOS**: `GCodeFiddler-GUI-macOS.zip` (extract and run the .app)
   - **Linux**: `GCodeFiddler-GUI-Linux`

2. **Run** - Double-click to launch (no Python installation needed!)
3. **Load** your G-code file using File → Open
4. **Preview** the toolpath and optimization suggestions
5. **Optimize** using the toolbar button or menu
6. **Compare** original vs optimized using the comparison view
7. **Save** the optimized G-code

> **📋 macOS Users**: When opening the app for the first time, macOS may show a security warning. To run the app:
> 1. **Right-click** on `GCodeFiddler.app` and select **"Open"**
> 2. In the security dialog, click **"Open"** to confirm

### Command Line Version
1. **Download** the CLI executable:
   - **Windows**: `GCodeFiddler-CLI-Windows.exe`
   - **macOS**: `GCodeFiddler-CLI-macOS`
   - **Linux**: `GCodeFiddler-CLI-Linux`

2. **Run** from terminal:
```bash
# Basic optimization
./GCodeFiddler-CLI-[Platform] input.gcode

# With custom parameters
./GCodeFiddler-CLI-[Platform] input.gcode --corner-smoothing --corner-speed 1500

# Analysis only (no modifications)
./GCodeFiddler-CLI-[Platform] input.gcode --analyze-only
```

## ✨ Key Features

### Core Optimization
- **Corner Smoothing**: Configurable angle detection and speed reduction for sharp direction changes
- **Helical Entry Slowdown**: Intelligent speed control for circular/helical machining operations
- **Feed Rate Override**: Set specific feed rates for consistent speeds
- **Speed Limiting**: Maximum speed constraints for safety
- **Endpoint Validation**: Ensures dimensional accuracy is preserved after optimization

### Analysis & Visualization
- **Basic Visualization**: 2D toolpath preview with optimization highlighting
- **File Statistics**: Analysis of total lines, movement commands, and estimated times
- **G-code Comparison**: View original vs optimized G-code side-by-side
- **Real-time Feedback**: Progress updates during optimization processing

### User Interface
- **Simple GUI**: Easy file loading with drag & drop support (.nc, .gcode, .cnc)
- **Command Line Interface**: Full CLI support for automation workflows
- **Cross-Platform**: Available for Windows, macOS, and Linux
- **Standalone Executables**: No additional software installation required

## 🔧 System Requirements

- **Windows**: Windows 10 or later (x64, 4GB RAM, OpenGL 3.0+)
- **macOS**: macOS 10.14 or later (Intel/Apple Silicon, 4GB RAM)
- **Linux**: Ubuntu 18.04+ or equivalent (x64, 4GB RAM, X11/Wayland)

## 📋 Optimization Parameters

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

## 🛠️ Command Line Reference

### Basic Commands
```bash
# Analyze a G-code file
./GCodeFiddler-CLI input.gcode --analyze-only

# Optimize with custom output file
./GCodeFiddler-CLI input.gcode -o optimized_output.gcode

# Set feed rate and speed limits
./GCodeFiddler-CLI input.gcode --feed-rate 2000 --max-speed 3000
```

### Toolpath Analysis
```bash
# Analyze toolpaths without optimization
./GCodeFiddler-CLI input.gcode --analyze-toolpaths --analyze-only

# Export individual toolpaths to separate files
./GCodeFiddler-CLI input.gcode --export-toolpaths

# Use aggressive toolpath detection
./GCodeFiddler-CLI input.gcode --toolpath-sensitivity aggressive
```

### All Command Line Arguments
- `input_file`: Path to the input G-code file (required)
- `-o, --output`: Output file path (default: input_optimized.gcode)
- `--feed-rate`: Override feed rate in mm/min
- `--max-speed`: Maximum speed limit in mm/min
- `--analyze-only`: Only analyze the file without making modifications
- `--corner-smoothing`: Enable corner smoothing optimization
- `--corner-speed`: Feed rate for corners (mm/min, default: 2000)
- `--corner-angle`: Minimum angle threshold for corner detection (degrees, default: 45)
- `--approach-distance`: Approach distance for corners (mm, default: 20)
- `--validate-endpoints`: Validate that endpoints are preserved after optimization
- `--validation-tolerance`: Tolerance for endpoint validation (mm, default: 0.001)
- `--export-config`: Export machine configuration template to specified file
- `--check-updates`: Check for software updates and exit
- `--version`: Show version information

## 📊 Example Output

```
Loading G-code file: example.gcode

File Analysis:
  Total lines: 15847
  Movement commands: 12453
  Print time estimate: 87.34 minutes
  Average feed rate: 1800.00 mm/min

Applying optimizations...
Saving optimized G-code to: example_optimized.gcode

Optimization Results:
  New estimated time: 76.21 minutes
  Time saved: 11.13 minutes
  New average feed rate: 2100.00 mm/min
```

## ⚙️ Supported G-code Commands

- **G0/G1**: Linear movement commands - *corner smoothing and feed rate optimization*
- **G2/G3**: Circular interpolation - *helical entry slowdown for tight spirals*
- **G17/G18/G19**: Plane selection (preserved)
- **G20/G21**: Units (inches/millimeters) (preserved)
- **G28/G30**: Home position (preserved)
- **G54-G59**: Work coordinate systems (preserved)
- **G90/G91**: Absolute/incremental positioning (preserved)
- **M commands**: Machine commands (heating, cooling, etc.) (preserved)
- **Tool changes**: T commands for multi-tool setups (preserved)
- **Comments**: Preserves comments and file structure (preserved)

## 🔒 Safety & Best Practices

1. **Always preview** optimizations before saving
2. **Use endpoint validation** to ensure accuracy
3. **Start with conservative settings** and adjust based on results
4. **Back up original files** before optimization
5. **Test on simple parts** before production runs
6. **Review optimized G-code** before machining
7. **Ensure feed rates are appropriate** for your machine
8. **Keep backups** of original G-code files

## 🎯 How It Works

The optimizer processes G-code files through several stages:

1. **Parsing**: Reads and parses each line of the G-code file
2. **Analysis**: Calculates statistics like estimated time, total movements, and feed rates
3. **Optimization**: Applies selected optimization techniques:
   - Corner smoothing for sharp direction changes
   - Helical entry slowdown for circular/spiral operations
   - Feed rate overrides for consistent speeds
   - Speed limiting for safety constraints
4. **Validation**: Optional endpoint validation ensures dimensional accuracy is preserved
5. **Export**: Saves the optimized G-code with improvements applied

## 📚 Documentation

- [User Guide](docs/USER_GUIDE.md) - Detailed usage instructions
- [Command Line Reference](docs/CLI_REFERENCE.md) - Complete CLI documentation
- [Troubleshooting](docs/TROUBLESHOOTING.md) - Common issues and solutions
- [FAQ](docs/FAQ.md) - Frequently asked questions

## 🛣️ Roadmap

See our [Project Roadmap](ROADMAP.md) for upcoming features and development plans.

## 📝 Changelog

See [CHANGELOG.md](CHANGELOG.md) for detailed release notes and version history.

## 💬 Support

- **Issues**: [Report bugs or request features](https://github.com/3DTek-xyz/GCode-Fiddler-Releases/issues)
- **Discussions**: [Community support and questions](https://github.com/3DTek-xyz/GCode-Fiddler-Releases/discussions)
- **Email**: support@3dtek.xyz

## 🏢 About 3DTek

GCode-Fiddler is developed by [3DTek](https://3dtek.xyz), specialists in CNC automation and manufacturing optimization tools.

---

**Note**: This repository contains releases and documentation only. Source code is proprietary and not publicly available.

[![Built with ❤️ by 3DTek](https://img.shields.io/badge/Built%20with%20❤️%20by-3DTek-blue)](https://3dtek.xyz)
