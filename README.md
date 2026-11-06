# EXP.NO-6-edge-detection--Opencv.
 # Aim
To perform edge detection using Sobel, Roberts, Prewitt, Laplacian, and Canny edge detectors.

# Software Required
Anaconda – Python 3.7

Jupyter Notebook / VS Code

OpenCV (cv2)

NumPy

Matplotlib

# Algorithm
Step 1:
Import all the necessary modules for the program.

Step 2:
Load an image using cv2.imread().

Step 3:
Convert the image to grayscale.

Step 4:
Apply Sobel operator using OpenCV to detect edges.

Step 5:
Apply Prewitt operator using custom kernels.

Step 6:
Apply Roberts operator using custom kernels.

Step 7:
Apply Laplacian operator using OpenCV.

Step 8:
Apply Canny edge detector using OpenCV.

Step 9:
Display all edge-detected images for comparison.

# Developed By
# Name: MONISHA S
# Register No: 212225040258

# code:
```
import cv2
import numpy as np
import matplotlib.pyplot as plt

image = cv2.imread('PHOTO.jpeg')  # Replace with your image path
gray_image = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)

# Original Image
plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))
plt.title('Original Image')
plt.axis('off')

# Sobel Edge Detection
sobel_x = cv2.Sobel(gray_image, cv2.CV_64F, 1, 0, ksize=5)
sobel_y = cv2.Sobel(gray_image, cv2.CV_64F, 0, 1, ksize=5)
sobel_combined = cv2.magnitude(sobel_x, sobel_y)

plt.imshow(sobel_combined, cmap='gray')
plt.title('Sobel Edge Detection')
plt.axis('off')

# Laplacian Edge Detection
blurred = cv2.GaussianBlur(gray_image, (3, 3), 0)
laplacian = cv2.Laplacian(blurred, cv2.CV_64F, ksize=3)

laplacian = cv2.normalize(laplacian, None, 0, 255, cv2.NORM_MINMAX)
laplacian = np.uint8(laplacian)
laplacian = cv2.addWeighted(
    laplacian, 0.5,
    np.full_like(laplacian, 128), 0.5, 0
)

plt.figure(figsize=(8, 8))
plt.imshow(laplacian, cmap='gray')
plt.title('Laplacian Edge Detection')
plt.axis('off')
plt.show()

# Canny Edge Detection
canny_edges = cv2.Canny(gray_image, 50, 150)

plt.imshow(canny_edges, cmap='gray')
plt.title('Canny Edge Detection')
plt.axis('off')
plt.show()
```

# Output:

<img width="320" height="430" alt="image" src="https://github.com/user-attachments/assets/c6dc7962-f4d1-4358-88a3-a4aab830ea35" />



<img width="312" height="436" alt="image" src="https://github.com/user-attachments/assets/d0ac09f6-c9e6-45b4-bc9c-963ebf9d858d" />



<img width="520" height="701" alt="image" src="https://github.com/user-attachments/assets/828087de-629e-4a97-ba02-ca468014dd19" />



<img width="317" height="435" alt="image" src="https://github.com/user-attachments/assets/7aaeb19d-a685-4f2a-9614-39575c2cbe56" />





# Result
Thus, edges are successfully detected using Sobel, Prewitt, Roberts, Laplacian, and Canny edge detection techniques. Each method highlights edges differently based on gradient and intensity variations, improving feature extraction and analysis.
