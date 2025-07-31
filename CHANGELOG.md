# Changelog

All notable changes to GCode-Fiddler will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [0.0.2.0] - 2025-07-31

### Added
- **Helical Entry Slowdown**: New "Circular Plunge" feature renamed to more accurate "Helical Entry Slowdown"
- **Improved GUI Layout**: Side-by-side optimization panels for better organization
- **Template-based Configuration**: Hierarchical XML config system with automatic parameter migration
- **Windows DPI Support**: High-resolution icons and improved display scaling
- **Automatic Updates**: Built-in update checking and notification system (GUI only)
- **Performance Improvements**: Faster startup times, especially on Windows
- **Enhanced Build System**: Multi-platform automated builds with improved reliability

### Changed
- **"Circular Plunge" → "Helical Entry"**: More accurate terminology for spiral/helical machining operations
- **Configuration System**: Complete rewrite using hierarchical XML with Machine/OptimizationParameters/UserPreferences sections
- **GUI Improvements**: Fixed layout with Quick Options at top, side-by-side optimization controls
- **Build Process**: Updated PyInstaller specifications and GitHub Actions workflows

### Fixed
- **Windows Startup Hang**: Resolved performance bottleneck causing slow application launch
- **Icon Quality**: High-resolution icons for crisp display on all screen densities
- **Configuration Persistence**: Simplified and more reliable settings management
- **Cross-platform Compatibility**: Improved macOS and Linux support

### Technical Highlights
- Template-based config auto-updating when new parameters are added
- Parameter migration system for seamless upgrades
- Endpoint validation system for dimensional accuracy verification
- Comprehensive error handling and user feedback

## [0.0.1.0] - 2025-07-29

### Added
- Initial public release
- Corner smoothing with configurable angle detection and speed control
- Basic helical entry detection and speed optimization
- GUI with visual toolpath preview
- Command-line interface for automation
- Cross-platform support (Windows, macOS, Linux)
- Endpoint validation for dimensional accuracy
- Real-time comparison between original and optimized G-code

### Features
- **Corner Smoothing**: Automatically detects sharp direction changes
- **Helical Entry Processing**: Speed control for circular/spiral machining operations
- **Feed Rate Control**: Context-aware speed adjustments
- **Visual Feedback**: Basic toolpath preview with optimization highlighting
- **Safety Validation**: Ensures toolpath accuracy is maintained

### Technical Highlights
- Basic arc geometry calculations
- Configurable optimization parameters
- Cross-platform executable generation

---

*Note: Version 0.0.1.0 was the first public release. Prior development versions were private.*
