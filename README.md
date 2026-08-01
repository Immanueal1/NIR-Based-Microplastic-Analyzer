# NIR-Based Microplastic Analyzer

**A portable, AI-powered device that identifies plastic types in real time using near-infrared spectroscopy.**

![Features and Capabilities](Visual%20Explainers/Features%20and%20capabilities.png)

---

## Overview

Microplastics are one of the most pervasive and hardest-to-detect forms of pollution — too small for the naked eye, too varied for simple sorting, and increasingly present in water, soil, and even food. This project explores a low-cost, portable way to identify plastic type on the spot, using near-infrared (NIR) spectroscopy paired with a trained machine learning classifier.

The device shines calibrated near-infrared light through a sample, captures its 6-channel spectral response with a dedicated NIR sensor, and classifies the material in real time — no lab equipment, no shipping samples off for analysis, no waiting.

This repository is a **public portfolio showcase** of the project: results, hardware photos, live demonstrations, and published research. The underlying source code, firmware, trained model, and raw dataset remain private — see [License & Usage](#license--usage) below.

**Published research:** International Research Journal of Modernization in Engineering Technology and Science (IRJMETS) — see [Published Research](#published-research).

---

## How It Works

![End-to-End Data Flow](Visual%20Explainers/End%20to%20end%20data%20flow%20of%20an%20ai%20based%20nir%20based%20microplastic%20analyer.png)

1. A sample is placed in a quartz cuvette and illuminated with an 850nm NIR LED
2. A 6-channel NIR sensor (610–860nm) captures the material's spectral reflectance
3. An ESP32 microcontroller handles signal acquisition and edge preprocessing
4. A trained classifier identifies the plastic type from its spectral "fingerprint"
5. Results are displayed instantly on an onboard OLED screen and a live web dashboard

---

## Published Research

This project's methodology and results were peer-reviewed and published in:

> **International Research Journal of Modernization in Engineering Technology and Science (IRJMETS)**
> e-ISSN: 2582-5208 · Impact Factor: 7.868
> Paper ID: 80400090574

📄 [View Certificate of Publication](<certificate of Publication.pdf>)

*The full paper is available on request or via citation — it is not hosted directly in this repository, as it contains circuit-level implementation detail that is kept private.*

---

## System Architecture

![End-to-End System Architecture](Visual%20Explainers/End%20to%20end%20system%20architecture.png)

![Hardware Connection Overview](<Visual Explainers/hardware connection architecture.png>)

The system is built around six core components: a 6-channel NIR sensor, an NIR LED illumination source, a quartz sample cuvette, an ESP32 microcontroller for edge processing, an OLED display for standalone use, and a companion web dashboard for extended monitoring and history.

---

## Target Materials

![Plastic Types Detected](<Visual Explainers/Plastic Types Detected by the AI-Based NIR Microplastic Analyzer.png>)

The classifier is trained to distinguish between 5 common plastic types:

| Plastic | Full Name | Common Uses |
|---|---|---|
| **PET** | Polyethylene Terephthalate | Bottles, food containers |
| **PE** | Polyethylene | Bags, films, containers |
| **PP** | Polypropylene | Bottle caps, packaging |
| **PS** | Polystyrene | Cups, cutlery, insulation |
| **PVC** | Polyvinyl Chloride | Pipes, cabling |

---

## Hardware

![Device Prototype](<images/device_photos/Image of real prototypee.png>)

A fully self-contained, portable enclosure housing the ESP32, the NIR sensor and LED, the sample cuvette holder, an OLED display, and onboard battery power — no external lab equipment required.

### From Concept to Prototype

![Development Journey](<Visual Explainers/Development journery from concept to real prototype.png>)

---

## Software & Dashboard

Alongside the standalone OLED interface, the device connects to a companion web dashboard for live monitoring, prediction history, and richer visualization.

**Onboard OLED Interface**

![OLED Interface Modes](images/dashboard_screenshots/oled_interface_modes.png)

**Web Dashboard**

![Web Dashboard](images/dashboard_screenshots/web_dashboard_ui.png)

---

## Results & Performance

The trained classifier (SVM, RBF kernel) achieves **97.0% accuracy** (5-fold cross-validation) across all 5 target plastic types.

**Spectral Signatures** — each plastic type produces a distinct, reproducible NIR reflectance profile across all 6 channels:

![Spectral Signature Overview](charts/spectral_signature_overview.png)

**Class Separability** — a PCA projection shows the classifier's decision boundaries are well-separated across classes:

![Class Separability PCA](charts/class_separability_pca.png)

**Dataset:** 1,000 calibrated NIR readings, perfectly balanced across all 5 classes (200 readings each — 100 dry, 100 wet conditions).

More visualizations — including per-channel breakdowns, moisture-condition comparisons, correlation heatmaps, and individual per-plastic spectral curves — are available in the [`charts/`](charts) and [`charts_v2/`](charts_v2) folders, or as complete compiled reports:

- 📊 [NIR Dataset Visualizations (PDF)](NIR_Dataset_Visualizations_watermark.pdf) — full 8-chart summary
- 📈 [Spectral Signatures of Plastics (PDF)](Spectral_signature_of_plastics_watermark.pdf) — individual per-plastic signature curves

---

## Demo

Live recordings of the physical device and dashboard in action:

| Recording | Description |
|---|---|
| [Live Classification Demo](<Live Recordings/Final prototype live recording .mp4>) | The analyzer classifying a plastic sample in real time |
| [Prototype Bench Test](<Live Recordings/Prototype before finishing touches.mp4>) | Early prototype during development and testing |
| [Sensor Reading Capture](<Live Recordings/Reading recording.mp4>) | Full spectral data acquisition sequence |
| [Web Dashboard Walkthrough](<Live Recordings/WebDashboard Recording .mp4>) | Extended demo of the live web dashboard |

---

## Tech Stack

`ESP32` · `NIR Spectroscopy (6-channel, 610–860nm)` · `Python` · `Flask` · `scikit-learn (SVM)` · `Streamlit` · `OLED Display`

---

## Limitations

In the interest of transparency:

- **Single-session validation:** current accuracy figures are based on a single laboratory capture session per class. Multi-session validation across varied environmental conditions and sample geometries is planned future work.
- **PE labeling:** the "PE" class as currently labeled may represent a specific PE subtype (LDPE) rather than the full range of generic polyethylene — this is being reviewed for a future dataset revision.
- **Spectral range:** the sensor covers a fixed 610–860nm range; classification is limited to plastics with distinguishable signatures within this band.

---

## License & Usage

This repository is a **portfolio and proof-of-work showcase only**. It contains no source code, firmware, trained model files, or raw datasets — all implementation details are kept private.

See [LICENSE](LICENSE) for full terms. **All rights reserved** — no part of this repository may be reproduced, copied, or reused without explicit written permission.

---

## Credits

**Created by:** [Your Name]
**GitHub:** [@your-handle](https://github.com/your-handle)

*[Add: solo project / capstone project at Institution Name, course/year — optional]*

Reference spectral databases used for validation: SLoPP / SLoPP-E (see [`docs/Refrence/`](docs/Refrence)).
