# NIR-Based Microplastic Analyzer

### Portable AI-Powered Near-Infrared Spectroscopy System for Real-Time Microplastic Identification

---

![NIR Microplastic Analyzer Hardware Prototype](images/device_photos/Image%20of%20real%20prototypee.png)
*Figure 1: Custom portable hardware prototype analyzer featuring an integrated 6-channel NIR optical sensor, quartz sample cuvette holder, 4-mode OLED UI display, and rechargeable battery enclosure.*

---

## 📖 Overview

Microplastic contamination in aquatic environments poses a critical threat to global ecosystems, marine life, and human food safety. Traditional environmental microplastic identification relies on costly, labor-intensive laboratory techniques such as FT-IR and Raman spectroscopy. 

This project presents a **portable, low-cost Near-Infrared (NIR) microplastic analyzer** that bridges laboratory spectroscopy with real-time field deployment. By combining a 6-channel multi-spectral optical sensor (610–860 nm), custom dual-illumination optics, edge microcontroller data acquisition, and machine learning classification algorithms, the system identifies common environmental plastic polymers within **1.8 seconds**.

The solution features a dual-interface architecture: an autonomous hardware unit with an integrated OLED display for field operators, alongside a real-time web-based classification dashboard for remote environmental monitoring and session data analytics.

> **📌 Portfolio Showcase Notice:**  
> This repository serves as a public proof-of-work portfolio showcasing system engineering, physical prototyping, dataset analysis, and machine learning results. Underlying firmware source code (`.ino`), backend API scripts, training pipelines, raw tabular sensor data, and binary model artifacts (`.pkl`) are preserved in private working archives.

---

## ⚙️ How It Works

```
┌───────────────────────────┐     ┌───────────────────────────┐     ┌───────────────────────────┐     ┌───────────────────────────┐
│  1. Sample Preparation    │ ──► │  2. NIR Optical Capture   │ ──► │ 3. Preprocessing & Scaling│ ──► │   4. Real-Time Inference  │
│ Cuvette inserted in path  │     │ 6-channel (610-860nm)     │     │ SNV Feature Normalization │     │ 97% RBF-SVM Classifier    │
└───────────────────────────┘     └───────────────────────────┘     └───────────────────────────┘     └───────────────────────────┘
```

1. **Sample Insertion & Optical Illumination:** The water or dry microplastic sample is placed in a high-purity quartz cuvette holder positioned between an 850 nm NIR LED light source and a 6-channel optical spectral sensor.
2. **Multi-Channel Spectral Acquisition:** The sensor captures raw reflectance intensities across 6 discrete NIR wavelengths (610 nm, 680 nm, 730 nm, 760 nm, 810 nm, and 860 nm).
3. **Edge Signal Preprocessing:** Reflectance signals undergo baseline dark-current subtraction and Standard Normal Variate (SNV) transformation to eliminate optical path length and particle scattering variances.
4. **Machine Learning Classification & Output:** The preprocessed feature vector is evaluated by an RBF-kernel Support Vector Classifier (`SVC(C=100)`), displaying the predicted plastic polymer type and confidence score on both the physical OLED screen and the web dashboard.

![End-to-End Data Flow Pipeline](Visual%20Explainers/End%20to%20end%20data%20flow%20of%20an%20ai%20based%20nir%20based%20microplastic%20analyer.png)
*Figure 2: End-to-end optical acquisition, preprocessing, machine learning classification, and dual-interface data flow pipeline.*

---

## 📜 Published Academic Research

The theoretical framework, optical sensor integration methodology, and preliminary classification results of this project have been published in a peer-reviewed scientific journal:

| Scientific Journal Metric | Publication Detail |
| :--- | :--- |
| **Journal Name** | *International Research Journal of Modernization in Engineering Technology and Science* (**IRJMETS**) |
| **Publication Identifiers** | **e-ISSN:** 2582-5208 \| **Scientific Impact Factor:** 7.868 |
| **Paper ID / Reference** | `80400090574` |
| **Publication Certificate** | [[PDF] Official IRJMETS Certificate of Publication](certificate%20of%20Publication.pdf) |

