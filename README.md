# Sensor3DViewer

A real-time 3D visualization application for sensor orientation data, built with C# WinForms and SharpGL. This application demonstrates how to visualize IMU (Inertial Measurement Unit) sensor data through interactive 3D rendering.

## 📋 Overview

Sensor3DViewer simulates and visualizes 3D object orientation using Roll, Pitch, and Yaw (RPY) angles, commonly produced by accelerometers, gyroscopes, and magnetometers. The application renders multiple 3D cubes that rotate in real-time to reflect simulated sensor orientation, making it ideal for learning sensor data visualization concepts.

## 🎯 Features

- ✅ **Real-time 3D Rendering** - 60 FPS animation using SharpGL
- ✅ **RPY Visualization** - Interactive display of Roll, Pitch, and Yaw rotations
- ✅ **Dual Cube Display** - Two synchronized rotating cubes for comparison
- ✅ **Simulated Sensor Data** - Built-in data generator for testing
- ✅ **OpenGL Rendering** - Hardware-accelerated graphics
- ✅ **Perspective Camera** - Realistic 3D viewing experience
- ✅ **Windows Forms GUI** - Native desktop application interface

## 🔧 Technology Stack

| Component | Technology |
|-----------|-----------|
| **Language** | C# (.NET Framework) |
| **GUI Framework** | Windows Forms |
| **Graphics Engine** | SharpGL (OpenGL Wrapper) |
| **Rendering API** | OpenGL 2.1+ |
| **Development IDE** | Visual Studio 2019+ |
| **Target Framework** | .NET Framework 4.7.2+ |

## 🎮 How It Works

### Sensor Orientation System

The application uses the standard **Roll-Pitch-Yaw (RPY)** convention for representing 3D orientation:

```
Roll (X-axis):   Rotation around the X-axis (forward/backward tilt)
Pitch (Y-axis):  Rotation around the Y-axis (left/right tilt)
Yaw (Z-axis):    Rotation around the Z-axis (rotation/heading)
```

### Rendering Pipeline

1. **Sensor Data Generation** - Simulated RPY values update continuously
2. **Transformation Calculation** - RPY angles converted to rotation matrices
3. **Cube Rendering** - Two cubes rendered with calculated transformations
4. **Display Update** - Viewport refreshed at 60 FPS

## 📦 Project Structure

```
Sensor3DViewer/
├── Sensor3DViewer/
│   ├── Form1.cs                 # Main application window and logic
│   ├── Form1.Designer.cs        # WinForms designer generated code
│   ├── Program.cs               # Application entry point
│   ├── Sensor3DViewer.csproj    # Project file
│   └── Properties/
│       └── AssemblyInfo.cs      # Assembly metadata
├── README.md
├── .gitignore
└── packages.config              # NuGet dependencies
```

## 📊 Application Architecture

```
┌─────────────────────────────────────┐
│  Form1 (Main Window)                │
├─────────────────────────────────────┤
│ ┌─────────────────────────────────┐ │
│ │  OpenGL Control (SharpGL)       │ │
│ │  ├─ Viewport Setup              │ │
│ │  ├─ Camera Configuration        │ │
│ │  └─ Rendering Pipeline          │ │
│ └─────────────────────────────────┘ │
├─────────────────────────────────────┤
│ ┌─────────────────────────────────┐ │
│ │  Sensor Data Simulator          �� │
│ │  ├─ Roll Generation             │ │
│ │  ├─ Pitch Generation            │ │
│ │  └─ Yaw Generation              │ │
│ └─────────────────────────────────┘ │
└─────────────────────────────────────┘
```

## 🚀 Getting Started

### Prerequisites

- **Visual Studio** 2019 or later
- **.NET Framework** 4.7.2 or higher
- **NuGet Package Manager**
- Graphics card with OpenGL support

### Installation & Setup

1. **Clone the Repository**
   ```bash
   git clone https://github.com/74hamed/Sensor3DViewer.git
   cd Sensor3DViewer
   ```

2. **Open in Visual Studio**
   - Launch Visual Studio
   - Open the solution file (`Sensor3DViewer.sln`)

3. **Restore NuGet Packages**
   - Right-click on the solution → "Restore NuGet Packages"
   - Alternatively, use Package Manager Console:
     ```powershell
     Update-Package -Reinstall
     ```

4. **Build the Solution**
   - Press `Ctrl+Shift+B` or use `Build → Build Solution`
   - Ensure no build errors occur

5. **Run the Application**
   - Press `F5` to start debugging
   - The visualization window will open showing rotating cubes

## 📈 Sensor Data Format

The application works with RPY (Roll-Pitch-Yaw) orientation data:

```csharp
// Example sensor data structure
float Roll;   // X-axis rotation (-180 to +180 degrees)
float Pitch;  // Y-axis rotation (-90 to +90 degrees)
float Yaw;    // Z-axis rotation (-180 to +180 degrees)
```

## 🎮 User Interface

The main window displays:

- **Left Cube** - First sensor orientation visualization
- **Right Cube** - Second sensor orientation visualization (or alternative view)
- **Render Area** - OpenGL viewport showing real-time graphics
- **Status Bar** - FPS counter and system information (optional)

### Potential Controls (Extensible)

| Control | Function |
|---------|----------|
| Mouse Movement | Potential camera control (not implemented yet) |
| Window Resize | Viewport automatically adjusts |
| Application Focus | Rendering pauses when window loses focus |

