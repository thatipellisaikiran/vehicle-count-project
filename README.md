**Vehicle Detection and Speed Estimation using YOLOv8**
===============================================================
This project implements a real-time vehicle tracking system using the YOLOv8 model. It detects vehicles from a video stream, tracks their movement across predefined lines,
and estimates their speed based on the time taken to cross specific areas. The system uses OpenCV for video processing, YOLOv8 for object detection, 
and a custom Tracker class to track the vehicles and calculate their speed.

**Table of Contents**
==========================
1)Introduction

2)Project Setup

3)Project Files

4)How it Works

5)Usage

6)Output

7)Conclusion


**1)Introduction**
=======================
This project tracks the movement of cars from video input, calculates the speed, and logs the data. It can be used in applications like traffic monitoring, 
speed violation detection, or vehicle flow analysis.

Key Features:
---------------------------
Detects vehicles using YOLOv8.

Tracks the movement of vehicles.

Calculates the speed of vehicles in km/h.

Logs how many vehicles are moving in the "up" and "down" directions.

**2)Project Setup**
====================================
1. Prerequisites
Ensure that you have the following installed:

Python 3.7+

OpenCV

Pandas

Numpy

Ultralytics YOLOv8 library

2. Installation
Follow the steps below to set up the environment:

Clone the repository:
---------------------------
git clone https://github.com/your_username/vehicle-tracking.git
cd vehicle-tracking

Install the required Python packages:
---------------------------------------
pip install -r requirements.txt

Here's what your requirements.txt might look like:
-------------------------------------------------------
opencv-python-headless

numpy

pandas

ultralytics

Download the YOLOv8 model weights (yolov8l.pt):
---------------------------------------------------
By default, the script automatically downloads YOLOv8 weights if they are not present.
Ensure you have a video file for detection (e.g., cartraffic1.mp4) and a COCO class file (coco.txt).

**3)Project Files**
================================
main.py: Main script for vehicle detection and speed estimation.

tracker.py: A separate file containing the Tracker class to manage vehicle tracking.

requirements.txt: List of dependencies.

coco.txt: COCO dataset class names file used by YOLOv8 for object detection.

**4)How it Works**
============================
Object Detection: The YOLOv8 model detects vehicles (cars, trucks, buses) in the video stream.

Tracking: Using a custom tracker, each detected vehicle is assigned an ID, and its position is tracked frame-by-frame.

Speed Calculation: The speed of each vehicle is calculated based on the time taken to cross a fixed distance (assumed to be 10 meters in the code).

Direction Detection: Vehicles moving up and down in the frame are counted separately.

Key parameters:
----------------------------
cy1 and cy2: These lines represent different checkpoints for measuring vehicle speed.

offset: Tolerance for determining whether a vehicle crosses a line.

vh_up and vh_down: Dictionaries to store vehicle IDs and their times when they pass lines in the "up" or "down" direction.

**5)Usage**
===============================
1. Running the Project
Once you've set up the environment and downloaded the necessary files, you can run the project with the following command:
          python main.py

2. Video Input
Ensure the cartraffic1.mp4 video file is in your working directory or update the cap = cv2.VideoCapture(r'/content/cartraffic1.mp4') line in the code to point to your video file.

3. Output
The script will output a processed video (output.mp4) showing the detected vehicles, their bounding boxes, and their calculated speeds in km/h.
The number of vehicles moving in the "up" and "down" directions will be displayed on the video.

**6)Output**
==========================

The output video will display:
-----------------------------------
Bounding boxes around detected vehicles.

Real-time speed estimation (in km/h) displayed near each vehicle.

Total count of vehicles moving up and down.

You can find the output video at /content/output.mp4.

**7)Conclusion**
==================================
This project demonstrates the ability to use YOLOv8 for vehicle detection and speed estimation from video footage. It can be extended to include more advanced traffic analysis features such as real-time alerts, fine-tuned speed detection based on specific road distances, or integrated with external sensors for improved accuracy.

**Future Work**
====================================
Improve speed estimation by calibrating the distance covered by vehicles.
Add support for different types of vehicles.
Enhance tracking to deal with occlusions and overlaps.
