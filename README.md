# Watershed Medical Image Segmentation

Marker-controlled Watershed segmentation applied to medical chest X-ray images (PneumoniaMNIST) to separate overlapping pathological regions.

## Overview

Classical thresholding techniques (Otsu, Adaptive Thresholding) often fail when foreground regions overlap or touch, merging them into a single connected component.

This project demonstrates how marker-controlled Watershed, combined with Distance Transform, enables structured and measurable region separation.

The objective is not medical diagnosis, but demonstrating robust segmentation logic in noisy medical imaging scenarios.

---

## Dataset

- PneumoniaMNIST (MedMNIST)
- 28×28 grayscale chest X-ray images
- Binary labels: 0 = Normal, 1 = Pneumonia

Dataset reference:
https://medmnist.com/

---

## Methodology

### 1. Preprocessing
- CLAHE (Contrast Limited Adaptive Histogram Equalization)
- Median filtering for noise reduction

### 2. Thresholding (Failure Case)
- Otsu Threshold
- Adaptive Threshold

Both methods merge touching pathological regions into a single blob.

### 3. Distance Transform
Computes distance from each foreground pixel to nearest background pixel.
Local maxima correspond to object centers.

### 4. Marker Creation
Markers are placed at local maxima to serve as reliable seeds.

### 5. Watershed Segmentation
Flooding process expands from markers and constructs closed boundaries where regions meet.

---

## Key Insight

Thresholding alone is insufficient when topology matters.

Marker-controlled Watershed:
- Separates touching structures
- Produces closed region boundaries
- Enables region-level measurement and analysis

---

## Project Structure
watershed-medical-image-segmentation/
│
├── watershed_segmentation_medical.ipynb
├── requirements.txt
├── images/
│ ├── original.png
│ ├── otsu_failure.png
│ ├── watershed_result.png


---

## Technologies

- Python
- OpenCV
- NumPy
- Matplotlib

---

## Authors

- Lorenzo Ferrer de Oya
- Ariel Núñez Valencia
- Data Science and Artificial Intelligence