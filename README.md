# Camera---Classifier
The Camera Classifier is a Python application that uses a webcam feed and a LinearSVC model to classify images into two user-defined classes. It features real-time predictions, model training via a Tkinter GUI, and automatic classification of live camera frames.


---

# Camera Classifier v0.1 Alpha

Camera Classifier is an image classification application that uses a webcam to capture images, train a Support Vector Machine (SVM) model, and perform real-time classification of the webcam feed. This project is designed to demonstrate a basic workflow for image classification using OpenCV, Tkinter, and scikit-learn in Python.

## Table of Contents

- [Features](#features)
- [Project Structure](#project-structure)
- [Installation](#installation)
- [Usage](#usage)
- [File Descriptions](#file-descriptions)
- [How It Works](#how-it-works)
- [Limitations](#limitations)
- [Future Improvements](#future-improvements)
- [Contributing](#contributing)
- [License](#license)

## Features

- **Real-Time Image Capture**: Utilizes your webcam to capture images for training and prediction.
- **Binary Classification**: Supports classification between two user-defined classes.
- **Model Training**: Trains a Linear SVM classifier using images from the webcam.
- **Live Prediction**: Classifies the current webcam frame and displays the result in real time.
- **Auto-Prediction Mode**: Automatically classifies webcam frames at regular intervals.
- **Reset Functionality**: Clears training data and restarts the application to capture new classes.

## Project Structure

The project is organized into several folders and files:

```
camera_classifier/
│
├── app/
│   ├── __init__.py          # Package initialization file
│   └── app.py               # Main application code with GUI and functionality
│
├── camera/
│   ├── __init__.py          # Package initialization file
│   └── camera.py            # Camera handling code
│
├── model/
│   ├── __init__.py          # Package initialization file
│   └── model.py             # Model training and prediction code
│
├── main.py                  # Entry point for running the application
├── README.md                # Documentation file
└── requirements.txt         # List of Python dependencies
```

## Installation

To set up and run the Camera Classifier application, follow these steps:

1. **Clone the Repository:**

   ```bash
   git clone https://github.com/Anand0295/Camera-Classifier-v0.1-Alpha
   cd camera_classifier
   ```

2. **Create a Virtual Environment (Optional but Recommended):**

   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows use `venv\Scripts\activate`
   ```

3. **Install Dependencies:**

   Install the required Python packages listed in `requirements.txt`:

   ```bash
   pip install -r requirements.txt
   ```

   The main dependencies are:
   - `opencv-python`: For capturing video and image processing.
   - `Pillow`: For image manipulation.
   - `scikit-learn`: For the machine learning model.
   - `tkinter`: For creating the GUI (included in the standard Python library).

## Usage

1. **Run the Application:**

   Start the application by running the main script:

   ```bash
   python main.py
   ```

2. **Interact with the GUI:**

   - **Class Names**: Upon starting, you'll be prompted to enter names for two classes. These names will label the images you capture.
   - **Capture Images**: Use the buttons labeled with the class names to capture images from your webcam for each class.
   - **Train Model**: Click "Train Model" to train the SVM classifier using the captured images.
   - **Predict**: Click "Predict" to classify the current frame from the webcam.
   - **Auto Prediction**: Toggle "Auto Prediction" to continuously classify the webcam feed.
   - **Reset**: Click "Reset" to clear all captured images and start over with new classes.

## File Descriptions

### 1. `app/app.py`

**Description**: Contains the main application logic and GUI implementation using Tkinter.

**Key Components**:
- `__init__()`: Initializes the GUI components and sets up the application window.
- `init_gui()`: Sets up the GUI layout including buttons and display canvas.
- `auto_predict_toggle()`: Toggles automatic classification mode.
- `save_for_class(class_num)`: Captures and saves images for a specified class.
- `train_model()`: Trains the SVM model with the captured images.
- `predict()`: Predicts the class of the current webcam frame and updates the display label.
- `update()`: Continuously updates the webcam feed and handles auto-prediction.

### 2. `camera/camera.py`

**Description**: Manages webcam operations using OpenCV.

**Key Components**:
- `__init__()`: Initializes the webcam and retrieves its properties (width and height).
- `__del__()`: Releases the camera resource when the object is deleted.
- `get_frame()`: Captures a frame from the webcam and converts it to RGB format.

### 3. `model/model.py`

**Description**: Handles the image classification model using scikit-learn.

**Key Components**:
- `__init__()`: Initializes the Linear SVM model.
- `train_model(counters)`: Trains the model using images from the specified directories.
- `predict(frame)`: Predicts the class of the given frame using the trained model.

### 4. `main.py`

**Description**: The entry point for running the application. Initializes and starts the Tkinter application window.

## How It Works

1. **Image Capture**:
   - The application captures images from the webcam, converts them to grayscale, and resizes them to 150x150 pixels.
   - Images are saved in directories named `1/` and `2/`, corresponding to the two classes.

2. **Model Training**:
   - Captured images are flattened into vectors and used to train a Linear SVM classifier.
   - The model learns to distinguish between the two classes based on pixel intensity patterns.

3. **Prediction**:
   - For each new frame from the webcam, the same preprocessing steps (grayscale, resize, flatten) are applied.
   - The trained model predicts the class of the frame and displays the result in the GUI.

4. **Auto-Prediction**:
   - When enabled, the application continuously predicts the class of the current frame at regular intervals.

## Limitations

- **Binary Classification**: The current implementation supports only two classes.
- **Basic Image Processing**: The model uses basic image preprocessing techniques (grayscale and resizing), which may limit performance.
- **Fixed Image Size**: The model requires images to be of a fixed size (150x150 pixels), which may not be optimal for all scenarios.

## Future Improvements

- **Multi-Class Classification**: Expand to support more than two classes.
- **Advanced Image Preprocessing**: Implement more advanced techniques such as feature extraction.
- **Model Persistence**: Add functionality to save and load trained models.
- **Enhanced GUI**: Improve the user interface with additional features and a more polished design.
- **Deep Learning Integration**: Explore using deep learning models (e.g., Convolutional Neural Networks) for more complex image classification tasks.

## Contributing

Contributions are welcome! If you would like to contribute to this project, please follow these steps:

1. **Fork the Repository**: Create your own copy of the repository on GitHub.
2. **Create a New Branch**: Use `git checkout -b feature-branch` to create a new branch for your changes.
3. **Make Changes**: Implement your changes and test them thoroughly.
4. **Commit Changes**: Use `git commit -am 'Add new feature or fix bug'` to commit your changes.
5. **Push to GitHub**: Push your branch to your forked repository using `git push origin feature-branch`.
6. **Create a Pull Request**: Open a pull request on the main repository to propose your changes.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for more details.

---