## 🔄 Rendering Loop

The application runs a continuous rendering loop:

```
Loop (60 FPS):
  1. Update sensor data (simulated or received)
  2. Calculate rotation matrices from RPY
  3. Clear OpenGL framebuffer
  4. Render Cube 1 with transformation
  5. Render Cube 2 with transformation
  6. Swap display buffers
  7. Update UI (FPS counter, etc.)
```

## 🛠️ Dependencies

### Required NuGet Packages

- **SharpGL** - .NET OpenGL bindings and wrapper library
  ```powershell
  Install-Package SharpGL
  ```

### Optional Packages
- Additional utility libraries for math operations (if implementing quaternions)

## 📝 Code Example

Typical sensor data handling pattern:

```csharp
// Update sensor data (example)
float roll = 45.0f;    // Degrees
float pitch = 30.0f;   // Degrees
float yaw = 90.0f;     // Degrees

// Apply to cube transformation
// Matrix = RotZ(Yaw) * RotY(Pitch) * RotX(Roll)
```

## 🚧 Future Enhancements

These improvements are planned for future versions:

- [ ] **Serial Port Communication** - Read sensor data from hardware (Arduino, Raspberry Pi)
- [ ] **Real Sensor Integration** 
  - [ ] MPU6050 (6-axis IMU)
  - [ ] BNO055 (9-axis absolute orientation sensor)
  - [ ] LSM9DS1 (9-axis IMU)
- [ ] **Quaternion Support** - More efficient orientation representation
- [ ] **3D Model Loading** - Import custom `.obj` or `.fbx` models
- [ ] **Data Logging** - Record and playback sensor data
- [ ] **Calibration Tools** - Zero-offset and scale calibration
- [ ] **Advanced Camera Controls** 
  - [ ] Zoom and pan
  - [ ] Multiple view modes
  - [ ] Camera animation
- [ ] **Real-time Data Graphing** - Plot RPY values over time
- [ ] **Performance Optimization** - Batch rendering, shader improvements

## 🎓 Learning Resources

### Understanding Sensor Orientation

- **Euler Angles (RPY)** - Standard representation used in this project
  - Intuitive to understand
  - Visual representation is straightforward
  - Can suffer from gimbal lock in edge cases

- **Quaternions** - Advanced orientation representation
  - More mathematically robust
  - No gimbal lock
  - Requires deeper understanding of quaternion algebra

### Recommended Learning Path

1. Understand RPY angle conventions
2. Learn rotation matrix mathematics
3. Explore OpenGL transformation matrices
4. Study 3D graphics pipeline
5. Implement sensor data reading (future)
6. Extend with quaternion support (advanced)

## 🧪 Testing & Validation

To verify the application works correctly:

1. **Visual Verification**
   - Cubes should rotate smoothly at 60 FPS
   - Rotation should match simulated sensor data
   - No visual glitches or stuttering

2. **Performance Monitoring**
   - Monitor FPS (should be stable at 60)
   - Check CPU usage (should be moderate)
   - Monitor GPU usage (should be low for cubes)

## 🤝 Contributing

Contributions are welcome! To contribute:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/enhancement`)
3. Make your improvements
4. Test thoroughly
5. Commit with clear messages
6. Push to your fork
7. Create a Pull Request

### Contribution Ideas

- Implement serial port sensor reading
- Add data logging functionality
- Create quaternion visualization mode
- Add configuration UI for sensor parameters
- Implement network-based sensor data

## 📄 License

This project is intended for **educational and demonstration purposes**. Feel free to use, modify, and adapt for your learning or projects.

## 👤 Author

**Hamed** - [GitHub Profile](https://github.com/74hamed)

## 🔗 Useful Resources

### Documentation & Tutorials
- [SharpGL GitHub Repository](https://github.com/dwmkerr/sharpgl)
- [Learn OpenGL - Transformations](https://learnopengl.com/Getting-started/Transformations)
- [Euler Angles Explanation](https://en.wikipedia.org/wiki/Euler_angles)
- [C# WinForms Documentation](https://docs.microsoft.com/en-us/dotnet/desktop/winforms/)

### Hardware Resources
- [Arduino IMU Projects](https://www.arduino.cc/)
- [MPU6050 Documentation](https://invensense.tdk.com/)
- [Raspberry Pi Projects](https://www.raspberrypi.org/)

### Mathematics
- [3D Graphics Mathematics](https://www.3dmath.info/)
- [Rotation Matrices](https://en.wikipedia.org/wiki/Rotation_matrix)
- [Quaternions in 3D Graphics](https://www.3dmath.info/quaternions.html)

## 📞 Support & Troubleshooting

### Common Issues

**Q: Application crashes on startup**
- A: Ensure graphics drivers are up to date
- A: Verify OpenGL support on your graphics card

**Q: Low FPS or stuttering**
- A: Check background processes consuming CPU/GPU
- A: Reduce window size
- A: Update graphics drivers

**Q: Cubes not rotating**
- A: Check sensor data simulator is working
- A: Verify rotation calculation is correct
- A: Check OpenGL error logs

### Getting Help

- Check GitHub Issues for similar problems
- Review code comments for implementation details
- Consult OpenGL and C# documentation
- Test with simulated data first before hardware integration

---

**Last Updated**: June 2024  
**Status**: Deprecated  
**Version**: 1.0 (Educational Release)

**Repository**: https://github.com/74hamed/Sensor3DViewer
