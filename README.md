# carbon-crunch-ocr

# 🧾 Carbon Crunch OCR Receipt Extraction Pipeline

## 📌 Overview

This project builds an end-to-end OCR pipeline to extract structured information from real-world receipt images. The system processes noisy, unstructured receipt photos and converts them into usable JSON data with confidence scores.

---

## ⚙️ Tech Stack

* **Python**
* **EasyOCR**
* **OpenCV**
* **NumPy**
* **Pandas**
* **Google Colab**

---

## 🔄 Pipeline Workflow

1. **Data Loading**

   * Images loaded from Google Drive or fallback local folder

2. **Image Preprocessing**

   * Noise removal (Gaussian Blur)
   * Deskewing using Hough Transform
   * Contrast enhancement (CLAHE)
   * Binarization (Otsu Thresholding)
   * Dark image correction (Gamma correction)

3. **OCR Extraction**

   * Text detection using EasyOCR
   * Confidence score captured for each text block

4. **Information Extraction**

   * Store Name
   * Date
   * Line Items
   * Total Amount

5. **Confidence Scoring**

   * Based on:

     * OCR confidence (50%)
     * Pattern validation (30%)
     * Keyword detection (20%)
   * Invalid values are penalized

6. **Output Generation**

   * Structured JSON per receipt
   * Confidence JSON per receipt
   * Financial summary across all receipts

---

## 📊 Output Structure

### Basic Output

```json
{
  "store_name": "ABC Store",
  "date": "12/04/2026",
  "items": [
    {"name": "Milk", "price": 50.0}
  ],
  "total_amount": 150.0
}
```

### Confidence Output

Includes confidence scores and low-confidence flags for each field.

---

## 📈 Financial Summary

* Total Spend
* Number of Transactions
* Average Transaction Value
* Spend per Store
* Receipts flagged for review

---

## 🧠 Confidence Scoring Methodology

Confidence is computed using:

* OCR confidence (0.5 weight)
* Regex/pattern validation (0.3 weight)
* Keyword presence (0.2 weight)

Low-confidence fields are flagged for potential human review.

---

## ⚠️ Challenges Faced

* OCR inaccuracies due to noisy and low-quality images
* Variability in receipt formats and layouts
* Missing or ambiguous total fields
* Difficulty in item extraction due to inconsistent spacing

---

## 🚀 Improvements Implemented

* Validation checks for numeric fields
* Fallback logic for total extraction
* Filtering of noisy OCR outputs
* Confidence penalty for invalid values
* Reproducible pipeline with fallback data handling

---

## 🔮 Future Improvements

* Use deep learning models (e.g., LayoutLM)
* Better table/line-item extraction
* Real-time API deployment
* Model monitoring using confidence thresholds

---

## 📂 Repository Structure

```
carbon-crunch-ocr/
 ┣ 📜 CarbonCrunch_OCR.ipynb
 ┣ 📜 README.md
 ┣ 📦 carbon_crunch_outputs.zip
```

---

## ▶️ How to Run

1. Open the notebook in Google Colab
2. Mount Google Drive (if using personal dataset)
3. Ensure sample images are available (fallback)
4. Run all cells sequentially
5. Download output ZIP

---

## ✅ Key Highlights

* End-to-end OCR pipeline
* Handles real-world noisy receipts
* Confidence-based reliability system
* Robust error handling (no crashes)
* Reproducible and production-aware design

---

## 👤 Author

**TARINI JAJORIA**

---
