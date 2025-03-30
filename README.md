# Camera Calibration and Augmented Reality

This repository contains implementation of camera calibration techniques and augmented reality applications using OpenCV, demonstrating the fundamental principles behind AR technology.

## Overview

This project implements various computer vision techniques to achieve augmented reality experiences. Starting with camera calibration to estimate camera parameters, the system can project 3D virtual objects onto ArUco markers and tracked objects in a video stream.

## Features

- **ArUco Marker Detection**: Utilizes DICT_5X5_1000 dictionary for robust marker detection
- **Camera Calibration**: Estimates intrinsic and extrinsic camera parameters
- **Pose Estimation**: Calculates camera position relative to detected markers
- **Virtual Object Projection**: Projects various 3D objects onto markers
- **SIFT Feature Detection**: Implements Scale-Invariant Feature Transform for robust corner detection
- **Multiple Extensions**:
  - 3D OBJ Wireframe Rendering
  - Face Detection with AR Object Overlay
  - Multi-Target Support
  - 3D Point Cloud (.pcd) Rendering from Depth Images

## Implementation Details

### ArUco Marker Detection
The system uses ArUco markers for target detection due to their asymmetric design and unique IDs, making them robust to different orientations. Detection is performed using OpenCV's `detectMarkers()` function.

### Camera Calibration
Camera calibration is performed using OpenCV's `calibrateCamera()` function to obtain the camera matrix and distortion coefficients, which are then stored in a .yml file for later use.

### Pose Estimation
The `solvePNP()` function is used to estimate the camera's position relative to detected markers, returning rotation and translation vectors that transform 3D points from the object coordinate frame to the camera coordinate frame.

### Virtual Object Projection
Using the camera parameters and pose estimation, 3D objects are projected onto the 2D image plane using `projectPoints()`. The system can render tetrahedrons, wireframes of OBJ files, and other 3D structures.

## Extensions

### OBJ Wireframe Rendering
The system can load and render wireframes of 3D models from OBJ files, accurately positioned and oriented relative to ArUco markers in the scene.

### Face Detection AR
Using Haar cascade classifiers for face detection, the system can overlay virtual objects (like a hat) on detected faces in real-time, similar to AR filters in social media applications.

### Multiple Target Support
The system supports both single-marker detection and multiple markers arranged in a grid, with proper calculation of relative positions and spacing between markers.

### 3D Point Cloud Rendering
DepthAnything network is utilized to estimate depth information, which is combined with RGB data to create 3D point clouds (.pcd files) that can be visualized and projected onto AR markers.

## Requirements

- C++11 or later
- OpenCV 4.x with contributed modules (for ArUco detection)
- Point Cloud Library (PCL) for point cloud visualization
- CMake 3.10 or later
- A webcam or video input device

## Installation & Usage

### Prerequisites

1. Install OpenCV with contrib modules:
   ```bash
   # Ubuntu/Debian
   sudo apt update
   sudo apt install libopencv-dev python3-opencv
   sudo apt install libopencv-contrib-dev
   
   # For PCL
   sudo apt install libpcl-dev pcl-tools
   ```

2. Print ArUco markers:
   - Generate and print ArUco markers using the provided utility in `src/utils/generate_markers.cpp`
   - Alternatively, use online ArUco marker generators with dictionary DICT_5X5_1000

### Building the Project

1. Clone the repository:
   ```bash
   git clone https://github.com/username/calibration-augmented-reality.git
   cd calibration-augmented-reality
   ```

2. Create a build directory:
   ```bash
   mkdir build
   cd build
   ```

3. Build using CMake:
   ```bash
   cmake ..
   make
   ```
   
## Examples

- ArUco marker detection with axes projection
- Tetrahedron projection on markers
- OBJ wireframe rendering (Pikachu, bed frame, cylinder)
- AR hat placement on detected faces
- Multi-marker grid support
- 3D point cloud visualization and projection

## Acknowledgements

- [OpenCV Calibration Tutorial](https://docs.opencv.org/4.x/dc/dbb/tutorial_py_calibration.html)
- [OpenCV Calibration Documentation](https://docs.opencv.org/3.4/d9/d0c/group__calib3d.html)
- [OpenCV Drawing Functions](https://docs.opencv.org/4.x/dc/da5/tutorial_py_drawing_functions.html)
- [OpenGL Model Loading Tutorial](https://www.opengl-tutorial.org/beginners-tutorials/tutorial-7-model-loading/)
- [OpenGL Tutorials](https://github.com/opengl-tutorials/ogl)
- [ArUco Detector Documentation](https://docs.opencv.org/4.x/d2/d1a/classcv_1_1aruco_1_1ArucoDetector.html)

## Authors

- Yuyang Tian
- Arun Mekkad

## License

MIT License
