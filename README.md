<h1> ANPR (Automatic Number Plate Recognition) System</h1>
This project implements a robust pipeline for Automatic Number Plate Recognition (ANPR) using Python, OpenCV, and EasyOCR. The approach integrates classical image processing with deep learning-based Optical Character Recognition (OCR) to detect and decode license plates from vehicle images.

🔧 <h3>Libraries Used</h3>
cv2 (OpenCV) – for image processing and computer vision operations

numpy – for numerical operations and array manipulation

matplotlib – for visualizing intermediate results

imutils – for convenience functions in image translation, rotation, resizing, etc.

easyocr – for deep learning-based optical character recognition

<h3>🧩 1. Image Acquisition, Grayscale Conversion & Noise Suppression</h3>
Image Loading: The input image is read using OpenCV’s cv2.imread().

Grayscale Conversion: Color information is discarded using cv2.cvtColor() with cv2.COLOR_BGR2GRAY to simplify processing and reduce computational complexity.

Gaussian Blur: A Gaussian filter is applied via cv2.GaussianBlur() to suppress high-frequency noise and smooth the image, enhancing edge detection performance in subsequent steps.

<h3>🧠 2. Edge Detection & Region of Interest (ROI) Enhancement</h3>
Bilateral Filtering (optional): If used, it preserves edges while reducing noise—ideal for license plate clarity.

Edge Detection: The Canny edge detector (cv2.Canny()) is applied to extract prominent edges, which often correspond to plate boundaries and characters.

Morphological Operations (e.g., dilation or erosion) can optionally be applied to close gaps in edges and emphasize structural elements of the plate.

<h3>🔍 3. Contour Detection & License Plate Localization</h3>
Contour Extraction: Using cv2.findContours(), all external contours in the edge map are identified.

Filtering by Aspect Ratio & Area: Bounding rectangles are calculated for each contour. Contours that match the expected aspect ratio and area constraints of a license plate (typically rectangular and within a plausible size range) are shortlisted.

Mask Creation: A binary mask is created and applied to isolate the suspected license plate region, helping eliminate background noise.

<h3>🧾 4. Text Extraction Using EasyOCR</h3>
The localized plate region is passed to EasyOCR, which utilizes a deep learning model trained on diverse character sets and scripts.

EasyOCR automatically detects text orientation and performs character segmentation and recognition in a single step.

The output is a list of predicted text strings with associated confidence scores.



<h3>🎨 5. Result Rendering & Annotation</h3>
<img width="400" height="275" alt="Screenshot 2025-07-17 183823" src="https://github.com/user-attachments/assets/74d48b9d-a003-4168-b44c-d6df1e993665" />
<img width="380" height="250" src= "https://github.com/user-attachments/assets/8ad5287f-e063-4bcb-bc3c-dfc0f8eb1cfe"/>

The recognized license plate text is overlaid on the original image using cv2.putText() for visual confirmation.
A bounding box is drawn around the detected plate region using cv2.rectangle() or cv2.polylines().

Optionally, the result is saved or displayed using matplotlib.pyplot or cv2.imshow().
