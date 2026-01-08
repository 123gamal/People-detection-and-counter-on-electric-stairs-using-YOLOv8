# People-detection-and-counter-on-electric-stairs-using-YOLOv8
An intelligent computer vision system that detects and counts people moving up and down escalators in real-time using YOLOv8 object detection and SORT tracking algorithm.

🎯 Features

Real-time Detection: Detects people using YOLOv8n (nano) model for fast inference
Bi-directional Counting: Separately tracks people going UP and DOWN
SORT Tracking: Uses Simple Online Realtime Tracking for accurate person tracking
ROI Masking: Focuses detection on specific regions to improve accuracy
Visual Feedback: Live visualization with bounding boxes, IDs, and count display
Unique ID Tracking: Prevents duplicate counting of the same person

🛠️ Technologies Used

YOLOv8 - State-of-the-art object detection
OpenCV - Computer vision and video processing
SORT Algorithm - Multi-object tracking
NumPy - Numerical computations
CVZone - Computer vision helper functions

📋 Requirements
txtultralytics
opencv-python
cvzone
numpy
filterpy
scikit-image
🚀 Installation

Clone the repository:

bashgit clone https://github.com/123gamal/People-detection-and-counter-on-electric-stairs-using-YOLOv8.git
cd People-detection-and-counter-on-electric-stairs-using-YOLOv8

Download YOLOv8 weights:

bash# The model will auto-download on first run, or manually download:
wget https://github.com/ultralytics/assets/releases/download/v0.0.0/yolov8n.pt

Prepare your files:


Add your video file as video.mp4
Create a mask.png to define the detection region
Add graphics.png for overlay (optional)

📂 Project Structure
├── main.py                 # Main detection script
├── sort.py                 # SORT tracking algorithm
├── video.mp4              # Input video (not included)
├── mask.png               # Region of interest mask
├── graphics.png           # UI overlay graphics
├── requirements.txt       # Python dependencies
└── README.md             # Project documentation
💻 Usage
Run the detection script:
bashpython main.py
Key Parameters to Adjust:
python# Detection confidence threshold
conf > 0.3  # Adjust between 0.1 - 0.9

# Counting line positions (adjust for your video)
limitsUp = [527, 320, 735, 320]      # Upper escalator line
limitsDown = [527, 489, 735, 489]    # Lower escalator line

# SORT tracker parameters
tracker = Sort(max_age=20, min_hits=3, iou_threshold=0.3)
🎨 How It Works

Video Input: Reads video frame by frame
ROI Masking: Applies mask to focus on escalator areas
Object Detection: YOLOv8 detects people in each frame
Tracking: SORT algorithm assigns unique IDs to each person
Line Crossing Detection: Checks if person crosses counting lines
Count Update: Increments counter when crossing is detected
Visualization: Displays bounding boxes, IDs, and counts

📊 Performance

Speed: ~30 FPS on modern CPU (depends on video resolution)
Accuracy: >90% detection accuracy with proper lighting
Model: YOLOv8n (6.3M parameters, 3.2 MB size)

🎯 Use Cases

🏢 Mall foot traffic analysis
🚇 Metro station crowd monitoring
🏬 Shopping center analytics
📊 Customer behavior analysis
🔒 Security and surveillance

🔧 Customization
Adjust Video Size:
pythonimg = cv2.resize(img, (0, 0), fx=0.5, fy=0.5)  # 50% zoom out
Change Detection Class:
pythonif currentClass == "person" and conf > 0.3:  # Modify class or confidence
Modify Counting Lines:
Use mouse callback to find coordinates by clicking on the video
🐛 Troubleshooting
Video appears zoomed in?

Add resize: img = cv2.resize(img, (0, 0), fx=0.5, fy=0.5)

Counting lines in wrong position?

Adjust limitsUp and limitsDown coordinates

Mask not found error?

Ensure mask.png exists in the project directory

Low FPS?

Use YOLOv8n (nano) for faster inference
Reduce video resolution
Use GPU if available

📸 Screenshots
Add your screenshots here showing:

Detection in action
Counting display
Bounding boxes and tracking IDs

🤝 Contributing
Contributions are welcome! Feel free to:

Report bugs
Suggest features
Submit pull requests

📝 License
This project is licensed under the MIT License - see the LICENSE file for details.
👨‍💻 Author
Your Name

GitHub: @123gamal

🙏 Acknowledgments

Ultralytics YOLOv8
SORT Algorithm
OpenCV

📧 Contact
For questions or suggestions, please open an issue or contact me directly.
