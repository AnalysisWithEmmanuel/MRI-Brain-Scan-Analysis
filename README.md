# 🧠 MRI Brain Scan Analysis | Alzheimer's Detection  
Python + Power BI Project | 44,000 MRI Scans | Images ➝ Data ➝ Insights

## 📚 Table of Contents
* [Project Overview](#project-overview)
* [Tools & Technologies](#tools--technologies)
* [Dataset Breakdown](#dataset-breakdown)
* [Feature Engineering](#feature-engineering)
* [Power BI Dashboard](#power-bi-dashboard)
* [Insights & Findings](#insights--findings)
* [Recommendations](Recommendations)
* [Repository Structure](#repository-structure)
* [Future Work](#future-work)

### Project Overview  
This project analyzes **44,000+ MRI brain scans** to extract image-based features that help understand the progression of **Alzheimer’s Disease**. Using **Python** for image processing and **Power BI** for interactive visualizations, we convert raw medical images into **actionable insights**.

### Tools & Technologies  
* Python (OpenCV, NumPy, Pandas, Matplotlib)  
* Power BI  
* Jupyter Notebook  
* Dataset of labeled brain MRI scans (NonDemented, Mild, Moderate, etc.)

### Dataset Breakdown  
The dataset contains MRI scans labeled under 4 categories:
* `NonDemented`
* `VeryMildDemented`
* `MildDemented`
* `ModerateDemented`

Each image was analyzed to extract:
* Mean pixel intensity
* Standard deviation of pixel intensity
* Entropy
* Edge density
* Center brightness

### Feature Engineering  
Python was used to automate image processing and extract meaningful features.

```python
import cv2
import numpy as np

img = cv2.imread('example.jpg', cv2.IMREAD_GRAYSCALE)
mean_intensity = np.mean(img)
std_intensity = np.std(img)
entropy = -np.sum((img/255.0) * np.log2(img/255.0 + 1e-10))

# Additional features
edges = cv2.Canny(img, 100, 200)
edge_density = np.sum(edges > 0) / edges.size

h, w = img.shape
center = img[h//4:3*h//4, w//4:3*w//4]
center_brightness = np.mean(center)
# Extracted features were compiled into a structured dataset to be visualized in Power BI.
```

#### 🖼️ 1. Dataset Exploration  
The MRI images were distributed across 4 labeled folders:
- `NonDemented`
- `VeryMildDemented`
- `MildDemented`
- `ModerateDemented`

Each image was grayscale, showing cross-sections of the brain from various angles. I manually examined samples to understand lighting, structure, and variation.

![images](https://github.com/user-attachments/assets/4a177594-069e-48c6-85a8-462c3bc4d549)

---

#### 🧮 2. Python Feature Extraction  
I wrote Python scripts using **OpenCV**, **NumPy**, and **Pandas** to extract the following features for each image:

- **Mean Pixel Intensity**: Measures overall brightness  
- **Standard Deviation**: Shows brightness variation  
- **Entropy**: Indicates the level of structural complexity  
- **Edge Density**: Captures texture and detail using Canny edge detection  
- **Center Brightness**: Focuses on brightness in the central brain area

![python](https://github.com/user-attachments/assets/7149c9de-3370-499a-947f-4e111ab20d1d)

Each scan was processed in a loop, and the features were saved row by row into a structured dataset.

---

#### 📁 3. Creating a Clean Feature Dataset (Excel/CSV)  
After feature extraction, I compiled everything into a structured **Excel file** (and CSV) containing:

| Filename       | Label           | Mean | Std Dev | Entropy | Edge Density | Center Brightness |  is_Augumented  |
|----------------|------------------|------|---------|---------|---------------|--------------------|--------------|
| Mild_1234.jpg  | MildDemented     | ...  | ...     | ...     | ...           | ...                |True          |
| Non_4567.jpg   | NonDemented      | ...  | ...     | ...     | ...           | ...                |False         |
| ...            | ...              | ...  | ...     | ...     | ...           | ...                | ...          |

![ece](https://github.com/user-attachments/assets/d39d8d76-9992-4231-924a-13382f18f79e)


This dataset became the **core input** for my Power BI dashboard.

---

### Power BI Dashboard

Once the Excel dataset was ready, I imported it into **Power BI** to build an interactive dashboard that visualizes disease patterns, image features, and comparisons between diagnosis classes.

#### Key Visuals Include:
- 📈 **Disease Progression Score**: Based on entropy and center brightness  
- 🌡️ **Scan Disorder Level**: Comparing all diagnosis classes  
- 💡 **Radiance Progression**: Mean brightness across classes  
- 🧠 **Top Diseased vs. Healthy Scans**  
- 📋 **Interactive Table**: All images with their extracted features  
- 📉 **Entropy Distribution**: Shows lower entropy in Alzheimer's patients  
- 🎯 **Brightness Variation**: Used to separate Normal vs. Diseased groups

![mri](https://github.com/user-attachments/assets/efe5560e-1061-4a63-b8c2-231209cebc70)
![mri 2](https://github.com/user-attachments/assets/c3ebe89e-5be7-4c3b-b1b1-c3f04e22a5cd)

The dashboard allows **filtering by diagnosis**, viewing statistical differences, and exploring trends across thousands of scans in just a few clicks.

### Insights & Findings
     
1.Diseased brains showed lower entropy and reduced center brightness
2. NonDemented scans had clearer structures and higher brightness variation
3. Entropy and brightness levels may support early Alzheimer’s detection

---

### 🧭 Recommendations  

Based on the image analysis and patterns observed across 44,000+ MRI brain scans, the following recommendations are proposed:

#### 1. ✅ Use Image-Based Features for Early Screening  
Features like **entropy** and **center brightness** showed significant differences between healthy and diseased scans — especially in Mild and VeryMildDemented categories.  
> 🧠 These could be used as **early screening indicators** before full cognitive symptoms appear.

#### 2. 🧪 Integrate Feature Extraction into Clinical Tools  
The Python-based feature extraction pipeline could be integrated into:
- Radiology image viewers
- Hospital EMR systems
- Research platforms

> ⚙️ Automatically tagging or flagging scans with abnormal entropy or brightness levels can help doctors **prioritize high-risk patients**.

#### 3. 📊 Extend Dashboard for Clinical Decision Support  
The Power BI dashboard could be adapted into a **clinical tool** with:
- Live scan upload & auto-analysis
- Diagnosis probability indicators
- Patient progression tracking over time

> 📈 Providing this visual decision support could assist neurologists and radiologists in making faster, evidence-driven decisions.

#### 4. 🔬 Use This Workflow for Other Brain Disorders  
This same pipeline (image ➝ features ➝ dataset ➝ dashboard) can be re-used for:
- Parkinson’s Disease
- Brain Tumor classification
- Stroke damage comparison

> 🧩 The flexible design means this project could serve as a **template** for other medical imaging tasks.

---

### Repository Structure
```
📁 mri-alzheimers-analysis/
├── data/                     # Feature CSV files
├── images/                   # Sample MRI scan images
├── notebooks/                # Jupyter notebooks
├── dashboards/               # Power BI .pbix files
├── README.md
└── requirements.txt
```

### Future Work

1.Build predictive ML models (e.g., CNNs)
2. Develop a web dashboard using Streamlit or Flask
3. Integrate with medical diagnosis APIs or electronic health records



Acknowledgements
Thanks to open-source medical datasets, radiologists, and the research community contributing to Alzheimer’s detection and analysis.