---

## 📐 System Architecture

The system integrates optical hardware, edge computing, backend communication, and machine learning into a unified real-time architecture:

![System Architecture Overview](Visual%20Explainers/End%20to%20end%20system%20architecture.png)
*Figure 3: Conceptual hardware-to-cloud system architecture block diagram.*

![Hardware Connection Architecture](Visual%20Explainers/hardware%20connection%20architecture.png)
*Figure 4: System hardware block diagram illustrating power distribution, optical light path, data communication, and control signal flow.*

---

## 🧪 Target Materials

The analyzer is trained to identify the 5 most prevalent environmental microplastic pollutants:

| Polymer | Chemical Name | Typical Consumer & Industrial Uses | Environmental Risk Level |
| :---: | :--- | :--- | :---: |
| **PET** | Polyethylene Terephthalate | Beverage bottles, food packaging containers, synthetic polyester textiles | High |
| **PE** | Polyethylene (LDPE/HDPE) | Single-use shopping bags, squeeze bottles, plastic film, container caps | High |
| **PP** | Polypropylene | Reusable food containers, bottle caps, drinking straws, automotive parts | Moderate |
| **PS** | Polystyrene | Disposable cutlery, rigid foam insulation, food clamshells, packaging | High |
| **PVC** | Polyvinyl Chloride | Water supply pipes, credit cards, medical tubing, synthetic leather | Severe |

![Target Plastic Types Detected](Visual%20Explainers/Plastic%20Types%20Detected%20by%20the%20AI-Based%20NIR%20Microplastic%20Analyzer.png)
*Figure 5: Target plastic polymers classified by the AI-powered NIR Analyzer system.*

---

## 🛠️ Hardware & Engineering Evolution

The hardware prototype was engineered through iterative optical testing and CAD enclosure modeling:

- **Optical Core:** 6-channel AS7263 NIR multi-spectral sensor (610, 680, 730, 760, 810, 860 nm) paired with an 850 nm NIR illumination LED.
- **Microcontroller:** ESP32 development board managing I2C sensor polling, multi-mode button state logic, and Wi-Fi streaming.
- **User Interface:** 0.96-inch OLED display providing autonomous 4-mode cyclic navigation.
- **Power Management:** Internal 3.7V Li-ion battery integrated with dual DC-DC voltage regulators (3.3V stable bus).

![Development Journey from Concept to Prototype](Visual%20Explainers/Development%20journery%20from%20concept%20to%20real%20prototype.png)
*Figure 6: Hardware evolution timeline from optical theory and breadboard circuit validation to 3D housing design and integrated enclosure assembly.*

---

## 💻 Software & User Interfaces

The platform features two complementary interfaces for local field operations and remote lab monitoring:

| OLED Hardware Interface | Web Classifier Dashboard |
| :---: | :---: |
| ![OLED 4-State Navigation Interface](images/dashboard_screenshots/oled_interface_modes.png) | ![Streamlit Real-Time Web Classifier UI](images/dashboard_screenshots/web_dashboard_ui.png) |
| *Figure 7: Physical OLED 4-state navigation UI (Home, WiFi, Predict Engine, Info).* | *Figure 8: Streamlit web dashboard displaying live spectral curves and classification output.* |

---

## 📈 Results & Classification Performance

Machine learning evaluations were conducted across calibrated 6-channel NIR spectral datasets:

- **Primary Classification Model:** **Support Vector Classifier with Radial Basis Function Kernel (`SVC(C=100, kernel='rbf')`)**.
- **Overall Cross-Validation Accuracy:** **97.0%** (evaluated via 5-fold cross-validation).
- **Inference Latency:** **< 1.8 seconds** per prediction cycle.

> ⚠️ **Validation Caveat:**  
> Reported accuracy figures were evaluated on a single-session laboratory dataset under controlled ambient conditions. Multi-session validation across environmental microplastic samples, varied particle geometries, and field aquatic turbidities is designated for future research.

