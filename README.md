# AI Hand Gesture Recognition

This project is a real-time, in-browser computer vision application that uses a custom-trained YOLOv8 model to detect and classify hand gestures from a webcam feed. It combines a powerful deep learning model for gesture recognition with MediaPipe for visual effects, creating a responsive and interactive experience.

![Demo Screenshot]((https://discord.com/channels/1191341773268717649/1191341773268717654/1391393133010485339))

---

## Features

* **Real-Time Detection:** Classifies hand gestures (0-5 fingers) directly in the browser using a live webcam feed.
* **Custom YOLOv8 Model:** Powered by a YOLOv8 model trained on the extensive HaGRID and "Fingers" datasets for robust, color-aware detection.
* **ESP-Style Visuals:** Uses MediaPipe to overlay a cool "ESP" hand skeleton and bounding box on the detected hand.
* **"One" Finger Trail Effect:** Displays a special glowing particle trail that follows the user's index finger when the "one" gesture is detected.
* **Adjustable Confidence:** Includes a slider to fine-tune the detection confidence threshold, helping to filter out uncertain predictions.
* **Multi-Page Structure:** Features a professional landing page that directs users to either the live vision demo or a static image classification tool.

## How It Works

This project uses a combination of powerful web technologies:

* **TensorFlow.js:** This library allows us to run our custom-trained YOLOv8 model directly in the browser, with no server-side processing required.
* **YOLOv8:** A state-of-the-art object detection model that we trained on a combined dataset to recognize hand gestures from full-color images.
* **MediaPipe Hands:** A library from Google that provides fast and accurate hand landmark detection, which we use to create the cool visual overlays.
* **HTML, CSS (Tailwind), and JavaScript:** The core web technologies used to build the user interface and control the application logic.

## How to Run This Project Locally

To get this project running on your own computer, follow these simple steps.

### 1. Download or Clone the Repository

First, get the project files onto your machine. You can either download the ZIP file or use Git to clone the repository.

```bash
git clone [your-github-repository-url]
```

### 2. Set Up the Project Folder

Navigate into the project folder. It is crucial that your files are arranged in the following structure:

```
YourProjectFolder/
|
├── index.html         # The main landing page
├── image.html         # The page for image uploads
├── vision.html        # The live webcam detection page
|
└── yolov8n_web_model/   # The folder containing your trained model
    ├── model.json
    └── ... (all the group1-shard.bin files)
```

### 3. Run a Local Web Server

You cannot simply open the `index.html` file in your browser due to security policies that block loading model files. You must serve the files from a local server. The easiest way is with Python.

1.  **Open your terminal or command prompt.**
2.  **Navigate into your project folder** using the `cd` command.
    ```bash
    cd path/to/YourProjectFolder
    ```
3.  **Start the server.**
    ```bash
    python -m http.server
    ```
    You will see a message like `Serving HTTP on 0.0.0.0 port 8000 ...`.

### 4. View the Application

Open your web browser (like Chrome or Firefox) and go to the following address:

**`http://localhost:8000`**

The website should now be running! It will ask for camera permission when you navigate to the "Real-Time Vision" page.

---

## Training Your Own Model

This repository uses a pre-trained model. If you wish to train your own, the process involves using a Google Colab notebook to:
1.  Download the **HaGRID** and **Fingers** datasets from Kaggle.
2.  Process and combine the datasets into the YOLOv8 format.
3.  Train a YOLOv8 model on the combined data.
4.  Export the final trained model to the TensorFlow.js format (`..._web_model` folder).
