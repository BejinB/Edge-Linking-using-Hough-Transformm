# Edge-Linking-using-Hough-Transformm
## Aim:
To write a Python program to detect the lines using Hough Transform.

## Software Required:
Anaconda - Python 3.7

## Algorithm:
### Step1:

Import all the necessary modules for the program.
### Step2:

Load a image using imread() from cv2 module.
### Step3:

Convert the image to grayscale.
### Step4:

Using Canny operator from cv2,detect the edges of the image.
### Step5:

Using the HoughLinesP(),detect line co-ordinates for every points in the images.Using For loop,draw the lines on the found co-ordinates.Display the image.

## Program:
### Developed by: BEJIN.B
### Reg no: 21222223021
```python
import cv2
import numpy as np
import matplotlib.pyplot as plt
```

### Input image and grayscale image
```python
image = cv2.imread('img4.jpeg')  
gray_image = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)
plt.subplot(2, 2, 1)
plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))
plt.title('Input Image')
plt.axis('off')

```
![image](https://github.com/user-attachments/assets/bc150524-189f-455d-80c4-af2884780be8)
```python
plt.subplot(2, 2, 2)
plt.imshow(gray_image, cmap='gray')
plt.title('Grayscale Image')
plt.axis('off')

```


![image](https://github.com/user-attachments/assets/62c64593-3d5a-42dd-9582-23ea36a59c5a)



### Canny Edge detector 
```python
edges = cv2.Canny(gray_image, 50, 150, apertureSize=3)

plt.subplot(2, 2, 3)
plt.imshow(edges, cmap='gray')
plt.title('Canny Edge Detector Output')
plt.axis('off')
```
![image](https://github.com/user-attachments/assets/f2001faf-58e6-4eeb-8a21-b5d0b841a466)



### Detect lines using the probabilistic Hough transform
```python

lines = cv2.HoughLinesP(edges, rho=1, theta=np.pi/180, threshold=100, minLineLength=50, maxLineGap=10)
```
### Draw the lines on the original image
```python
output_image = image.copy()

if lines is not None:
    for line in lines:
        x1, y1, x2, y2 = line[0]
        cv2.line(output_image, (x1, y1), (x2, y2), (0, 255, 0), 2)
```

### Hough Transform Result
```python
plt.subplot(2, 2, 4)
plt.imshow(cv2.cvtColor(output_image, cv2.COLOR_BGR2RGB))
plt.title('Hough Transform - Line Detection')
plt.axis('off')
```
![image](https://github.com/user-attachments/assets/a87b445c-e7c0-4815-84e2-078e0e9b4b60)


## Result:
Thus, the program to detect the lines using Hough Transform implemented successfully.

