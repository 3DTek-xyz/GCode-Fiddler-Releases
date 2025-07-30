# GCode-Fiddler

**Advanced CNC G-code Feed Rate Optimizer**

GCode-Fiddler is a professional-grade tool for optimizing CNC machining operations by intelligently adjusting feed rates at corners, arc transitions, and critical path points. Designed for machinists, CNC operators, and manufacturing professionals who demand precision and efficiency.

## 🚀 Quick Start (No Installation Required)

[![Latest Release](https://img.shields.io/github/v/release/3DTek-xyz/GCode-Fiddler-Releases?label=Latest%20Release)](https://github.com/3DTek-xyz/GCode-Fiddler-Releases/releases/latest)
[![Downloads](https://img.shields.io/github/downloads/3DTek-xyz/GCode-Fiddler-Releases/total)](https://github.com/3DTek-xyz/GCode-Fiddler-Releases/releases)

### 📥 Direct Downloads (Always Latest Version)

**GUI Version (Recommended)**
<br>
[![Windows GUI](https://img.shields.io/badge/Windows-GUI-blue?style=for-the-badge&logo=windows)](https://github.com/3DTek-xyz/GCode-Fiddler-Releases/releases/latest/download/GCodeFiddler-GUI-Windows.exe)
[![macOS GUI](https://img.shields.io/badge/macOS-GUI-black?style=for-the-badge&logo=apple)](https://github.com/3DTek-xyz/GCode-Fiddler-Releases/releases/latest/download/GCodeFiddler-GUI-macOS.zip)
[![Linux GUI](https://img.shields.io/badge/Linux-GUI-orange?style=for-the-badge&logo=linux)](https://github.com/3DTek-xyz/GCode-Fiddler-Releases/releases/latest/download/GCodeFiddler-GUI-Linux)

**Command Line Interface**
<br>
[![Windows CLI](https://img.shields.io/badge/Windows-CLI-lightblue?style=for-the-badge&logo=windows&logoColor=white)](https://github.com/3DTek-xyz/GCode-Fiddler-Releases/releases/latest/download/GCodeFiddler-CLI-Windows.exe)
[![macOS CLI](https://img.shields.io/badge/macOS-CLI-gray?style=for-the-badge&logo=apple&logoColor=white)](https://github.com/3DTek-xyz/GCode-Fiddler-Releases/releases/latest/download/GCodeFiddler-CLI-macOS)
[![Linux CLI](https://img.shields.io/badge/Linux-CLI-yellow?style=for-the-badge&logo=linux&logoColor=black)](https://github.com/3DTek-xyz/GCode-Fiddler-Releases/releases/latest/download/GCodeFiddler-CLI-Linux)

> 💡 **These links automatically download the latest version** - no need to browse releases!

### GUI Version (Recommended for most users)
1. **Download** the appropriate executable for your platform:
   - **Windows**: [`GCodeFiddler-GUI-Windows.exe`](https://github.com/3DTek-xyz/GCode-Fiddler-Releases/releases/latest/download/GCodeFiddler-GUI-Windows.exe)
   - **macOS**: [`GCodeFiddler-GUI-macOS.zip`](https://github.com/3DTek-xyz/GCode-Fiddler-Releases/releases/latest/download/GCodeFiddler-GUI-macOS.zip) (extract and run the .app)
   - **Linux**: [`GCodeFiddler-GUI-Linux`](https://github.com/3DTek-xyz/GCode-Fiddler-Releases/releases/latest/download/GCodeFiddler-GUI-Linux)

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
   - **Windows**: [`GCodeFiddler-CLI-Windows.exe`](https://github.com/3DTek-xyz/GCode-Fiddler-Releases/releases/latest/download/GCodeFiddler-CLI-Windows.exe)
   - **macOS**: [`GCodeFiddler-CLI-macOS`](https://github.com/3DTek-xyz/GCode-Fiddler-Releases/releases/latest/download/GCodeFiddler-CLI-macOS)
   - **Linux**: [`GCodeFiddler-CLI-Linux`](https://github.com/3DTek-xyz/GCode-Fiddler-Releases/releases/latest/download/GCodeFiddler-CLI-Linux)

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
- **Intelligent Corner Detection**: Automatically identifies sharp corners and arc transitions
- **Feed Rate Optimization**: Reduces vibration and tool wear through smart speed control
- **Arc-Aware Processing**: Proper handling of G2/G3 arc commands with tangent calculations
- **Corner Smoothing**: Configurable angle threshold for optimized toolpaths
- **Travel Move Optimization**: Optimize non-cutting moves for speed
- **Professional Validation**: Endpoint validation ensures dimensional accuracy

### Visualization & Analysis
- **3D Visualization**: Interactive toolpath preview with grid toggle
- **Real-time Preview**: See optimizations before processing
- **Visual Feedback**: Orange highlighting for slowdown sections
- **G-code Comparison View**: Side-by-side analysis of original vs optimized G-code
- **Toolpath Analysis**: Advanced analysis to identify and separate individual machining operations
- **Detailed Statistics**: Get comprehensive analysis of your G-code files

### User Interface
- **Drag & Drop**: Easy file loading (.nc, .gcode, .cnc)
- **Simple GUI Interface**: Easy file selection with real-time progress
- **Cross-Platform**: Available for Windows, macOS, and Linux
- **No Dependencies**: Standalone executables require no additional software

## 🔧 System Requirements

- **Windows**: Windows 10 or later (x64, 4GB RAM, OpenGL 3.0+)
- **macOS**: macOS 10.14 or later (Intel/Apple Silicon, 4GB RAM)
- **Linux**: Ubuntu 18.04+ or equivalent (x64, 4GB RAM, X11/Wayland)

## 📋 Optimization Parameters

### Corner Smoothing
- **Corner Angle Threshold**: Minimum angle (degrees) to trigger slowdown
- **Corner Speed**: Feed rate for approaching corners (mm/min)
- **Approach Distance**: Distance before corner to start slowing (mm)

### Arc Processing
- **Min Arc Radius**: Radius threshold for arc speed limiting (mm)
- **Max Arc Speed**: Maximum speed for small radius arcs (mm/min)

### Advanced Options
- **Feed Rate Override**: Set specific feed rate (mm/min)
- **Max Speed Limit**: Maximum speed limit for safety (mm/min)
- **Toolpath Sensitivity**: Detection sensitivity (conservative, default, aggressive)
- **Coordinate Precision**: Round coordinates to reduce file size

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
- `--analyze-toolpaths`: Analyze and display individual toolpaths
- `--export-toolpaths`: Export each toolpath as a separate G-code file
- `--toolpath-sensitivity`: Toolpath detection sensitivity
- `--corner-smoothing`: Enable corner smoothing (none, light, aggressive)
- `--corner-speed`: Feed rate for corners (mm/min)
- `--corner-angle`: Minimum angle threshold for corner detection (degrees)

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

- **G0/G1**: Linear movement commands (rapid/linear interpolation)
- **G2/G3**: Circular interpolation
- **G17/G18/G19**: Plane selection
- **G20/G21**: Units (inches/millimeters)
- **G28/G30**: Home position
- **G54-G59**: Work coordinate systems
- **G90/G91**: Absolute/incremental positioning
- **M commands**: Machine commands (heating, cooling, etc.)
- **Tool changes**: T commands for multi-tool setups
- **Comments**: Preserves comments and file structure

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
2. **Analysis**: Calculates statistics like print time, distances, and feed rates
3. **Optimization**: Applies various optimization techniques:
   - Optimizes feed rates for travel vs. cutting moves
   - Applies speed limits for safety
   - Rounds coordinates to reduce file size
   - Implements corner smoothing and arc processing
4. **Validation**: Ensures dimensional accuracy with endpoint validation
5. **Export**: Saves the optimized G-code with improvements

## 📚 Command Line Reference

### Basic Usage

```bash
# Analyze G-code file only (no modifications)
GCodeFiddlerCLI input.gcode --analyze-only

# Optimize G-code file with default settings
GCodeFiddlerCLI input.gcode

# Optimize with custom output file
GCodeFiddlerCLI input.gcode -o optimized_output.gcode
```

### Advanced Options

```bash
# Corner smoothing optimization
GCodeFiddlerCLI input.gcode --corner-smoothing --corner-angle 45 --corner-speed 2000

# Custom feed rate and speed limits
GCodeFiddlerCLI input.gcode --feed-rate 2500 --max-speed 4000

# Endpoint validation for accuracy verification
GCodeFiddlerCLI input.gcode --corner-smoothing --validate-endpoints --validation-tolerance 0.001

# Export machine configuration template
GCodeFiddlerCLI --export-config machine_template.xml

# Check for software updates
GCodeFiddlerCLI --check-updates
```

### Complete Parameter Reference

| Parameter | Type | Description | Default |
|-----------|------|-------------|---------|
| `input_file` | path | Input G-code file (required) | - |
| `-o, --output` | path | Output file path | `input_optimized.gcode` |
| `--feed-rate` | float | Override feed rate (mm/min) | - |
| `--max-speed` | float | Maximum speed limit (mm/min) | - |
| `--analyze-only` | flag | Only analyze, don't modify | false |
| `--config` | path | Custom machine configuration file | - |
| `--corner-smoothing` | flag | Enable corner smoothing | false |
| `--corner-speed` | float | Speed for corners (mm/min) | 2000.0 |
| `--corner-angle` | float | Corner angle threshold (degrees) | 45.0 |
| `--approach-distance` | float | Approach distance for corners (mm) | 20.0 |
| `--validate-endpoints` | flag | Validate endpoint preservation | false |
| `--validation-tolerance` | float | Tolerance for validation (mm) | 0.001 |
| `--export-config` | path | Export configuration template | - |
| `--check-updates` | flag | Check for updates and exit | false |
| `--version` | flag | Show version information | - |

### Configuration File Format

Export a template configuration file:
```bash
GCodeFiddlerCLI --export-config machine_config.xml
```

Example configuration structure:
```xml
<?xml version="1.0" encoding="UTF-8"?>
<machine_config>
    <max_rapid_speed>5000</max_rapid_speed>
    <max_cut_speed>2000</max_cut_speed>
    <max_x_travel>300</max_x_travel>
    <max_y_travel>300</max_y_travel>
    <max_z_travel>100</max_z_travel>
    <max_spindle_speed>24000</max_spindle_speed>
</machine_config>
```

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
