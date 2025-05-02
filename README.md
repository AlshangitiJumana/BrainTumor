# 🧠 Brain Tumor Detection with YOLO: Multi-Version Comparative Study

This project compares various YOLO model versions and sizes (YOLOv5, YOLOv10, YOLOv11) for **brain tumor detection and classification** using MRI scans. The work is inspired by [Selçuk et al. (2023)](https://ieeexplore.ieee.org/abstract/document/10626992), and uses the **same dataset** for benchmarking purposes.

> 📊 This README summarizes our experiment, dataset, methods, and results—including precision/recall comparisons and performance trade-offs.

---

## 🧠 Motivation

Manual interpretation of MRI scans is time-consuming, expertise-dependent, and prone to delay—especially in overloaded healthcare systems like Saudi Arabia.

We aimed to:
- Automate tumor detection using YOLO-based deep learning models
- Compare multiple YOLO versions and model sizes on speed, recall, and precision
- Enhance **recall**, which is critical in medical diagnosis to reduce false negatives

---

## 🧪 Dataset

We used the publicly available dataset from Kaggle:  
📦 [Labeled MRI Brain Tumor Dataset](https://www.kaggle.com/datasets/ammarahmed310/labeled-mri-brain-tumor-dataset)

**Classes:**
- `glioma`
- `meningioma`
- `pituitary`
- `no tumor`

Each image was annotated with bounding boxes using **LabelImg**, and converted into YOLO format.  
The dataset split: 80% training / 20% testing  
YAML path config is provided in `brain_tumor_dataset.yaml`.

---

## 🧠 Models Compared

We tested 10 YOLO models:

| Version | Sizes       |
|---------|-------------|
| YOLOv5  | n, s, m     |
| YOLOv10 | n, s, m     |
| YOLOv11 | n, s, m     |
| YOLOv8  | s (baseline from Selçuk et al.) |

All models were trained with:
- `epochs = 50`
- `batch_size = 16`
- Same train/test split and augmentations

---

## 📈 Results

### 🔢 Overall Precision vs Recall

![YOLO Comparison](image (1).png)

📌 **Best Overall Recall**: `YOLOv5n` — 0.902  
📌 **Best Overall Precision**: `YOLOv11s` — 0.935  
📌 **Fastest Inference**: `YOLOv5n` — 0.8ms  
📌 **Largest Model**: `YOLOv5m` — 25M parameters  

| Model     | Precision | Recall | Params | Inference |
|-----------|-----------|--------|--------|-----------|
| YOLOv5n   | 0.914     | **0.902** | 2.5M   | **0.8ms** |
| YOLOv5m   | 0.918     | 0.900  | 25.0M  | 3.4ms     |
| YOLOv10s  | 0.908     | 0.896  | 8.0M   | 2.1ms     |
| YOLOv11s  | **0.935** | 0.861  | 9.4M   | 1.8ms     |
| YOLOv8s   | 0.913     | 0.885  | 11.1M  | 1.8ms     |

📊 See more in our notebook: [`YOLOversions_comparison.ipynb`](YOLOversions_comparison (1).ipynb)

---

## 🩻 Per-Class Recall

| Model     | Glioma | Meningioma | No Tumor | Pituitary |
|-----------|--------|------------|----------|-----------|
| YOLOv5m   | **0.966** | 0.945      | 0.705    | 0.982     |
| YOLOv11m  | 0.927  | **0.951**   | 0.705    | 0.945     |
| YOLOv11n  | 0.935  | 0.948      | 0.677    | **1.000** |

---

## 📝 Paper

You can read our full academic paper here:  
📄 [`CV_paper3.pdf`](paper.pdf)

---

## 🔍 Citation

If you use this code or results in your own work, please cite our study or give appropriate credit.  
Thank you!

---

## 📂 Repository Structure

