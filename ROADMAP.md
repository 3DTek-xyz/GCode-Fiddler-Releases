# Future Features & Enhancements

## Overview
This document outlines planned enhancements and future development priorities for GCode-Fiddler. Features are organized by category and development priority to provide a roadmap for continued improvement.

## Development Status Legend
- ✅ **Implemented**: Feature is complete and available in current release
- 🔄 **In Progress**: Currently being developed or tested
- ⏳ **Planned**: Scheduled for future development
- 💡 **Proposed**: Under consideration, feedback welcome

---

## Current Status (v0.0.2.0)

### ✅ Implemented Features
- **Basic Corner Smoothing**: Configurable angle detection with approach distance control
- **Helical Entry Slowdown**: Speed control for circular/spiral machining operations (5-30mm diameter range)
- **Feed Rate Override**: Manual feed rate control for consistent speeds
- **Speed Limiting**: Maximum speed constraints for safety
- **Endpoint Validation**: Dimensional accuracy verification system
- **Configuration System**: Template-based XML configuration with parameter migration
- **Cross-platform Support**: Windows, macOS, and Linux executables
- **Command Line Interface**: Full CLI automation support
- **Update System**: Automatic update checking and notification (GUI)

---

## Validation & Safety Features

### 3D Shape Validation System ⏳
**Priority: High** | **Target: v1.1.0**

Provide rock-solid validation that G-code optimizations preserve the exact physical output of CNC machining operations.

**Current Status:**
- ✅ **Endpoint Validation**: Ensures all G-code commands end at the same XYZ coordinates
- ⏳ **3D Shape Validation**: Complete 3D toolpath validation (planned)

**Key Benefits:**
- Prevents expensive machine crashes
- Mathematical proof that optimizations preserve physical output
- Confidence in automated optimization

**Implementation Phases:**
1. **Phase 1**: Basic 3D toolpath hashing and coordinate system validation
2. **Phase 2**: Advanced arc geometry and tool engagement validation
3. **Phase 3**: Physics-based simulation and material removal validation

### Enhanced Error Detection ⏳
**Priority: Medium** | **Target: v1.2.0**

- **G-code Syntax Validation**: Detect malformed commands before processing
- **Machine Limits Checking**: Validate moves against machine capabilities
- **Tool Collision Detection**: Basic collision detection for rapid moves
- **Feedrate Validation**: Ensure feed rates are within safe machine limits

---

## Optimization Algorithms

### Enhanced Corner Smoothing ⏳
**Priority: High** | **Target: v0.0.3.0**

Current corner smoothing is functional but basic. Planned enhancements:

- **Adaptive Speed Control**: Automatically adjust speeds based on corner geometry
- **Look-ahead Optimization**: Consider multiple corners for smoother transitions
- **Arc Transition Handling**: Better integration between linear and arc movements
- **Configurable Sensitivity**: User-adjustable detection sensitivity levels

### Intelligent Feed Rate Optimization ⏳
**Priority: High** | **Target: v1.1.0**

- **Material-aware Optimization**: Adjust feeds based on material properties
- **Tool Wear Consideration**: Modify feeds to extend tool life
- **Chip Load Optimization**: Maintain optimal chip load across varying geometries
- **Surface Finish Priority**: Balance speed vs. surface quality

### Advanced Toolpath Strategies ⏳
**Priority: Medium** | **Target: v1.2.0**

- **Trochoidal Milling**: Convert conventional paths to trochoidal for better chip evacuation
- **Climb vs. Conventional**: Automatic selection based on material and tool
- **Tool Engagement Optimization**: Minimize sudden tool engagement changes
- **Rest Machining Detection**: Identify and optimize rest machining operations

### Vacuum Bed Optimisation ⏳
**Priority: High** | **Target: v1.1.0**

Intelligent optimization for CNC machines with vacuum bed workholding systems to maximize cutting efficiency and minimize part movement.

**Key Features:**
- **Part Layout Analysis**: Analyze G-code to understand part positioning and nesting on the vacuum bed
- **Vacuum Zone Mapping**: Identify which vacuum zones will be active for optimal holding force
- **Cut Sequence Optimization**: Reorder cutting operations to maintain maximum holding force throughout the job
- **Critical Cut Identification**: Identify cuts that could compromise part stability (full-depth cuts, perimeter cuts)
- **Finishing Strategy**: Optimize when to perform finish cuts vs. rough cuts to prevent part movement
- **Multi-part Coordination**: For nested parts, optimize cutting order to prevent adjacent parts from moving

**Implementation Phases:**
1. **Phase 1**: Basic part boundary detection and cut sequence analysis
2. **Phase 2**: Vacuum zone simulation and holding force calculation
3. **Phase 3**: Advanced multi-part optimization and machine-specific vacuum patterns

**Benefits:**
- Reduce part movement and improve dimensional accuracy
- Minimize scrap due to parts shifting during cutting
- Optimize cycle time by cutting parts in the most efficient order
- Reduce manual intervention and operator monitoring

