# Future Features & Enhancements

## Overview
This document outlines planned enhancements and future development priorities for GCode-Fiddler. Features are organized by category and development priority to provide a roadmap for continued improvement.

## Development Status Legend
- ✅ **Implemented**: Feature is complete and available
- 🔄 **In Progress**: Currently being developed
- ⏳ **Planned**: Scheduled for future development
- 💡 **Proposed**: Under consideration, feedback welcome

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

### Advanced Corner Smoothing 🔄
**Priority: High** | **Target: v1.0.9**

Current corner smoothing is basic. Planned enhancements:

- **Adaptive Speed Control**: Automatically adjust speeds based on corner geometry
- **Look-ahead Optimization**: Consider multiple corners for smoother transitions
- **Tool-specific Parameters**: Different smoothing based on tool type and material
- **Jerk Limitation**: Respect machine jerk limits for smoother motion

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

### Advanced GUI Features ⏳
**Priority: Medium** | **Target: v1.1.0**

- **3D Toolpath Visualization**: Interactive 3D preview of toolpaths
- **Before/After Comparison**: Visual comparison of original vs. optimized
- **Real-time Preview**: Live preview of optimization effects
- **Material Removal Simulation**: Visual simulation of machining process

### Batch Processing ⏳
**Priority: Medium** | **Target: v1.0.10**

- **Folder Processing**: Process entire directories of G-code files
- **Automated Workflows**: Save and reuse optimization settings
- **Progress Tracking**: Monitor batch processing progress
- **Report Generation**: Summary reports of optimization results

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

### Machining Time Prediction ⏳
**Priority: High** | **Target: v1.0.9**

- **Accurate Time Estimation**: Consider acceleration, deceleration, and actual machine dynamics
- **Multi-axis Consideration**: Account for rotary axis movement in time calculations
- **Tool Change Time**: Include tool change operations in time estimates
- **Machine-specific Timing**: Use actual machine specifications for predictions

---

## Build & Platform Support

### Extended macOS Compatibility ⏳
**Priority: Medium** | **Target: v1.0.9**

Expand macOS platform support to reach more users with older Mac hardware and operating systems.

**Current Status:**
- ✅ **ARM64 (Apple Silicon)**: macOS 14+ on M1/M2/M3 Macs
- ⏳ **Intel x64**: Support for Intel-based Macs (2020 and earlier)
- ⏳ **Older macOS**: Support for macOS 11+ (Big Sur and later)

**Implementation Plans:**
- **Multi-architecture Builds**: Create separate builds for ARM64 and Intel x64
- **Backward Compatibility**: Test and ensure compatibility with macOS 11-13
- **Universal Binaries**: Explore creating universal binaries that support both architectures
- **Legacy Support**: Evaluate minimum macOS version requirements vs. development complexity

**Benefits:**
- Reach users with Intel-based Macs (significant portion of Mac user base)
- Support organizations with older Mac hardware
- Provide upgrade path for users hesitant to upgrade macOS

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

### Short Term (Next 3 months)
- 🔄 Enhanced corner smoothing
- ⏳ Improved time estimation
- ⏳ Basic 3D validation
- ⏳ Vacuum bed optimization foundation

### Medium Term (3-12 months)
- ⏳ Advanced GUI features
- ⏳ Batch processing
- ⏳ Full vacuum bed optimization
- ⏳ Extended macOS compatibility

### Long Term (12+ months)
- ⏳ Advanced toolpath strategies
- ⏳ Multi-platform build matrix
- ⏳ Enhanced error detection

*Timeline subject to change based on user feedback and development priorities.*
