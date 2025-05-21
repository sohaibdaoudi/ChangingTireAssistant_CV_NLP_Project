
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

```markdown
# Models Testing

## 📦 Object Detection

---

### YOLOv11 Nano Implementation Guide

**Requirements**:
- Python 3.10 or newer
- Ultralytics package (for YOLOv11 Nano)
- CUDA 11.8+ recommended for GPU acceleration

---

### Setup Options

#### With Git:
```bash
# Clone repository
git clone https://github.com/sohaibdaoudi/ChangingTireAssistant_CV_NLP_Project.git
cd changing-tire-assistant/Object\ Detection/
```

#### Without Git (ZIP Download):
1. Download repository ZIP:
   - Full repo: Click "Code" → "Download ZIP" on GitHub
   - Object Detection only: [Download Link](https://github.com/yourusername/changing-tire-assistant/archive/refs/heads/main.zip)
2. Extract ZIP file
3. Navigate to Object Detection folder

---

### Installation & Execution

1. Install requirements (use venv recommended):
```bash
python -m pip install --upgrade pip
pip install ultralytics==11.0.0 opencv-python==4.9.0.80
```

2. Run detection (basic CPU version):
```bash
python detect_yolo.py --model best.pt --source test.mp4 --resolution 1280x720
```

---

> Note: Commands with `--resolution` flag support various input sizes (1280x720 shown as example)
```

## 📦 Action Recognition




# 👨‍💻 Authors
- **SOHAIB DAOUDI** – [soh.daoudi@gmail.com](mailto:soh.daoudi@gmail.com)
- **MAROUANE MAJIDI** – [majidi.marouane0@gmail.com](mailto:majidi.marouane0@gmail.com)

---

# 📜 License
This project is licensed under the [MIT License](https://opensource.org/licenses/MIT). See the `LICENSE` file for more details.

