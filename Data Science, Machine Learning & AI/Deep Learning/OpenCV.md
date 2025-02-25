# 📷 OpenCV Comprehensive Cheatsheet

## 🔹 Introduction
OpenCV (**Open Source Computer Vision Library**) is an open-source library for **image processing, computer vision, and machine learning**.

---

## 🔹 Installing OpenCV
```sh
# Install OpenCV using pip
pip install opencv-python opencv-python-headless

# Import OpenCV
import cv2
```

---

## 🔹 Reading & Displaying Images
```python
# Read an image
image = cv2.imread("image.jpg")

# Display the image
cv2.imshow("Image", image)
cv2.waitKey(0)
cv2.destroyAllWindows()
```

---

## 🔹 Resizing & Cropping Images
```python
# Resize image
resized = cv2.resize(image, (300, 300))

# Crop image
cropped = image[50:200, 50:200]
```

---

## 🔹 Converting Color Spaces
```python
# Convert to grayscale
gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)

# Convert to HSV
hsv = cv2.cvtColor(image, cv2.COLOR_BGR2HSV)
```

---

## 🔹 Drawing Shapes
```python
# Draw a rectangle
cv2.rectangle(image, (50, 50), (200, 200), (0, 255, 0), 2)

# Draw a circle
cv2.circle(image, (150, 150), 50, (255, 0, 0), -1)
```

---

## 🔹 Image Thresholding
```python
_, thresh = cv2.threshold(gray, 127, 255, cv2.THRESH_BINARY)
```

---

## 🔹 Edge Detection
```python
edges = cv2.Canny(image, 100, 200)
```

---

## 🔹 Contours Detection
```python
contours, _ = cv2.findContours(thresh, cv2.RETR_TREE, cv2.CHAIN_APPROX_SIMPLE)
cv2.drawContours(image, contours, -1, (0, 255, 0), 2)
```

---

## 🔹 Face Detection with Haar Cascades
```python
face_cascade = cv2.CascadeClassifier(cv2.data.haarcascades + "haarcascade_frontalface_default.xml")
gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)
faces = face_cascade.detectMultiScale(gray, 1.3, 5)
for (x, y, w, h) in faces:
    cv2.rectangle(image, (x, y), (x+w, y+h), (255, 0, 0), 2)
```

---

## 🔹 Video Capture
```python
cap = cv2.VideoCapture(0)
while True:
    ret, frame = cap.read()
    cv2.imshow("Webcam", frame)
    if cv2.waitKey(1) & 0xFF == ord('q'):
        break
cap.release()
cv2.destroyAllWindows()
```

---

## 🔹 Best Practices
- **Convert images to grayscale** for faster processing.
- **Use Gaussian blur** before edge detection for better results.
- **Tune parameters in thresholding & contour detection**.
- **Always release video capture & close windows** to avoid memory leaks.

---