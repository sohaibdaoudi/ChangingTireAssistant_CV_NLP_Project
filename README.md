
# Changing Tire Assistant – Computer Vision & NLP Project

[![Python Version](https://img.shields.io/badge/python-3.x-blue.svg)](https://www.python.org/downloads/)
[![Streamlit Version](https://img.shields.io/badge/streamlit-1.20%2B-ff69b4.svg)](https://streamlit.io/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

**🚧 Project Status: Under Development 🚧**

---

## 📖 Overview

This assistant leverages real-time computer vision and NLP to guide users through changing a flat tire using an egocentric (chest-mounted) camera. Inspired by energy optimization projects like V2G, this project focuses on practical, real-world assistance using a lightweight CV-NLP pipeline.

The assistant detects tools, tracks task progress, and provides interactive, step-by-step visual and voice instructions.

---

## 🔍 System Features

- **Real-Time Tool Detection**:
  - Identifies car jack, wheel wrench, and flat/new tires.
- **Action Recognition**:
  - Tracks task progression like loosening nuts, jacking the car, replacing the wheel, etc.
- **Voice Assistant**:
  - Responds to user queries such as "What’s next?" or "Am I doing it right?"
- **Edge-Friendly Pipeline**:
  - Designed for deployment on mobile or embedded systems.

---

## 📂 Project Structure

```
├── app/                    # Streamlit-based user interface
├── models/                 # Trained YOLO/Action Recognition models
├── notebooks/              # Data processing and model training notebooks
├── data/                   # Sample egocentric video frames, annotations
├── utils/                  # Utility scripts for preprocessing, inference
├── requirements.txt        # Python dependencies
└── README.md               # This file
```

---

## 🧠 Models Used

- **Object Detection**:
  - YOLOv5-based custom model trained on annotated tire change scenes.
- **Action Recognition**:
  - RNN or Temporal CNN to recognize the current step being performed.
- **Voice Assistant**:
  - Lightweight NLP model based on intent classification (non-LLM).

---

## 🚀 Running the Assistant

```bash
git clone https://github.com/sohaibdaoudi/ChangingTireAssistant_CV_NLP_Project.git
cd ChangingTireAssistant_CV_NLP_Project

python3 -m venv venv
source venv/bin/activate  # or `venv\Scripts\activate` on Windows

pip install -r requirements.txt
streamlit run app/main.py
```

---

## 🔮 Future Work

- [ ] Integrate multimodal reasoning for complex error recovery.
- [ ] Improve action segmentation with Transformers.
- [ ] Enhance voice assistant via on-device TTS/STT.

---

## 👨‍💻 Authors

- **SOHAIB DAOUDI** – [soh.daoudi@gmail.com](mailto:soh.daoudi@gmail.com)
- **MAROUANE MAJIDI** – [majidi.marouane0@gmail.com](mailto:majidi.marouane0@gmail.com)

---

## 📜 License

This project is licensed under the [MIT License](https://opensource.org/licenses/MIT). See the `LICENSE` file for more details.
