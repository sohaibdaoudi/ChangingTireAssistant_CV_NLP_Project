
# Changing Tire Assistant – Computer Vision & NLP Project

[![Python Version](https://img.shields.io/badge/python-3.x-blue.svg)](https://www.python.org/downloads/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](./LICENSE)


**🚧 Project Status: Under Development 🚧**

---

## 📖 Overview
This assistant leverages real-time computer vision and NLP to guide users through changing a flat tire using an egocentric (chest-mounted) camera. 

The assistant detects tools, tracks task progress, and provides interactive, step-by-step visual and voice instructions for changing a vehicle tire.

---

## 🔍 System Features
- **Real-Time Tool Detection**:
  - Identifies car jack, wheel wrench, etc.
- **Action Recognition**:
  - Tracks task progression like loosening nuts, jacking the car, replacing the wheel, etc.
- **Voice Assistant**:
  - Responds to user queries such as "What's next?"
- **Edge-Friendly Pipeline**:
  - Designed for deployment on mobile or embedded systems with minimal latency.

---

## 📂 Project Structure
```              
├── action_recognition/                 
├── Object Detection/                 
├── UML Model                 
```

---

## 🧠 Models Used
- **Object Detection**: YOLOv8 fine-tuned on tire-change-specific tools and components
- **Action Recognition**: We are trying different models SlowFast , TSM , TimeDistributed EfficientNetB0
- **Voice Assistant**: Whisper-based STT with a custom NLP pipeline for contextual understanding

---

## 📊 Data
We collected and curated a custom dataset specifically for the tire change domain:

### Data Collection Methodology
- **Primary Source**: Self-collected footage changing two tires on a Renault Megane 2, recorded with Samsung A50 smartphones from chest-mounted positions
- **Secondary Source**: Curated YouTube videos showing different tire change scenarios and vehicle types
- **Other Source**: We scraped the web to gather tool specifications and case studies related to flat tires. Additionally, we recorded standard videos and extracted frames for further processing. These frames were then manually annotated to identify tools, resulting in a dataset of approximately 1,597 annotated images.
- **Annotation Process**: Manual annotation of action segments and tool detection bounding boxes

### Dataset Structure
The data directory contains the following action classes:
```
data/
├── lower_car/             # Videos/frames of lowering the car from the jack
├── lift_car_with_jack/    # Videos/frames of raising the car with jack
├── tighten_bolts/         # Videos/frames of final bolt tightening with wrench
├── initial_wrench_tighten/# Videos/frames of initial wrench positioning
├── place_spare_tire/      # Videos/frames of positioning the spare tire
├── remove_tire/           # Videos/frames of removing the flat tire
├── hand_tighten_bolts/    # Videos/frames of hand-tightening bolts
├── loosen_bolts/          # Videos/frames of loosening wheel bolts
├── remove_bolts/          # Videos/frames of removing wheel bolts
├── labels.csv             # Action timestamps and class annotations
└── README.txt             # Dataset documentation
```

Each action class directory contains video clips used for model training and validation.

https://github.com/user-attachments/assets/6d6bef7f-5d31-4b78-b57b-93b3566c5007

# Changing Tire Assistant - Computer Vision & NLP Project: Models Testing

This document outlines the setup and usage of the models implemented within the Changing Tire Assistant project.

---

## 📦 Object Detection

This section details the implementation of the object detection model.

### YOLOv11 Nano Implementation Guide

**Description**: This model is utilized for identifying various objects relevant to the tire-changing process.

**Prerequisites**:
* Python 3.1X
* Ultralytics package (version compatible with your GPU, you can ask any AI for that)
* CUDA 11.8+ (recommended for GPU acceleration)

---

### ⚙️ Setup

You can set up the project by cloning the full repository or by cloning only the `Object Detection` directory using Git's sparse checkout feature.

#### Option 1: Using Git (Recommended - Full Repository)

1.  **Clone the Repository**:
    ```bash
    git clone https://github.com/sohaibdaoudi/ChangingTireAssistant_CV_NLP_Project.git
    ```
2.  **Navigate to the Object Detection Directory**: Open your terminal or command prompt and change to the `Object Detection` folder within the extracted contents.


#### Option 2: Manual Download (ZIP)

1.  **Download the Repository**:
    * **Full Repository**: Navigate to the [main repository page](https://github.com/sohaibdaoudi/ChangingTireAssistant_CV_NLP_Project) and click on "Code" → "Download ZIP".
    * **Object Detection**: A direct download for only the Object Detection folder is typically achieved by downloading the full repository and then extracting the relevant folder.
2.  **Extract the ZIP File**: Unzip the downloaded file to your desired location.
3.  **Navigate to the Object Detection Directory**: Open your terminal or command prompt and change to the `Object Detection` folder within the extracted contents.

---

### 🚀 Installation and Execution

### 0. Navigate to Your Project Directory

First, open your command line interface (e.g., Command Prompt, PowerShell, Terminal, Anaconda Prompt) and navigate to the project's root folder. Replace `C:\path_to_project` with the actual path to your project.
```bash
cd C:\path_to_project
```

1.  **Create a Virtual Environment (Recommended)** (Choose **one** of the following methods):
    * **Using `venv` (Python's built-in)**:
        ```bash
        python -m venv venv
        ```
        Activate the virtual environment:
        * On Windows:
            ```bash
            venv\Scripts\activate
            ```
        * On macOS/Linux:
            ```bash
            source venv/bin/activate
            ```

    * **Using `conda` (Anaconda/Miniconda)**:
        Replace `myenv` with your desired environment name and your preferred compatible version of python (3.1X).
        ```bash
        conda create --name myenv python
        ```
        Activate the Conda environment:
        ```bash
        conda activate myenv
        ```

2.  **Install Dependencies**:
    Ensure your `pip` is up to date (if using `venv` or pip within Conda) and then install the required packages.
    ```bash
    python -m pip install --upgrade pip
    pip install ultralytics==XX.XX.XX opencv-python==XX.XX.XX
    ```
    *(Note: Install `ultralytics` version that will work with GPU if you have one, if not install whatever you want)*

    *If using Conda, you might prefer to install packages using Conda where possible, for example:*
    ```bash
    # conda install anaconda # For a fuller anaconda distribution within the environment if needed
    # conda install pip # To ensure pip is available in the conda env
    # pip install ultralytics==XX.XX.XX opencv-python==XX.XX.XX
    ```

3.  **Run Detection**:
    Execute the detection script. The following command runs the detection on the test video using the GPU (or not by removing --device 0).
    ```bash
    python detect_yolo.py --model best.pt --source test.mp4 --resolution 1280x720 --device 0
    ```
    * `--model best.pt`: Specifies the path to your trained model weights.
    * `--source test.mp4`: Specifies the path to your input video or image source.
    * `--resolution 1280x720`: Sets the input resolution. This flag supports various input sizes.
    * `--device 0`: This command will let the test run on GPU, you can delete it if you want to use only CPU.

---

## 📦 Action Recognition

*(Details for the Action Recognition module, including specific models, requirements, setup, installation, and execution, should be added here following a similar structure to the Object Detection section.)*

---

## 👨‍💻 Authors

This project is developed and maintained by:

* **SOHAIB DAOUDI** – [soh.daoudi@gmail.com](mailto:soh.daoudi@gmail.com)
* **MAROUANE MAJIDI** – [majidi.marouane0@gmail.com](mailto:majidi.marouane0@gmail.com)

---

## 📜 License

This project is licensed under the [MIT License](https://opensource.org/licenses/MIT). Please see the `LICENSE` file in the repository for full license text and details.
