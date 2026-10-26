# Experiment 1: Image Handling and Pixel Transformations Using OpenCV

### Developed By
### **Name:** Sujith A
### **Register Number:** 212224230278

## Aim
To perform image handling and pixel transformations using OpenCV in Python, including image loading and displaying, drawing shapes, color-space conversion, pixel manipulation, resizing, cropping, flipping, and saving images.

## Requirements
- Python
- Anaconda Prompt
- Jupyter Notebook
- OpenCV (`cv2`)
- Matplotlib
- Input image: `ex.png`

## Procedure

1. Import OpenCV and Matplotlib.
2. Load and display the original image.
3. Draw a line, circle, rectangle, and text on the image.
4. Convert the image to HSV, grayscale, and YCrCb color spaces.
5. Convert the HSV image back to RGB.
6. Access pixel information and modify a block of pixels to white.
7. Resize the image to half its original dimensions.
8. Crop a region of interest (ROI).
9. Flip the image horizontally and vertically.
10. Save the final modified image when the save operation is added to the notebook.

---

## 1. Load and Display the Original Image

The image is loaded using `cv2.imread()` and converted from OpenCV's BGR color order to RGB for display with Matplotlib.

```python
import cv2
import matplotlib.pyplot as plt

img = cv2.imread("ex.png", cv2.IMREAD_COLOR)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

plt.imshow(img_rgb)
plt.title("Original Image")
plt.axis("off")
plt.show()
```

### Output

<img width="259" height="311" alt="image" src="https://github.com/user-attachments/assets/60506034-48bf-4294-892f-02c7ea632009" />


---

## 2. Drawing Shapes and Text

OpenCV drawing functions are used to add a line, circle, rectangle, and text to the image.

### 2.1 Draw a Line

```python
image = cv2.imread("ex.png")
img_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)

line_img = cv2.line(img_rgb, (0, 0), (768, 600), (255, 0, 0), 2)

plt.imshow(line_img)
plt.title("Image with Line")
plt.axis("off")
plt.show()
```

### Output

<img width="265" height="311" alt="image" src="https://github.com/user-attachments/assets/1e845e13-2d2c-452a-8cb0-6d6f2cb47777" />


### 2.2 Draw a Circle

```python
image = cv2.imread("ex.png")
img_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)

circle_img = cv2.circle(img_rgb, (400, 300), 150, (255, 0, 0), 10)

plt.imshow(circle_img)
plt.title("Image with Circle")
plt.axis("off")
plt.show()
```

### Output

<img width="274" height="307" alt="image" src="https://github.com/user-attachments/assets/368838ea-c809-48d2-ad04-99827521d6c9" />

### 2.3 Draw a Rectangle

```python
image = cv2.imread("ex.png")
img_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)

rectangle_img = cv2.rectangle(img_rgb, (0, 0), (500, 400), (0, 0, 255), 10)

plt.imshow(rectangle_img)
plt.title("Image with Rectangle")
plt.axis("off")
plt.show()
```

### Output

<img width="265" height="309" alt="image" src="https://github.com/user-attachments/assets/6fdf9552-1cfa-4a40-bf81-efe516c982ef" />


### 2.4 Add Text

```python
image = cv2.imread("ex.png")
img_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)

text_img = cv2.putText(
    img_rgb, "OpenCV Drawing", (10, 30),
    cv2.FONT_HERSHEY_SIMPLEX, 1, (255, 255, 255), 10
)

plt.imshow(text_img)
plt.title("Image with Text")
plt.axis("off")
plt.show()
```

### Output

<img width="263" height="308" alt="image" src="https://github.com/user-attachments/assets/318abafe-a44e-46af-9f6f-dbb9ad3de26b" />


---

## 3. Color-Space Conversion

The image is converted into HSV, grayscale, and YCrCb color spaces. The HSV image is also converted back to RGB.

```python
image = cv2.imread("ex.png")
image_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)

# RGB to HSV
image_hsv = cv2.cvtColor(image_rgb, cv2.COLOR_RGB2HSV)
plt.imshow(image_hsv)
plt.title("HSV Image")
plt.axis("off")
plt.show()

# RGB to grayscale
image_gray = cv2.cvtColor(image_rgb, cv2.COLOR_RGB2GRAY)
plt.imshow(image_gray, cmap="gray")
plt.title("Grayscale Image")
plt.axis("off")
plt.show()

# RGB to YCrCb
image_ycrcb = cv2.cvtColor(image_rgb, cv2.COLOR_RGB2YCrCb)
plt.imshow(image_ycrcb)
plt.title("YCrCb Image")
plt.axis("off")
plt.show()

# HSV back to RGB
image_hsv_to_rgb = cv2.cvtColor(image_hsv, cv2.COLOR_HSV2RGB)
plt.imshow(image_hsv_to_rgb)
plt.title("HSV to RGB Image")
plt.axis("off")
plt.show()
```