### **Flagship Spectral & Classification Visuals**

| Overlaid NIR Spectral Signatures | 2D PCA Class Separability |
| :---: | :---: |
| ![NIR Spectral Signatures Overview](charts/spectral_signature_overview.png) | ![2D PCA Class Separability Scatter Plot](charts/class_separability_pca%20v2.png) |
| *Figure 9: Mean reflectance fingerprints (610–860 nm) with ±1 std confidence bands.* | *Figure 10: 2D Principal Component Analysis (PCA) scatter plot showing linear/RBF decision cluster separation.* |

### **Compiled Visual PDF Reports**
- [[PDF] NIR Dataset Visualizations Report](NIR_Dataset_Visualizations_watermark.pdf) — Complete 8-chart visual summary report.
- [[PDF] Spectral Signature of Plastics Report](Spectral_signature_of_plastics_watermark.pdf) — Individual B-spline signature curves for all 5 target polymers.
- Browse full image sets in the [charts/](charts/) and [charts_v2/](charts_v2/) directories.

---

## 📊 Dataset Summary

The primary dataset consists of calibrated 4-phase spectra recorded across target plastic classes and reference baselines:

| Plastic Type | DRY Condition Spectra | WET Condition Spectra | Total `NIR_ONLY` Readings | Dataset Share |
| :--- | :---: | :---: | :---: | :---: |
| **PET** | 100 readings | 100 readings | **200 readings** | 20.0% |
| **PE** | 100 readings | 100 readings | **200 readings** | 20.0% |
| **PP** | 100 readings | 100 readings | **200 readings** | 20.0% |
| **PS** | 100 readings | 100 readings | **200 readings** | 20.0% |
| **PVC** | 100 readings | 100 readings | **200 readings** | 20.0% |
| **Total** | **500 readings** | **500 readings** | **1,000 readings** | **100.0% Perfectly Balanced** |

*Note: The complete dataset contains 3,600 valid 4-phase spectra (`NIR_ONLY`: 1,000, `ALL_ON`: 1,000, `DARK_1`: 800, `DARK_2`: 800) audit-verified for scientific consistency in [docs/NIR_Dataset_Excel_Summary.xlsx](docs/NIR_Dataset_Excel_Summary.xlsx).*

---

## 🎥 Video Demonstrations

System operation and software workflows are recorded in the [Live Recordings/](Live%20Recordings) directory:

| Video Recording File | File Size | Duration | Video Description | Direct File Link |
| :--- | :---: | :---: | :--- | :---: |
| **`Final prototype live recording .mp4`** | 3.86 MB | 19.3 s | Live video demonstration of physical analyzer classifying plastic samples | [Watch Video](Live%20Recordings/Final%20prototype%20live%20recording%20.mp4) |
| **`Prototype before finishing touches.mp4`** | 6.59 MB | 34.8 s | Demonstration of early hardware prototype enclosure during bench testing | [Watch Video](Live%20Recordings/Prototype%20before%20finishing%20touches.mp4) |
| **`Reading recording.mp4`** | 24.27 MB | ~1m 35s | Sensor data acquisition sequence and serial stream recording | [Watch Video](Live%20Recordings/Reading%20recording.mp4) |
| **`WebDashboard Recording .mp4`** | 97.03 MB | ~5m 12s | Comprehensive video demonstration of Streamlit web classifier dashboard | [Watch Video](Live%20Recordings/WebDashboard%20Recording%20.mp4) |

---

## 🖼️ Complete Image & Asset Gallery

Below is a catalog of all visual assets available in this repository:

