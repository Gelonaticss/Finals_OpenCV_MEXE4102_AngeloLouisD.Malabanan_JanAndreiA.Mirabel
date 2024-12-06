
<a id="top"></a>
<div align="center">
  <h1>Outlining Shapes of Small Household Objects with Contours</h1>
</div>

## Table of Contents
- [Introduction](#introduction)
  - [Problem and Significance in Computer Vision](#problem-and-significance-in-computer-vision)
- [Abstract](#abstract)
  - [Project's Objective](#projects-objective)
  - [Approach](#approach)
  - [Expected Results](#expected-results)
- [Project Methods](#project-methods)
- [Conclusion](#conclusion)
  - [Summary Of Findings](#summary-of-findings)
  - [Challenges](challenges)
  - [Solutions](solutions)
  - [Outcomes](outcomes)
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
