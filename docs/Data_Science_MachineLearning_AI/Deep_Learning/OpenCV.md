
# 📷 OpenCV Comprehensive Cheatsheet

## 🔹 Introduction
OpenCV (**Open Source Computer Vision Library**) is an open-source library for **image processing, computer vision, and machine learning**.

---

## 🔹 Installing OpenCV
```sh
pip install opencv-python opencv-python-headless
```
```python
import cv2
```

---

## 🔹 Reading & Displaying Images
```python
image = cv2.imread("image.jpg")
type(image)  # <class 'numpy.ndarray'>

cv2.imshow("Image", image)
cv2.waitKey(0)  # Waits indefinitely until a key is pressed
cv2.destroyAllWindows()
```

---

## 🔹 Display with Matplotlib
```python
import matplotlib.pyplot as plt

plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))
plt.axis('off')
plt.title("Image with Matplotlib")
plt.show()
```

---

## 🔹 Resizing, Cropping & Display Utility
```python
resized = cv2.resize(image, (300, 300))
cropped = image[50:200, 50:200]

def resize_display(img, scale=0.5):
    h, w = img.shape[:2]
    return cv2.resize(img, (int(w*scale), int(h*scale)))
```

---

## 🔹 Color Space Conversions
```python
gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)
hsv = cv2.cvtColor(image, cv2.COLOR_BGR2HSV)
lab = cv2.cvtColor(image, cv2.COLOR_BGR2LAB)
ycrcb = cv2.cvtColor(image, cv2.COLOR_BGR2YCrCb)
```

---

## 🔹 Blurring (Preprocessing)
```python
blurred = cv2.GaussianBlur(image, (5, 5), 0)
```

---

## 🔹 Drawing Shapes & Text
```python
cv2.rectangle(image, (50, 50), (200, 200), (0, 255, 0), 2)
cv2.circle(image, (150, 150), 50, (255, 0, 0), -1)
cv2.putText(image, "OpenCV!", (10, 30), cv2.FONT_HERSHEY_SIMPLEX, 1, (255, 255, 255), 2)
```

---

## 🔹 Thresholding
```python
_, thresh = cv2.threshold(gray, 127, 255, cv2.THRESH_BINARY)
binary_inv = cv2.threshold(gray, 127, 255, cv2.THRESH_BINARY_INV)[1]
adaptive = cv2.adaptiveThreshold(gray, 255, cv2.ADAPTIVE_THRESH_GAUSSIAN_C,
                                 cv2.THRESH_BINARY, 11, 2)
```

---

## 🔹 Edge Detection
```python
edges = cv2.Canny(image, 100, 200)
```

---

## 🔹 Contour Detection
```python
contours, _ = cv2.findContours(thresh, cv2.RETR_TREE, cv2.CHAIN_APPROX_SIMPLE)
cv2.drawContours(image, contours, -1, (0, 255, 0), 2)
```

---

## 🔹 Face Detection (Haar Cascades)
```python
face_cascade = cv2.CascadeClassifier(cv2.data.haarcascades + "haarcascade_frontalface_default.xml")
gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)
faces = face_cascade.detectMultiScale(gray, 1.3, 5)
for (x, y, w, h) in faces:
    cv2.rectangle(image, (x, y), (x+w, y+h), (255, 0, 0), 2)
    cv2.putText(image, "Face", (x, y-10), cv2.FONT_HERSHEY_SIMPLEX, 0.7, (255, 255, 0), 2)
cv2.putText(image, f"Faces: {len(faces)}", (10, 30), cv2.FONT_HERSHEY_SIMPLEX, 1, (0, 255, 255), 2)
```

---

## 🔹 Trackbar Example (for Threshold)
```python
def nothing(x):
    pass

cv2.namedWindow("Trackbar")
cv2.createTrackbar("Threshold", "Trackbar", 0, 255, nothing)

while True:
    t = cv2.getTrackbarPos("Threshold", "Trackbar")
    _, binary = cv2.threshold(gray, t, 255, cv2.THRESH_BINARY)
    cv2.imshow("Trackbar", binary)
    if cv2.waitKey(1) & 0xFF == ord('q'):
        break
cv2.destroyAllWindows()
```

---

## 🔹 Video Capture (with Save Option)
```python
cap = cv2.VideoCapture(0)
out = cv2.VideoWriter('output.avi', cv2.VideoWriter_fourcc(*'XVID'), 20.0, (640,480))

while True:
    ret, frame = cap.read()
    if not ret:
        break
    out.write(frame)
    cv2.imshow("Webcam", frame)
    if cv2.waitKey(1) & 0xFF == ord('q'):
        break

cap.release()
out.release()
cv2.destroyAllWindows()
```

---

## 🔹 Read Video File
```python
cap = cv2.VideoCapture("video.mp4")
```

---

## 🔹 Saving Images
```python
cv2.imwrite("output.jpg", image)
```

---

## 🔹 Best Practices
- ✅ Always convert to grayscale before thresholding or face detection.
- ✅ Use Gaussian blur to reduce noise before edge detection.
- ✅ Draw text and shapes using `cv2.putText`, `cv2.rectangle`, and `cv2.circle`.
- ✅ Use `cv2.imwrite()` to save output results.
- ✅ Always release `VideoCapture` objects and close windows with `cv2.destroyAllWindows()`.
- ✅ Use `cv2.resize()` for resizing and scaling display.
- ✅ Prefer `cv2.waitKey(n)` with proper timing for animation or video frame delay.
- ✅ Use `adaptiveThreshold` or `trackbars` for dynamic threshold tuning.

---

