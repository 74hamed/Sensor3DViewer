# Sensor3DViewer

A real-time 3D orientation visualization application built with C# WinForms and SharpGL.

The project simulates sensor data (Roll, Pitch, and Yaw) and renders two rotating 3D cubes to demonstrate orientation tracking and visualization concepts commonly used in IMU, robotics, aerospace, and embedded systems applications.

## Features

* Real-time 3D rendering using SharpGL
* Roll, Pitch, and Yaw rotation visualization
* Dual cube display
* 60 FPS rendering loop
* Simulated sensor data updates
* WinForms-based desktop application
* OpenGL perspective camera

## Technologies

* C#
* .NET WinForms
* SharpGL
* OpenGL

## How It Works

The application continuously updates three orientation angles:

* Roll (X-axis rotation)
* Pitch (Y-axis rotation)
* Yaw (Z-axis rotation)

These values are applied to two 3D cubes rendered in an OpenGL scene, providing a visual representation of object orientation in space.

## Project Structure

```text
Sensor3DViewer
│
├── Form1.cs
├── Form1.Designer.cs
├── Program.cs
└── References
    └── SharpGL
```

## Installation

1. Clone the repository:

```bash
git clone https://github.com/74hamed/Sensor3DViewer.git
```

2. Open the solution in Visual Studio.

3. Restore NuGet packages.

4. Build and run the project.

## Future Improvements

* Serial port communication
* Real sensor integration (MPU6050, BNO055, etc.)
* Quaternion support
* 3D model loading
* Data logging
* Adjustable camera controls

## License

This project is intended for educational and demonstration purposes.
