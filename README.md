# Real-Time Face Detection using MATLAB

A comprehensive MATLAB implementation for real-time face detection using the Viola-Jones algorithm and computer vision techniques.

## 📋 Table of Contents
- [Overview](#overview)
- [Features](#features)
- [Requirements](#requirements)
- [Installation](#installation)
- [Usage](#usage)
- [Code Structure](#code-structure)
- [Examples](#examples)
- [Troubleshooting](#troubleshooting)
- [Contributing](#contributing)
- [License](#license)
- [Acknowledgments](#acknowledgments)

## 🎯 Overview

This project demonstrates various image processing techniques and implements real-time face detection using MATLAB's Computer Vision Toolbox. The implementation covers basic image operations, facial feature detection, and real-time webcam-based face detection using the Viola-Jones algorithm.

## ✨ Features

- **Image Processing Operations**
  - Image loading and display
  - Grayscale conversion
  - Binary thresholding
  - Image cropping, resizing, flipping, and rotation

- **Face Detection Capabilities**
  - Static image face detection
  - Facial feature detection (eyes, nose, mouth)
  - Upper body detection
  - Corner feature detection in face regions

- **Real-Time Detection**
  - Webcam integration
  - Live face detection
  - Real-time annotation and display

## 🔧 Requirements

- MATLAB R2016b or later
- Image Processing Toolbox
- Computer Vision Toolbox
- Webcam (for real-time detection)

### Required MATLAB Toolboxes:
```matlab
% Check if required toolboxes are installed
ver('vision')
ver('images')
```

## 📦 Installation

1. **Clone the repository:**
   ```bash
   git clone https://github.com/yourusername/face-detection-matlab.git
   cd face-detection-matlab
   ```

2. **Open MATLAB and navigate to the project directory:**
   ```matlab
   cd('path/to/face-detection-matlab')
   ```

3. **Verify toolbox installation:**
   ```matlab
   % Run this to check if all required toolboxes are available
   disp('Checking required toolboxes...')
   if license('test', 'image_toolbox')
       disp('✓ Image Processing Toolbox is available')
   else
       error('✗ Image Processing Toolbox is required')
   end
   
   if license('test', 'video_and_image_blockset')
       disp('✓ Computer Vision Toolbox is available')
   else
       error('✗ Computer Vision Toolbox is required')
   end
   ```

## 🚀 Usage

### Basic Usage

1. **Run the main script:**
   ```matlab
   run('face_detection.m')
   ```

2. **For real-time face detection:**
   ```matlab
   realTimeFaceDetection()
   ```

3. **For enhanced real-time detection:**
   ```matlab
   enhancedRealTimeFaceDetection()
   ```

### Step-by-Step Usage

#### Image Processing
```matlab
% Load and process an image
im = imread('your_image.jpg');
imshow(im);

% Convert to grayscale
imgray = rgb2gray(im);
imshow(imgray);
```

#### Face Detection on Static Image
```matlab
% Create face detector
faceDetector = vision.CascadeObjectDetector();

% Convert image to grayscale
grayImage = rgb2gray(yourImage);

% Detect faces
bboxes = step(faceDetector, grayImage);

% Display results
detectedImg = insertObjectAnnotation(yourImage, 'Rectangle', bboxes, 'Face');
imshow(detectedImg);
```

#### Real-Time Webcam Detection
```matlab
% Initialize webcam
cam = webcam();

% Create detector
detector = vision.CascadeObjectDetector('FrontalFaceCART');

% Detection loop
while true
    frame = snapshot(cam);
    grayFrame = rgb2gray(frame);
    bboxes = step(detector, grayFrame);
    
    if ~isempty(bboxes)
        frame = insertObjectAnnotation(frame, 'rectangle', bboxes, 'Face');
    end
    
    imshow(frame);
    pause(0.03);
end
```

### Main Sections in the Code:

1. **Section 1-2**: Basic image reading and interactive selection
2. **Section 3-5**: Image processing operations (grayscale, thresholding, saving)
3. **Section 6-10**: Feature detection (face, mouth, nose, eyes, upper body)
4. **Section 11-12**: Basic webcam setup
5. **Section 13-14**: Real-time face detection implementations

## 📸 Examples

### Face Detection Results
- **Input**: RGB image
- **Output**: Annotated image with detected faces highlighted
- **Features**: Bounding boxes around detected faces, corner points marking

### Real-Time Detection
- **Live webcam feed processing**
- **Real-time face detection and annotation**
- **Performance optimization for smooth operation**

## 🔧 Troubleshooting

### Common Issues:

1. **"No webcam found" error:**
   ```matlab
   % Check available webcams
   camList = webcamlist;
   disp(camList);
   ```

2. **Toolbox not found:**
   ```matlab
   % Install required toolboxes from MATLAB Add-Ons
   % Or check your MATLAB license
   ```

3. **Poor detection performance:**
   ```matlab
   % Adjust detection parameters
   detector.MergeThreshold = 4;
   detector.MinSize = [60 60];
   detector.MaxSize = [300 300];
   ```

4. **Memory issues during real-time detection:**
   ```matlab
   % Clear variables periodically
   clear unnecessary_variables;
   
   % Reduce frame rate
   pause(0.1); % Increase pause duration
   ```

### Performance Tips:

- Ensure good lighting conditions for better detection
- Keep the webcam steady for consistent results
- Close other applications to free up system resources
- Use smaller image sizes for faster processing



### Guidelines:
- Follow MATLAB coding standards
- Add comments for complex operations
- Test your code thoroughly
- Update documentation as needed


## 🙏 Acknowledgments

- **MATLAB Image Processing Toolbox** - For providing essential image processing functions
- **MATLAB Computer Vision Toolbox** - For face detection algorithms and webcam integration
- **Viola-Jones Algorithm** - For robust face detection capabilities
- **Academic Community** - For research and development in computer vision

## 📞 Contact

**Author**: Abubakkar  
**Course**: DSP Lab  
**Institution**: KICSIT  

For questions or suggestions, please open an issue on GitHub.

---

## 📊 Technical Details

### Algorithm Used:
- **Viola-Jones Algorithm**: Efficient object detection framework
- **Cascade Classifiers**: For fast face detection
- **Haar-like Features**: For pattern recognition

### Performance Metrics:
- **Real-time processing**: ~30 FPS on standard hardware
- **Detection accuracy**: High accuracy in good lighting conditions
- **Memory usage**: Optimized for continuous operation

---

*Last updated: January 2024*
