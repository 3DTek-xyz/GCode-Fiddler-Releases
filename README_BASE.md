# GCode-Fiddler

A Python tool for reading, analyzing, and optimizing G-code files to improve CNC machining performance and reduce cycle times. Available as both command-line interface and easy-to-use GUI.

## 🚀 Quick Start (No Installation Required)

### Download
Get the latest executables from the [Releases page](https://github.com/3DTek-xyz/gcode-fiddler/releases/latest):

### GUI Version (Recommended for most users)
1. **Download**: Go to the [Releases page](https://github.com/3DTek-xyz/gcode-fiddler/releases/latest) and download the GUI executable for your platform:
   - **Windows**: [GCodeFiddler-Windows.exe](https://github.com/3DTek-xyz/gcode-fiddler/releases/latest/download/GCodeFiddler-Windows.exe)
   - **macOS**: [GCodeFiddler-macOS.zip](https://github.com/3DTek-xyz/gcode-fiddler/releases/latest/download/GCodeFiddler-macOS.zip) (extract and run the .app)
   - **Linux**: [GCodeFiddler-Linux](https://github.com/3DTek-xyz/gcode-fiddler/releases/latest/download/GCodeFiddler-Linux)

> **📋 macOS Users**: When opening the app for the first time, macOS may show a security warning because the app is not signed with an Apple Developer Certificate. This is normal for open-source software. To run the app:
> 1. **Extract** the downloaded zip file
> 2. **Right-click** on `GCodeFiddler.app` and select **"Open"**
> 3. In the security dialog, click **"Open"** to confirm
> 
> The app will then open normally on subsequent launches.

2. Double-click to run - no Python installation needed!
3. Click "Browse" to select your G-code file
4. Adjust optimization settings if desired
5. Click "Process G-code" to optimize

### Command Line Version
1. **Download**: Go to the [Releases page](https://github.com/3DTek-xyz/gcode-fiddler/releases/latest) and download the CLI executable:
   - **Windows**: [GCodeFiddlerCLI-Windows.exe](https://github.com/3DTek-xyz/gcode-fiddler/releases/latest/download/GCodeFiddlerCLI-Windows.exe)
   - **macOS**: [GCodeFiddlerCLI-macOS](https://github.com/3DTek-xyz/gcode-fiddler/releases/latest/download/GCodeFiddlerCLI-macOS)
   - **Linux**: [GCodeFiddlerCLI-Linux](https://github.com/3DTek-xyz/gcode-fiddler/releases/latest/download/GCodeFiddlerCLI-Linux)
2. Run from terminal: `./GCodeFiddlerCLI-[Platform] input.gcode`

## Features

- **Simple GUI Interface**: Easy file selection with real-time progress
- **G-code Comparison View**: Side-by-side comparison of original and optimized files
- **Corner Smoothing**: Automatically reduce feed rates at sharp corners for better surface finish
- **Toolpath Analysis**: Advanced analysis to identify and separate individual machining operations
- **Toolpath Export**: Export individual toolpaths to separate G-code files for selective processing
- **G-code Analysis**: Parse and analyze G-code files to extract statistics
- **Feed Rate Optimization**: Optimize movement speeds for different types of moves
- **Travel Move Optimization**: Optimize non-cutting moves for speed
- **Coordinate Precision**: Round coordinates to reduce file size
- **Change Logging**: Preserve original lines as comments when modifications are made
- **Detailed Statistics**: Get comprehensive analysis of your G-code files
- **Cross-Platform**: Works on Windows, macOS, and Linux
- **No Dependencies**: Standalone executables require no additional software

## 📦 Distribution

The build process creates standalone executables that users can run without installing Python:

**macOS:**
* `GCodeFiddler.app` - GUI application (double-click to run)
* `GCodeFiddlerCLI` - Command-line executable

**Windows:**
* `GCodeFiddler.exe` - GUI application
* `GCodeFiddlerCLI.exe` - Command-line executable

**Linux:**
* `GCodeFiddler` - GUI application
* `GCodeFiddlerCLI` - Command-line executable

## 🔧 Development Setup

If you want to run from source or modify the code:

1. Clone or download this repository
2. Install the required dependencies:

```bash
pip install -r requirements.txt
```

## Usage

### GUI Application

Run the graphical interface:
```bash
python gui.py
```

The GUI provides:
- File browser to select G-code files
- Real-time optimization settings
- Progress tracking
- Detailed output log
- One-click processing
- **G-code Comparison View**: Side-by-side comparison of original and optimized files

#### G-code Comparison View

After processing a file, click the "Compare Original/Edited" button to open a side-by-side comparison window that shows:

- **Original G-code** (left panel) with line numbers
- **Optimized G-code** (right panel) with line numbers  
- **Synchronized scrolling** between both panels
- **Visual highlighting** of changed lines
- **Statistics** showing number of changes made
- **Line alignment** when edits create multiple lines

This makes it easy to see exactly what optimizations were applied and verify the changes before using the optimized file.

### Command Line Interface

Analyze a G-code file:
```bash
python main.py input.gcode --analyze-only
```

Optimize a G-code file:
```bash
python main.py input.gcode
```

Optimize with custom output file:
```bash
python main.py input.gcode -o optimized_output.gcode
```

### Advanced Options

Set a specific feed rate:
```bash
python main.py input.gcode --feed-rate 2000
```

Set maximum speed limit:
```bash
python main.py input.gcode --max-speed 3000
```

Combine multiple options:
```bash
python main.py input.gcode -o fast_print.gcode --feed-rate 2500 --max-speed 4000
```

### Command Line Arguments

- `input_file`: Path to the input G-code file (required)
- `-o, --output`: Output file path (default: input_optimized.gcode)
- `--feed-rate`: Override feed rate in mm/min
- `--max-speed`: Maximum speed limit in mm/min
- `--analyze-only`: Only analyze the file without making modifications
- `--analyze-toolpaths`: Analyze and display individual toolpaths in the G-code
- `--export-toolpaths`: Export each toolpath as a separate G-code file
- `--toolpath-sensitivity`: Toolpath detection sensitivity (conservative, default, aggressive)
- `--corner-smoothing`: Enable corner smoothing (none, light, aggressive)

### Toolpath Analysis Examples

Analyze toolpaths without optimization:
```bash
python main.py input.gcode --analyze-toolpaths --analyze-only
```

Export individual toolpaths to separate files:
```bash
python main.py input.gcode --export-toolpaths
```

Use aggressive toolpath detection:
```bash
python main.py input.gcode --analyze-toolpaths --toolpath-sensitivity aggressive
```

## Example Output

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

## How It Works

The optimizer processes G-code files through several stages:

1. **Parsing**: Reads and parses each line of the G-code file
2. **Analysis**: Calculates statistics like print time, distances, and feed rates
3. **Optimization**: Applies various optimization techniques:
   - Optimizes feed rates for travel vs. cutting moves
   - Applies speed limits for safety
   - Rounds coordinates to reduce file size
4. **Export**: Saves the optimized G-code with improvements

## Supported G-code Commands

- **G0/G1**: Linear movement commands (rapid/linear interpolation)
- **G28/G29**: Homing and machine setup commands
- **M commands**: Machine commands (heating, cooling, etc.)
- **Tool changes**: T commands for multi-tool setups
- **Comments**: Preserves comments and file structure

## Safety Considerations

- Always review optimized G-code before machining
- Test with non-critical prints first
- Ensure feed rates are appropriate for your printer
- Keep backups of original G-code files

## Building Standalone Executables

To create your own standalone executables:

### Automatic Build (All Platforms)
```bash
python build.py
```

### Platform-Specific Build Scripts

**macOS/Linux:**
```bash
chmod +x build.sh
./build.sh
```

**Windows:**
```batch
build.bat
```

### Manual Build with PyInstaller

**GUI Version:**
```bash
pyinstaller --onefile --windowed --name=GCodeFiddler gui.py
```

**CLI Version:**
```bash
pyinstaller --onefile --console --name=GCodeFiddlerCLI main.py
```

The executables will be created in the `dist/` folder and can be distributed without requiring Python installation.

## Requirements

- Python 3.7+ (for development)
- NumPy
- Matplotlib (for future visualization features)
- PyInstaller (for building executables)
- tkinter (included with Python)

## Contributing

Feel free to submit issues and enhancement requests!

## License

This project is open source. Use at your own risk and always verify optimized G-code before machining.

---

## Advanced Configuration and Development

### Machine Configuration Details

The application supports comprehensive machine configuration through both GUI and XML file management:

#### Configuration File Location
- **Windows**: `%USERPROFILE%\.gcode_optimizer\config.xml`
- **macOS/Linux**: `~/.gcode_optimizer/config.xml`

#### Example Configuration File
```xml
<?xml version="1.0" encoding="UTF-8"?>
<machine_config>
    <max_rapid_speed>5000</max_rapid_speed>
    <max_cut_speed>2000</max_cut_speed>
    <max_x_travel>300</max_x_travel>
    <max_y_travel>300</max_y_travel>
    <max_z_travel>100</max_z_travel>
    <max_spindle_speed>24000</max_spindle_speed>
    <use_acceleration>true</use_acceleration>
    <acceleration_time>0.5</acceleration_time>
</machine_config>
```

#### Configuration Features
- **Template System**: Import/export machine configuration templates via Tools menu
- **First-Run Setup**: Guided configuration on initial startup
- **XML Storage**: Configuration automatically saved to user directory
- **Machine-Specific Parameters**: Configure all aspects of your CNC machine capabilities

### Extended G-code Support

#### Additional Supported Commands
- **G2/G3**: Circular interpolation
- **G17/G18/G19**: Plane selection
- **G20/G21**: Units (inches/millimeters)
- **G28/G30**: Home position
- **G54-G59**: Work coordinate systems
- **G90/G91**: Absolute/incremental positioning

#### Coordinate Systems
- Support for absolute and incremental positioning
- Multiple work coordinate systems (G54-G59)
- Automatic unit detection and conversion

### Update System

The application includes an automatic update system for keeping the software current:

#### Update Features
- **Automatic Update Checking**: Check for new versions on startup (configurable)
- **Background Downloads**: Download updates in background with progress tracking
- **User-Controlled Updates**: Choose when to restart and apply updates
- **Manual Fallback**: Browser-based download option if automatic download fails

#### Update Process
1. Application checks for updates on startup (if enabled)
2. User can manually check via Help → Check for Updates
3. If update available, user chooses download method:
   - **Automatic**: Download in background with progress
   - **Manual**: Open browser to releases page
   - **Skip**: Ignore this version
4. When download complete, user prompted to restart
5. Update applied automatically on restart

### Development Setup

If you want to run from source or contribute to development:

#### Prerequisites
- Python 3.8 or higher
- Virtual environment (recommended)

#### Setup from Source
```bash
# Clone the repository
git clone https://github.com/3DTek-xyz/gcode-fiddler.git
cd gcode-fiddler

# Create virtual environment
python -m venv .venv

# Activate virtual environment
# On macOS/Linux:
source .venv/bin/activate
# On Windows:
.venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt
```

#### Project Structure
```
├── main.py              # CLI entry point
├── gui.py               # GUI application
├── gcode_processor.py   # Core G-code processing logic
├── config.py            # Machine configuration management
├── version.py           # Version checking and updates
├── build.py             # Build script for executables
├── requirements.txt     # Python dependencies
└── README.md           # This file
```

#### Building for Distribution
1. Update version in `version.py`
2. Run build scripts: `python build.py all`
3. Test executables on target platforms
4. Create GitHub release with binaries

### Troubleshooting

#### Common Issues

**Configuration not saving:**
- Check permissions for home directory
- Ensure `~/.gcode_optimizer/` directory is writable

**Update check failing:**
- Verify internet connection
- Check if repository URL is correct in `version.py`

**Executable not starting:**
- Check Python version compatibility
- Verify all dependencies are installed
- Try running from command line for error messages

**G-code parsing errors:**
- Verify G-code file format
- Check for non-standard commands
- Use analyze-only mode for debugging

### Contributing

Contributions are welcome! To contribute:

1. Fork the repository
2. Create a feature branch
3. Add your changes with tests
4. Submit a pull request

#### For Developers - Update System Configuration

To enable automatic updates in your fork:

1. Update repository URLs in `version.py`:
   ```python
   GITHUB_REPO = "your-username/gcode-fiddler"
   ```

2. Create GitHub releases with proper version tags (e.g., `v1.0.7`)

3. Attach platform-specific executables to releases:
   - `GCodeFiddler-macos.zip` (macOS)
   - `GCodeFiddler-windows.zip` (Windows) 
   - `GCodeFiddler-linux.zip` (Linux)

### Support

- Create issues for bugs or feature requests
- Check existing issues before creating new ones
- Provide G-code samples when reporting parsing issues
- Use the discussion section for questions and community support
