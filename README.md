
<a id="top"></a>
<div align="center">
  <h1>Outlining Shapes of Small Household Objects with Contours</h1>
</div>

## Table of Contents
- [Introduction](#introduction)
- [Abstract](#abstract)
  - [Project's Objective](#projects-objective)
  - [Approach](#approach)
  - [Expected Results](#expected-results)
- [Project Methods](#project-methods)
- [Conclusion](#conclusion)
  - [Summary Of Findings](#summary-of-findings)
  - [Challenges](#challenges)
  - [Solutions](#solutions)
  - [Outcomes](#outcomes)
- [References](#references)
- [Group Members](#group-members)

---

## Introduction

### Problem and Significance in Computer Vision
- **Object Recognition** is a fundamental task in *computer vision* with applications in automation, robotics, and AI-powered systems.
- **Small Household Objects** often present challenges due to their *variety of shapes*, *sizes*, and *textures*.
- This project highlights the significance of **contour detection** to identify, outline, and process object shapes effectively.
- Contour detection provides a **foundation for advanced tasks** like feature extraction, segmentation, and classification.

---

<div align="right">
  <a href="#top">⬆️ Back to Top</a>
</div>

## Abstract

### Project's Objective
- **Analyze and outline shapes** of small household objects using **contour detection** techniques.
- Apply **OpenCV** to improve shape recognition accuracy and enhance the **visualization of object contours**.

<div align="right">
  <a href="#top">⬆️ Back to Top</a>
</div>

### Approach
- Utilize the **Small Home Objects (SHO) Image Dataset** from Kaggle.
- Implement **OpenCV's contour detection algorithm** to highlight object shapes.
- Process dataset images to ensure **preparation and compatibility** with contour algorithms.

<div align="right">
  <a href="#top">⬆️ Back to Top</a>
</div>

### Expected Results
- Accurate **outlining of object shapes** in the dataset.
- Improved **understanding and application** of contour detection in real-world scenarios.
- A **step-by-step guide** for others to replicate and extend the work.

---

<div align="right">
  <a href="#top">⬆️ Back to Top</a>
</div>

## Project Methods

- **Step 1: Dataset Acquisition**
  - Download the **Small Home Objects (SHO) Image Dataset** from Kaggle.
  - Verify dataset integrity and compatibility with project requirements.

- **Step 2: Preprocessing Images**
  - Convert images to *grayscale* using **OpenCV**.
  - Apply **Gaussian Blurring** to reduce noise.
  - Use **thresholding techniques** to enhance contour visibility.

- **Step 3: Contour Detection**
  - Utilize the **cv2.findContours()** function from OpenCV.
  - Configure contour approximation parameters for accurate outlining.
  - Iterate through detected contours to highlight shapes.

- **Step 4: Filtering Noise**
  - Use **erosion and dilation** to filter out small, irrelevant contours caused by noise such as cracks, shadows, or background inconsistencies.
  - Apply conditional logic to focus on outlining larger shapes and ignore minor artifacts.

- **Step 5: Visualization and Annotation**
  - Draw detected contours on the original images.
  - Label contours with indices for better analysis.

- **Step 6: Result Evaluation**
  - Evaluate the accuracy and quality of detected contours.
  - Compare results across different object types.

- **Step 7: Documentation and Deployment**
  - Document the process in a well-structured GitHub repository.
  - Ensure reproducibility by sharing code, datasets, and insights.

---

<div align="right">
  <a href="#top">⬆️ Back to Top</a>
</div>

## Conclusion

### Summary Of Findings
- **Noise Issues:** The dataset contained a significant amount of noise, such as shadows, cracks, and objects blending with the background due to similar colors or lighting conditions.
- **Complexity in Object Colors:** Objects with multiple shades, such as the statue, presented additional challenges in segmentation and contour detection.

### Challenges
- **Segmentation Difficulties:** Shadows, cracks, and similar background-object colors led to difficulties in separating objects from their backgrounds.
- **Contour Detection Limitations:** Smaller or irrelevant shapes, such as shadows and cracks, were often mistakenly included as contours.

### Solutions
- **Erosion and Dilation:** These operations helped reduce noise and improve the accuracy of contour detection.
- **Conditional Contour Filtering:** A size threshold was applied to ignore smaller, irrelevant shapes and focus on outlining larger object contours.

### Outcomes
- Contours for most objects were successfully detected, providing a clear outline of shapes.
- The implemented methods and strategies can serve as a basis for further improvements and applications in real-world scenarios.

---
## Additional Materials

### Cloning the Repository
> *This code is used to clone the GitHub repository that contains the dataset.*
```python
#Step 1: Clone the Project Repository
# Cloning the repository containing the dataset and project files.
!git clone https://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@github.com/Gelonaticss/Finals_OpenCV_MEXE4102_AngeloLouisD.Malabanan_JanAndreiA.Mirabel.git

# Change the directory to the cloned repository
%cd Finals_OpenCV_MEXE4102_AngeloLouisD.Malabanan_JanAndreiA.Mirabel/

# Clear output for cleaner notebook display
from IPython.display import clear_output
clear_output()
```
### Application of outlining shapes of small household objects with contours in Handwatch
> *The "file path" should be updated to match the location of the image that will be processed.*
```python
# Step 2: Import Required Libraries
# Importing the OpenCV library for image processing and NumPy for numerical operations.
import cv2
import numpy as np
from google.colab.patches import cv2_imshow

# Step 3: Load and Process the Image
# Load the Image
# The image is loaded from the dataset folder.
img = cv2.imread("file path")

# Convert Image to Grayscale
# Grayscale simplifies image processing tasks by reducing dimensions.
gray = cv2.cvtColor(img,cv2.COLOR_BGR2GRAY)

# Apply Thresholding
# Thresholding creates a binary image for contour detection.
ret, thresh = cv2.threshold(gray, 50, 255, 1)

# Step 4: Reduce Noise with Morphological Operations
# Erosion
# Reduces noise by eroding boundaries.
kernel = np.ones((5,5), np.uint8)
erode_image = cv2.erode(thresh,kernel, iterations=1)

# Dilation
# Expands contours and fills small gaps.
dilate_image = cv2.dilate(erode_image, kernel, iterations=1)

# Step 5: Detect and Draw Contours
# Find Contours
# Contours are detected from the processed binary image.
contours,h = cv2.findContours(dilate_image,1,2)

# ### Filter and Draw Contours
# Contours are filtered by area and dimensions before being outlined on the original image.
for cnt in contours:
    x, y, w, h = cv2.boundingRect(cnt)  # Get bounding rectangle for each contour
    area = cv2.contourArea(cnt)        # Calculate contour area
    if area > 500 and w > 10:          # Filter contours by area and width
        cv2.drawContours(img, [cnt], 0, (255, 255, 0), 4)  # Draw contours with yellow color

# Step 6: Annotate Images for Visualization
# Add captions to each image for better understanding of the stages.
grayscale = cv2.putText(gray,"Grayscale Image",(25,150),cv2.FONT_HERSHEY_COMPLEX,1,(255,255,255),2)
thresho = cv2.putText(thresh,"Thresholded Image",(25,150),cv2.FONT_HERSHEY_COMPLEX,1,(255,255,255),2)
out = cv2.putText(img,"Outlined Image",(25,150),cv2.FONT_HERSHEY_COMPLEX,1,(255,255,255),2)

# Step 7: Display the Processed Images
# Show the Grayscale, Thresholded, and Outlined images.

cv2_imshow(grayscale)  # Display Grayscale Image
cv2_imshow(thresho)    # Display Thresholded Image
cv2_imshow(out)        # Display Image with Contours Outlined
```

---
<div align="right">
  <a href="#top">⬆️ Back to Top</a>
</div>

## References
- OpenCV Documentation: [Documentation](https://docs.opencv.org)
- Kaggle Dataset: [Small Home Objects (SHO) Image Dataset](https://www.kaggle.com/datasets/hosseinmousavi/small-home-objects-sho-image-dataset)
- Final Requirement Instructions: [MeXEE402_Finals_4102](https://github.com/MikkoDT/MeXEE402_Finals_4102)
- Additional resources on contour detection from OpenCV tutorials.

---

<div align="right">
  <a href="#top">⬆️ Back to Top</a>
</div>

## Group Members
1. Malabanan, Angelo Louis D. (21-04184)
2. Mirabel, Jan Andrei A. (21-02724)

<div align="right">
  <a href="#top">⬆️ Back to Top</a>
</div>
