This Flask application detects potholes in submitted images, saves annotated detections and their coordinates, and exposes a map view of stored reports. Its main runtime flow is image submission → YOLO inference → annotated-image response, with detected potholes also persisted for later retrieval.
*
*
*
https://potholedetectionproj.netlify.app/
*
https://huggingface.co/spaces/sharath3002/pothole-detection
*
*
*
*
*
[![Architecture diagram of sharath3002/pothole_detection](https://gitdiagram.com/sharath3002/pothole_detection/diagram.png)](https://gitdiagram.com/sharath3002/pothole_detection?utm_source=readme&utm_medium=picture)
[![Architecture diagram](https://gitdiagram.com/diagram-badge.svg)](https://gitdiagram.com/sharath3002/pothole_detection?utm_source=readme&utm_medium=badge)

Input video
<img width="977" height="471" alt="image" src="https://github.com/user-attachments/assets/2f57d3ea-e6b8-4f79-961d-7fc45771f629" />


Output video
<img width="977" height="468" alt="image" src="https://github.com/user-attachments/assets/cf1d17f8-298c-4e08-a6df-e0964b0bd817" />


Real-time detection
<img width="977" height="475" alt="image" src="https://github.com/user-attachments/assets/6ce8762e-5156-4c40-baac-6d011385745d" />


Map View
<img width="977" height="461" alt="image" src="https://github.com/user-attachments/assets/cd9ea600-c42a-4b18-b0e2-53db3fe56c32" />


Real time detection performance log
<img width="977" height="568" alt="image" src="https://github.com/user-attachments/assets/bad81283-6a2a-4e53-bc13-b82a721f1bf8" />



# Pothole Detection and Management System

## 1. Project Overview

The **Pothole Detection and Management System** is a computer vision-based application designed to identify potholes on roads and support road maintenance activities.

The system uses a YOLO-based object detection model to analyze road images and video frames, identify potholes, and display the detection results to users. It also uses geospatial information to help locate detected potholes and manage road damage information.

The main objective is to improve road safety, reduce manual road inspection efforts, and help authorities identify locations that require maintenance.

## 2. Objectives

- Automatically detect potholes using computer vision.
- Analyze uploaded road images or video frames.
- Display detected potholes with bounding boxes.
- Identify and visualize pothole locations using geographical data.
- Store and manage pothole-related information.
- Provide a centralized interface for viewing detection results and road damage information.

## 3. Technologies Used

| Technology | Purpose |
|---|---|
| Python | Core programming language and backend logic |
| YOLO | Pothole object detection |
| TensorFlow Lite / LiteRT | Lightweight model inference |
| OpenCV | Image processing and frame handling |
| Flask | Backend API and application logic |
| PostgreSQL | Storage and management of application data |
| HTML, CSS, JavaScript | Frontend user interface |
| Leaflet.js | Interactive map visualization |

## 4. System Architecture

The application consists of three main components:

### A. Frontend

The frontend provides the interface through which users interact with the application.

Its responsibilities include:

- Allowing users to submit road images or videos for analysis.
- Sending input data to the backend through API requests.
- Displaying the processed image and detection results.
- Showing pothole-related information.
- Displaying geographical locations on an interactive map using Leaflet.js.

### B. Backend

The backend handles communication between the frontend, detection model, and database.

Its responsibilities include:

- Receiving image or video input from the frontend.
- Processing incoming requests.
- Passing image data to the pothole detection module.
- Receiving detection results from the model.
- Preparing the results for the frontend.
- Managing pothole-related records in PostgreSQL.

### C. Detection Module

The detection module is responsible for identifying potholes using a trained YOLO-based model.

It uses image-processing techniques and a lightweight inference runtime to perform object detection.

Its responsibilities include:

- Loading the trained detection model.
- Preprocessing input images.
- Running model inference.
- Interpreting the model's output.
- Filtering detections based on confidence thresholds.
- Generating bounding boxes around detected potholes.

## 5. Working of the Project

The project follows the workflow below:

**Step 1: User Input**

The user provides a road image or video through the frontend interface.

**Step 2: Backend Request Processing**

The frontend sends the input to the backend using an API request. The backend receives the data and prepares it for analysis.

**Step 3: Image Preprocessing**

OpenCV is used to prepare the image for model inference. This may include resizing, color conversion, and other preprocessing operations required by the detection model.

**Step 4: Pothole Detection**

The preprocessed image is passed to the YOLO-based detection model.

The model analyzes the image and predicts whether potholes are present. For each detected object, it produces information such as:

- Class or object label.
- Confidence score.
- Bounding box coordinates.

**Step 5: Detection Result Processing**

The backend processes the model output and applies the required filtering and coordinate handling.

Detected potholes are highlighted using bounding boxes so that users can identify their positions within the image.

**Step 6: Result Display**

The processed detection results are returned to the frontend, where users can view the analyzed image and pothole information.

**Step 7: Geographical Visualization and Data Management**

Where geographical coordinates are available, pothole information can be associated with its location and displayed on an interactive Leaflet map.

PostgreSQL is used to maintain the application's structured data so that pothole information can be managed and retrieved.

## 6. Object Detection Process

The YOLO model performs object detection by analyzing the input image and predicting the location of potholes.

The general detection pipeline is:

1. Receive the input image.
2. Resize and preprocess the image.
3. Pass the image to the YOLO model.
4. Generate object detection predictions.
5. Apply confidence filtering and output processing.
6. Draw bounding boxes around detected potholes.
7. Return the final detection results.

The confidence score indicates how confident the model is about a particular detection.

## 7. Database Management

PostgreSQL is used as the relational database for storing and managing application information.

The database supports structured storage of pothole-related information and other records required by the application.

Geographical information can be used to associate detected potholes with their respective road locations.

## 8. Map Visualization

The application uses Leaflet.js to provide an interactive map interface.

The map helps users visualize geographical locations associated with pothole records.

This makes it easier to understand where road damage has been reported or detected and helps identify areas that may require inspection or maintenance.

## 9. Key Features

- **Automated Pothole Detection:** Uses a YOLO-based model to identify potholes in road images.
- **Image Processing:** Uses OpenCV for image preprocessing and detection-result visualization.
- **Detection Visualization:** Displays bounding boxes around identified potholes.
- **Lightweight Inference:** Uses TensorFlow Lite / LiteRT for model execution.
- **Interactive Map:** Uses Leaflet.js to visualize geographical information.
- **Database Integration:** Uses PostgreSQL to manage structured application data.
- **Frontend and Backend Integration:** Connects the user interface with the detection and data-management modules through APIs.

## 10. Advantages

- Reduces the need for completely manual road inspections.
- Helps identify potholes more efficiently.
- Provides visual evidence of detected road damage.
- Supports geographical visualization of pothole locations.
- Helps organize pothole information for maintenance activities.
- Provides a foundation for improving road monitoring and maintenance workflows.

## 11. Future Enhancements

- Integrate real-time pothole detection using vehicle-mounted cameras.
- Add GPS-based automatic location tagging.
- Introduce severity classification based on pothole dimensions.
- Generate reports showing pothole distribution across different areas.
- Add maintenance status tracking for reported potholes.
- Improve model accuracy using additional training data.

## 12. Conclusion

The Pothole Detection and Management System combines computer vision, machine learning, image processing, backend APIs, database management, and geographical visualization to support automated road damage identification.

By using a YOLO-based detection model, OpenCV, Flask, PostgreSQL, and Leaflet.js, the system provides a platform for detecting potholes and organizing their associated information.

The project aims to make road inspection more efficient and support better planning of road maintenance activities.
