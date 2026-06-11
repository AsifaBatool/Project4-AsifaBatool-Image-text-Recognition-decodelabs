# 🔍 Image Text Recognition using OCR

> **DecodeLabs Internship Project**

A complete Optical Character Recognition (OCR) pipeline built in Python that extracts text from images using preprocessing techniques and the Tesseract OCR engine.

---

## 📋 Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Pipeline](#pipeline)
- [Installation](#installation)
- [Usage](#usage)
- [Output](#output)
- [Project Structure](#project-structure)
- [Dependencies](#dependencies)

---

## Overview

This project implements a professional-grade OCR processor that takes an image as input, applies a series of preprocessing steps to enhance text clarity, and then extracts the text using Google's Tesseract OCR engine. It was developed as part of the **DecodeLabs Internship Program**.

---

## Features

- ✅ Automatic image download if no local image is provided
- ✅ Grayscale conversion for simplified processing
- ✅ Gaussian blur for noise reduction
- ✅ Adaptive thresholding for improved text/background contrast
- ✅ Text extraction via Tesseract OCR
- ✅ Saves preprocessed images and extracted text to an output directory
- ✅ Matplotlib visualization of each preprocessing stage
- ✅ Clean, modular `OCRProcessor` class with full error handling

---

## Pipeline

The OCR processing pipeline runs in the following order:

```
Input Image
    │
    ▼
1. Load Image
    │
    ▼
2. Convert to Grayscale
    │
    ▼
3. Apply Gaussian Blur  (kernel: 5×5)
    │
    ▼
4. Adaptive Thresholding  (block size: 11, constant: 2)
    │
    ▼
5. Extract Text  (Tesseract OCR — OEM 3, PSM 6)
    │
    ▼
6. Save Results  → output/gray.jpg, output/threshold.jpg, output/result.txt
```

---

## Installation

### 1. Clone or open the notebook

Open the notebook in [Google Colab](https://colab.research.google.com/) or run it locally.

### 2. Install Python dependencies

```bash
pip install pytesseract opencv-python matplotlib numpy requests
```

### 3. Install Tesseract OCR engine

**Linux / Google Colab:**
```bash
sudo apt update
sudo apt install tesseract-ocr
```

**Windows:**  
Download the installer from [UB Mannheim](https://github.com/UB-Mannheim/tesseract/wiki) and add it to your system PATH.

**macOS:**
```bash
brew install tesseract
```

---

## Usage

### Run via the `main()` function

```python
python ocr_processor.py
```

The script will automatically download a sample image if none is found at `images/sample.png`.

### Use the `OCRProcessor` class directly

```python
from ocr_processor import OCRProcessor

processor = OCRProcessor(image_path="images/sample.png", output_dir="output")
processor.process()
```

### Run individual steps

```python
processor = OCRProcessor("images/sample.png")

processor.load_image()
processor.convert_to_grayscale()
processor.apply_gaussian_blur(kernel_size=(5, 5))
processor.apply_adaptive_threshold(block_size=11, constant=2)
processor.extract_text()
processor.save_preprocessing_results()
processor.save_extracted_text()
processor.print_extracted_text()
processor.display_results()  # Optional visualization
```

---

## Output

After a successful run, the `output/` directory will contain:

| File | Description |
|------|-------------|
| `gray.jpg` | Grayscale version of the input image |
| `threshold.jpg` | Binary image after adaptive thresholding |
| `result.txt` | Extracted text from the image |

A 2×2 matplotlib figure is also generated showing each stage of the pipeline visually.

---

## Project Structure

```
ocr-project/
│
├── images/
│   └── sample.png          # Input image (auto-downloaded if missing)
│
├── output/
│   ├── gray.jpg             # Preprocessed grayscale image
│   ├── threshold.jpg        # Preprocessed threshold image
│   └── result.txt           # Extracted text output
│
├── ocr_processor.py         # Main OCR pipeline script / notebook
└── README.md
```

---

## Dependencies

| Library | Purpose |
|---------|---------|
| `opencv-python` | Image loading and preprocessing |
| `pytesseract` | Python wrapper for Tesseract OCR |
| `numpy` | Array operations |
| `matplotlib` | Visualization of pipeline stages |
| `requests` | Downloading sample images |
| `Tesseract OCR` | Underlying OCR engine |

---

## Author

Developed as part of the **DecodeLabs Internship Program**, 2024.