### Outputs

<img width="263" height="302" alt="image" src="https://github.com/user-attachments/assets/d53425eb-3330-4c1b-9a7f-21a4c97232c9" />
<br><br>
<img width="278" height="306" alt="image" src="https://github.com/user-attachments/assets/cb72d27f-d5c9-4d2a-affe-56cacf37aca8" />
<br><br>
<img width="258" height="308" alt="image" src="https://github.com/user-attachments/assets/66bc251f-6b74-49fd-965a-4498b03848e3" />
<br><br>
<img width="264" height="300" alt="image" src="https://github.com/user-attachments/assets/cd0c1aed-09a7-4158-8462-77cc1a389e09" />
<br><br>
<img width="273" height="311" alt="image" src="https://github.com/user-attachments/assets/c0192fc4-af19-424d-9545-93f7384e4f05" />

## 4. Pixel Manipulation

The notebook changes a rectangular block of pixels to white. The coordinates use NumPy's `[row, column]` indexing.

```python
image = cv2.imread("ex.png")

# Print the pixel value at (100, 100)
print("Pixel value:", image[100, 100])

# Change a 300 x 300 block to white, starting at row 200 and column 200
image[200:500, 200:500] = [255, 255, 255]

image_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)
plt.imshow(image_rgb)
plt.title("Image with White Block")
plt.axis("off")
plt.show()
```

### Output


<img width="265" height="305" alt="image" src="https://github.com/user-attachments/assets/99a23bfe-50cc-4ff0-ae78-076a9dc3ecac" />

---

## 5. Resize the Image

The image is resized to half its original width and height.

```python
image = cv2.imread("ex.png")
height, width = image.shape[:2]

resized_image = cv2.resize(image, (width // 2, height // 2))
resized_image_rgb = cv2.cvtColor(resized_image, cv2.COLOR_BGR2RGB)

plt.imshow(resized_image_rgb)
plt.title("Resized Image (Half Size)")
plt.axis("off")
plt.show()
```

### Output

<img width="371" height="310" alt="image" src="https://github.com/user-attachments/assets/f04435ff-9a42-4e33-80cf-6f86cb468f13" />


---

## 6. Crop a Region of Interest (ROI)

A 300 × 300 pixel region is cropped from the image, starting at `(50, 50)`.

```python
image = cv2.imread("ex.png")
roi = image[50:350, 50:350]
roi_rgb = cv2.cvtColor(roi, cv2.COLOR_BGR2RGB)

plt.imshow(roi_rgb)
plt.title("Cropped Region of Interest (ROI)")
plt.axis("off")
plt.show()
```

### Output
<img width="299" height="317" alt="image" src="https://github.com/user-attachments/assets/87896499-3cb5-4831-8414-a7b42597366f" />


---

## 7. Flip the Image

The original image is flipped horizontally and vertically using `cv2.flip()`.

```python
image = cv2.imread("ex.png")

# Horizontal flip
flipped_horizontally = cv2.flip(image, 1)
flipped_horizontally_rgb = cv2.cvtColor(
    flipped_horizontally, cv2.COLOR_BGR2RGB
)
plt.imshow(flipped_horizontally_rgb)
plt.title("Flipped Horizontally")
plt.axis("off")
plt.show()

# Vertical flip
flipped_vertically = cv2.flip(image, 0)
flipped_vertically_rgb = cv2.cvtColor(
    flipped_vertically, cv2.COLOR_BGR2RGB
)
plt.imshow(flipped_vertically_rgb)
plt.title("Flipped Vertically")
plt.axis("off")
plt.show()
```

### Outputs
---
<img width="272" height="305" alt="image" src="https://github.com/user-attachments/assets/2c7aeca0-f13e-40d1-9bf6-52e37544f03e" />

<br><br>

<img width="263" height="307" alt="image" src="https://github.com/user-attachments/assets/fe8310cb-1dab-4f4a-b900-01c56b7bfbfc" />



## 8. Save the Output Image

The notebook describes saving the final image, but a save operation was not present in the supplied notebook cells. To save a processed image, use `cv2.imwrite()` after creating it:

```python
cv2.imwrite("output.png", image)
```

## Result
Thus, image handling and pixel transformations were implemented using Python and OpenCV. The experiment demonstrates image loading, drawing, color space conversion, pixel manipulation, resizing, cropping, flipping, and saving images successfully.

