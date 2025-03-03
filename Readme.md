# Face Recognition

## Introduction
This project is designed for detecting and tracking a specific person across multiple videos. It extracts the number of times they appear and calculates the total duration of their presence in each video.

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
- **Input Videos** (e.g., `video1.mp4`, `video2.mp4`, `video3.mp4`)

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
1. Place the reference images and video files in the project directory.
2. Modify `reference_images` and `video_paths` in `main.py` according to your data.
3. Run the script:
   ```bash
   python main.py
   ```

### Output
- Detected face images will be saved in the `detected_faces/` directory.
- A summary video will be generated as `summary_clip.mp4`.
- Console output will display timestamps and presence durations for each video.

---

# Developer Guide

## Overview
This project implements real-time face detection and recognition using YOLO and DeepFace. It tracks a specific person’s presence across multiple videos and generates summary statistics.

## Features
✅ **YOLO-based Face Detection** - Identifies faces in video frames.  
✅ **DeepFace Verification** - Matches detected faces with reference images.  
✅ **Timestamp Logging** - Records the frames where the person appears in each video.  
✅ **Summary Video Generation** - Creates a video from detected face images across all videos.  

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
- Filters detections based on a confidence threshold.

### Face Verification
- Extracted faces are converted to grayscale.
- DeepFace’s Facenet model verifies faces against reference images.
- Cosine similarity is used with a threshold of **0.4**.

### Appearance Tracking
- Logs timestamps of detections for each video.
- Groups timestamps into continuous presence intervals.
- Calculates total presence duration for each video.

### Summary Video Creation
- Detected face images from all videos are compiled into a single video at **2x speed**.
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

---

# Changes in the Updated Version
- **Multiple Video Support**: The program now processes a list of videos instead of a single video.  
- **Unique Naming for Detected Faces**: Detected face images are named with the video filename to avoid conflicts.  
- **Consolidated Summary Video**: A single summary video is created from all detected faces across multiple videos.  
- **Improved Logging**: Timestamps and presence durations are logged separately for each video.  

---

# Example Output
### Console Output
```
Processing video: video1.mp4
✅ Match found in video1.mp4 at 12.34 seconds (frame 456), face 0!
✅ Virat appeared 5 times in video1.mp4.
📌 Time Stamps: [12.34, 14.56, 16.78, 18.90, 20.12]
⏳ Total presence duration: 8.22 seconds
📍 Appearance Intervals:
🕒 12.34s to 14.56s (Duration: 2.22s)
🕒 16.78s to 20.12s (Duration: 3.34s)

Processing video: video2.mp4
✅ Match found in video2.mp4 at 5.67 seconds (frame 123), face 1!
✅ Virat appeared 3 times in video2.mp4.
📌 Time Stamps: [5.67, 7.89, 9.01]
⏳ Total presence duration: 3.34 seconds
📍 Appearance Intervals:
🕒 5.67s to 7.89s (Duration: 2.22s)
🕒 9.01s to 9.01s (Duration: 0.00s)

🎥 Summary video saved as summary_clip.mp4
```

### Output Files
- `detected_faces/face_video1_456_0.jpg`  
- `detected_faces/face_video2_123_1.jpg`  
- `summary_clip.mp4`  

---

