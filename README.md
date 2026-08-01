# NIR-Based Microplastic Analyzer

> Portable AI-powered Near-Infrared Spectroscopy System for Real-Time Microplastic Identification

> **Public Portfolio Showcase** — This repository demonstrates the design, development, hardware integration, machine-learning workflow, and validation of a portable NIR-based microplastic analyzer. Source code, firmware, trained models, and raw datasets remain private.

---

# Overview

Microplastics are an emerging environmental concern due to their widespread presence in water, soil, food, and biological systems. This project presents a compact embedded system capable of identifying common plastic types using six-channel Near-Infrared spectroscopy and an AI classifier.

The workflow combines embedded electronics, spectroscopy, signal preprocessing, and machine learning to perform rapid material identification in approximately 1.8 seconds.

---

# Table of Contents

- Overview
- Features
- Device Overview
- How It Works
- Hardware
- Software
- Machine Learning Pipeline
- Dataset
- Results
- Dashboard
- Prototype
- Research
- Tech Stack
- Future Work
- Limitations
- License

---

# Features

- Portable battery-powered analyzer
- ESP32-based embedded platform
- Six-channel NIR spectroscopy
- Real-time plastic identification
- OLED user interface
- Flask dashboard
- Machine learning classification
- Modular architecture

---

# Device Overview

Replace this section with your hero render.

```md
![Device](images/device_gallery.png)
```

---

# How It Works

1. Place sample in quartz cuvette.
2. Illuminate with 850 nm NIR LED.
3. Acquire six spectral channels.
4. ESP32 transmits calibrated readings.
5. Python preprocessing.
6. Feature engineering.
7. SVM classification.
8. Display prediction.

---

# Hardware

- ESP32
- AS7263 NIR Sensor
- 850 nm LED
- Quartz Cuvette
- OLED Display
- Push Buttons
- Li-ion Battery

---

# Software

- Python
- Flask
- scikit-learn
- Streamlit
- Pandas
- NumPy
- Matplotlib

---

# Machine Learning

Pipeline:

Raw Spectrum → MSC → SNV → Savitzky-Golay → Scaling → Feature Vector → SVM → Prediction

---

# Dataset

- 1,000 calibrated NIR readings
- Five balanced plastic classes
- Dry and wet conditions
- Public repository includes only summary statistics

---

# Results

- Accuracy: **97.0%**
- Validation: **5-fold cross validation**
- Prediction time: **~1.8 s**

Insert:
- Performance figure
- Spectral signatures
- PCA plot

---

# Dashboard

Include dashboard screenshots demonstrating live prediction, confidence score, history, and monitoring.

---

# Prototype

Include the four-panel prototype gallery.

---

# Research

Published in IRJMETS.

Include publication certificate and citation.

---

# Repository Structure

```text
docs/
images/
charts/
reports/
demo/
README.md
LICENSE
```

---

# Tech Stack

Hardware:
ESP32, AS7263, OLED, Li-ion Battery

Software:
Python, Flask, scikit-learn, Streamlit

---

# Future Work

- Additional plastic classes
- PCB design
- Larger datasets
- Mobile app
- Cloud deployment

---

# Limitations

- Laboratory validation
- Limited spectral range
- Public showcase only

---

# License

All Rights Reserved.

This repository is intended as a portfolio showcase.

