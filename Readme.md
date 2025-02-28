# Face Recognition

## Introduction
This project is designed for detecting and tracking a specific person in a video. It extracts the number of times they appear and calculates the total duration of their presence.

## Requirements
### Prerequisites
- Python 3.x

### Required Libraries
Install the necessary libraries using:
```bash
pip install opencv-python torch deepface ultralytics
```

### Necessary Files
Ensure you have the following files before running the project:
- **Reference Images** (e.g., `image1.jpg`, `image2.jpg`, `image3.jpg`, `image4.jpg`)
- **Input Video** (e.g., `video.mp4`)

## Installation
### Clone the Repository
```bash
git clone https://github.com/your-repo/face-recognition.git
```

### Navigate to the Project Directory
```bash
cd face-recognition
```

### Install Dependencies
```bash
pip install -r requirements.txt
```

## Usage
1. Place the reference images and video file in the project directory.
2. Modify `reference_images` and `video_path` in `main.py` according to your data.
3. Run the script:
   ```bash
   python main.py
   ```

### Output
- Detected face images will be saved in the `detected_faces/` directory.
- A summary video will be generated as `summary_clip.mp4`.
- Console output will display timestamps and presence durations.

---

# Developer Guide

## Overview
This project implements real-time face detection and recognition using YOLO and DeepFace. It tracks a specific person’s presence in a video and generates summary statistics.

## Features
✅ **YOLO-based Face Detection** - Identifies faces in video frames.
✅ **DeepFace Verification** - Matches detected faces with reference images.
✅ **Timestamp Logging** - Records the frames where the person appears.
✅ **Summary Video Generation** - Creates a video from detected face images.

## File Structure
```
face-recognition/
│-- main.py           # Entry point
│-- yolov8n.pt        # YOLO model weights
│-- detected_faces/   # Folder for detected faces
│-- summary_clip.mp4  # Summary video
│-- README.md         # Documentation
```

## Implementation Details
### Face Detection
- Uses YOLOv8 to detect faces in video frames.
- Filters detections based on confidence threshold.

### Face Verification
- Extracted faces are converted to grayscale.
- DeepFace’s Facenet model verifies faces against reference images.
- Cosine similarity is used with a threshold of **0.4**.

### Appearance Tracking
- Logs timestamps of detections.
- Groups timestamps into continuous presence intervals.
- Calculates total presence duration.

### Summary Video Creation
- Detected face images are compiled into a video at **2x speed**.
- OpenCV is used to generate the final `summary_clip.mp4`.

## Development Setup
### Virtual Environment
```bash
python -m venv venv
source venv/bin/activate  # On macOS/Linux
venv\Scripts\activate    # On Windows
pip install -r requirements.txt
```

## Contributing
🚀 Contributions are welcome! Follow these steps to contribute:

1. **Fork** the repository.
2. **Create a feature branch**:
   ```bash
   git checkout -b feature-branch
   ```
3. **Commit your changes** and push to the branch.
4. **Open a pull request**.