**Use Cases:**
- **Sheet Metal Cutting**: Optimize plasma/laser cutting on vacuum tables
- **Wood/Composite Machining**: CNC router operations with vacuum workholding
- **Sign Making**: Multi-part jobs on vacuum bed routers
- **Production Nesting**: Large sheets with multiple parts requiring careful cut sequencing

---

## User Interface & Experience

### Improved 3D Visualization ⏳
**Priority: Medium** | **Target: v0.0.4.0**

Current visualization is basic 2D preview. Planned enhancements:

- **3D Toolpath Visualization**: Interactive 3D preview of toolpaths
- **Color-coded Speed Zones**: Visual indication of optimization effects
- **Before/After Comparison**: Visual comparison of original vs. optimized toolpaths
- **Grid and Reference Lines**: Better spatial orientation tools

### Toolpath Analysis System ⏳
**Priority: Medium** | **Target: v0.0.5.0**

Planned analysis features for better G-code understanding:

- **Toolpath Separation**: Identify and separate individual machining operations
- **Operation Classification**: Distinguish between roughing, finishing, and drilling operations
- **Cut vs Travel Detection**: Better identification of cutting vs rapid moves
- **Export Individual Toolpaths**: Save separate operations as individual G-code files

### File Watcher & Auto-Processing ⏳
**Priority: Medium** | **Target: v1.0.11**

Automatically detect and process new G-code files as they appear in watched directories.

**Key Features:**
- **Directory Monitoring**: Watch specified folders for new .nc/.gcode files
- **Auto-Processing**: Automatically apply saved optimization profiles to new files
- **Output Management**: Configurable output locations (same folder, dedicated output folder, etc.)
- **Processing Queue**: Handle multiple files arriving simultaneously
- **Notification System**: Desktop notifications when processing completes
- **Error Handling**: Robust handling of file access issues and processing failures
- **Hot Folder Support**: Production-ready hot folder functionality for manufacturing workflows

**Use Cases:**
- **CAM Integration**: Automatically optimize files as they're exported from CAM software
- **Production Workflows**: Seamless integration into manufacturing pipelines
- **Network Folder Monitoring**: Watch shared network drives for new jobs
- **Batch Optimization**: Overnight processing of large job queues

---

## Advanced Analysis

### Improved Time Estimation ⏳
**Priority: High** | **Target: v0.0.3.0**

Current time estimation is basic. Planned improvements:

- **Acceleration/Deceleration Modeling**: Consider machine dynamics for realistic times
- **Feed Rate Transition Analysis**: Account for speed changes and ramp times
- **Machine-specific Timing**: Use actual machine specifications for predictions
- **Tool Change Time**: Include tool change operations in time estimates
- **Multi-axis Consideration**: Account for rotary axis movement in time calculations
- **Tool Change Time**: Include tool change operations in time estimates
- **Machine-specific Timing**: Use actual machine specifications for predictions

---

## Build & Platform Support

### Extended macOS Compatibility ⏳
**Priority: Low** | **Target: v0.0.4.0**

Current macOS support is Apple Silicon focused. Planned expansion:

**Current Status:**
- ✅ **ARM64 (Apple Silicon)**: macOS 14+ on M1/M2/M3 Macs
- ⏳ **Intel x64**: Support for Intel-based Macs (2020 and earlier)
- ⏳ **Older macOS**: Support for macOS 11+ (Big Sur and later)

**Implementation Plans:**
- **Multi-architecture Builds**: Create separate builds for ARM64 and Intel x64
- **Backward Compatibility**: Test and ensure compatibility with macOS 11-13
- **Legacy Support**: Evaluate minimum macOS version requirements

### Multi-Platform Build Matrix ⏳
**Priority: Low** | **Target: v1.1.0**

- **Windows x86/x64**: Ensure broad Windows compatibility
- **Linux Distributions**: Support for Ubuntu, CentOS, and other popular distributions
- **Container Support**: Docker images for cross-platform deployment
- **ARM Linux**: Support for Raspberry Pi and other ARM-based Linux systems

---

## Contributing

We welcome feedback and suggestions for future features! Please consider:

1. **Use Cases**: Describe your specific machining workflows and challenges
2. **Priority**: Help us understand which features would provide the most value
3. **Implementation Ideas**: Technical suggestions and approaches
4. **Testing**: Volunteer to test new features in your environment

**Contact**: Open issues on GitHub or reach out through our community channels.

---

## Development Timeline

### Short Term (Next 2-3 months) - v0.0.3.0
- ⏳ Enhanced corner smoothing algorithms
- ⏳ Improved time estimation with machine dynamics
- ⏳ Better error handling and user feedback

### Medium Term (3-6 months) - v0.0.4.0 & v0.0.5.0  
- ⏳ 3D visualization improvements
- ⏳ Extended macOS compatibility (Intel support)
- ⏳ Toolpath analysis and separation features

### Long Term (6+ months) - v0.1.0+
- ⏳ Advanced optimization algorithms
- ⏳ Batch processing capabilities
- ⏳ Professional features for production environments

*Timeline subject to change based on user feedback and development priorities.*
