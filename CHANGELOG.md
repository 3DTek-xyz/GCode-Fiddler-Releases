# Changelog

All notable changes to GCode-Fiddler will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [0.0.1.0] - 2025-07-29

### Added
- Initial public release
- Intelligent corner detection and feed rate optimization
- Arc-aware processing with proper tangent calculations
- GUI with visual toolpath preview
- Command-line interface for automation
- Cross-platform support (Windows, macOS, Linux)
- Endpoint validation for dimensional accuracy
- Real-time comparison between original and optimized G-code

### Features
- **Corner Smoothing**: Automatically detects sharp direction changes
- **Arc Transitions**: Proper handling of linear-to-arc and arc-to-linear transitions
- **Feed Rate Intelligence**: Context-aware speed adjustments
- **Visual Feedback**: Color-coded speed zones in preview
- **Professional Validation**: Ensures toolpath accuracy is maintained

### Technical Highlights
- Enhanced arc geometry calculations
- Tangent-based direction vector analysis
- Configurable optimization parameters
- Robust error handling and validation

---

*Note: This is the first public release. Prior development versions were private.*