| Visual Asset Description | Relative File Path | Category | Direct Link |
| :--- | :--- | :---: | :---: |
| **Comprehensive System Overview Diagram** | `Visual Explainers/Overview Image.png` | Infographic | [View Image](Visual%20Explainers/Overview%20Image.png) |
| **5-Class Target Balance Donut Chart** | `charts/class_distribution.png` | Result Chart | [View Image](charts/class_distribution.png) |
| **DRY vs. WET Signature Shift Plot** | `charts/dry_vs_wet_comparison.png` | Result Chart | [View Image](charts/dry_vs_wet_comparison.png) |
| **Per-Channel Mean Intensity Bar Grid** | `charts/channel_comparison_grid.png` | Result Chart | [View Image](charts/channel_comparison_grid.png) |
| **NIR Channel Correlation Heatmap** | `charts/channel_correlation_heatmap (2).png` | Result Chart | [View Image](charts/channel_correlation_heatmap%20%282%29.png) |
| **Performance & Caveat Summary Graphic** | `charts/accuracy_confidence_summary.png` | Result Chart | [View Image](charts/accuracy_confidence_summary.png) |
| **Dataset Composition Dashboard Panel** | `charts/sample_composition_dashboard.png` | Result Chart | [View Image](charts/sample_composition_dashboard.png) |
| **Dataset Overview Flowchart** | `charts/Data set composition over view.png` | Result Chart | [View Image](charts/Data%20set%20composition%20over%20view.png) |
| **PET B-Spline Spectral Signature Curve** | `charts_v2/spectral_signature_PET.png` | Spectral Curve | [View Image](charts_v2/spectral_signature_PET.png) |
| **PE B-Spline Spectral Signature Curve** | `charts_v2/spectral_signature_PE.png` | Spectral Curve | [View Image](charts_v2/spectral_signature_PE.png) |
| **PP B-Spline Spectral Signature Curve** | `charts_v2/spectral_signature_PP.png` | Spectral Curve | [View Image](charts_v2/spectral_signature_PP.png) |
| **PS B-Spline Spectral Signature Curve** | `charts_v2/spectral_signature_PS.png` | Spectral Curve | [View Image](charts_v2/spectral_signature_PS.png) |
| **PVC B-Spline Spectral Signature Curve** | `charts_v2/spectral_signature_PVC.png` | Spectral Curve | [View Image](charts_v2/spectral_signature_PVC.png) |
| **Public NIR Dataset Excel Summary** | `docs/NIR_Dataset_Excel_Summary.xlsx` | Spreadsheet | [View File](docs/NIR_Dataset_Excel_Summary.xlsx) |
| **Public SLoPP / SLoPP-E Raman Reference** | `docs/Refrence` | Reference Data | [Browse Folder](docs/Refrence) |

---

## 💻 Technology Stack

`ESP32 Microcontroller` · `AS7263 NIR Spectroscopy` · `Python 3.12` · `scikit-learn` · `Support Vector Machines (SVM)` · `NumPy` · `Pandas` · `SciPy` · `Flask REST API` · `Streamlit Web UI` · `OpenPyXL`

---

## ⚠️ System Limitations

1. **Single-Session Laboratory Dataset:** Model training and accuracy metrics were evaluated on laboratory samples under uniform ambient conditions. Further multi-session field validation is required.
2. **Polymer Sub-Classification:** PE sample captures reflect Low-Density Polyethylene (LDPE); further training is required to distinguish High-Density Polyethylene (HDPE).
3. **Spectral Resolution:** Optical sensing is constrained to the 6 discrete wavelength channels of the AS7263 NIR sensor (610 nm to 860 nm).

---

## 🔒 License & Usage Terms

This project and repository contents are governed by the [LICENSE](LICENSE) file (**All Rights Reserved**).

- **Purpose:** Provided strictly for portfolio presentation, academic demonstration, and proof-of-work evaluation.
- **Restrictions:** No permission is granted to copy, reproduce, modify, distribute, sublicense, or build upon any portion of this repository or its underlying concepts without prior written consent from the copyright holder.

---

## 👤 Credits & Attribution

- **Project Lead & System Developer:** `[Your Name / GitHub Handle]`
- **Academic Institution:** `[Your University / Department]`
- **Publication Reference:** IRJMETS Paper ID `80400090574` (2026)
