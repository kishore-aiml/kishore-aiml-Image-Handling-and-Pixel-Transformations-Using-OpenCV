# Image-Handling-and-Pixel-Transformations-Using-OpenCV 

## AIM:
Write a Python program using OpenCV that performs the following tasks:

1) Read and Display an Image.  
2) Adjust the brightness of an image.  
3) Modify the image.  
4) Generate the modified image.

## Software Required:
- Anaconda - Python 3.7
- Jupyter Notebook (for interactive development and execution)


## Algorithm:

### Step 1:
Load an image from your local directory and display it.

### Step 2:
Create a matrix of ones (with data type float64) to adjust brightness.

### Step 3:
Create brighter and darker images by adding and subtracting the matrix from the original image.  
Display the original, brighter, and darker images.

### Step 4:
Modify the image contrast by creating two higher contrast images using scaling factors of 1.1 and 1.2 (without overflow fix).  
Display the original, lower contrast, and higher contrast images.

### Step 5:
Split the image into B, G, R components and display the channels

## Program Developed By:
- **Name:** KISHORE J
- **Register Number:** 212225240072

  ### Ex. No. 01

#### 1. Load an image from your local directory and display it.
```python
import cv2
import matplotlib.pyplot as plt

# Read the image using OpenCV
img = cv2.imread('Image Jul 18, 2026, 02_23_21 PM.png', cv2.IMREAD_COLOR)

# Convert BGR (OpenCV's default) to RGB (Matplotlib's expected color order)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

# Display the image using Matplotlib
plt.imshow(img_rgb, cmap='viridis')  # You can change 'viridis' to another cmap or use None for RGB images
plt.title("Original Image")
plt.axis('off')  # Removes axis ticks and labels
plt.show()
```

#### 2. Draw a line from the top-left to the bottom-right of the image.
```python

# Draw a line from top-left to bottom-right
line_img = cv2.line(img_rgb, (0, 0), (1536, 1024), (255,0 , 0), 3) # cv2.line(image, start_point, end_point, color, thickness)

plt.imshow(line_img, cmap='viridis')  
plt.title("Image with Line")
plt.axis('off')  
plt.show()
```

#### 3. Draw a circle at the center of the image..
```python

circle_img = cv2.circle(img_rgb,(700,300),150,(0,0,255),10) # cv2.circle(image, center, radius, color, thickness)

plt.imshow(circle_img, cmap='viridis')  
plt.title("Image with Circle")
plt.axis('off')  
plt.show()
```

#### 4. Draw a rectangle around  the whole image.
```python

# Draw a rectangle around the Whole image
rectangle_img = cv2.rectangle(img_rgb, (0, 0), (768, 600), (0, 255, 0), 10)  # cv2.rectangle(image, start_point, end_point, color, thickness)


plt.imshow(rectangle_img, cmap='viridis')  
plt.title("Image with Rectangle")
plt.axis('off')  
plt.show()

```

#### 5. Add the text "Your text" at the top-left corner of the image.
```python
# Add text to the image
text_img = cv2.putText(img_rgb, "OpenCV Drawing", (10, 30), cv2.FONT_HERSHEY_SIMPLEX, 1, (255, 255, 255), 10)  ## cv2.putText(image, text, position, font, font_scale, color, thickness)

plt.imshow(text_img, cmap='viridis')  
plt.title("Image with Text")
plt.axis('off')  
plt.show()
```

#### 6. onvert the image from RGB to HSV and display it..
```python
# Convert RGB to HSV
image_hsv = cv2.cvtColor(image_rgb, cv2.COLOR_RGB2HSV)

```

#### 7. Convert the image from RGB to GRAY and display it. .
```python
# Convert RGB to GRAY
image_gray = cv2.cvtColor(image_rgb, cv2.COLOR_RGB2GRAY)
```

#### 8. Convert the image from RGB to YCrCb and display it.
```python
# Convert RGB to YCrCb
image_ycrcb = cv2.cvtColor(image_rgb, cv2.COLOR_RGB2YCrCb)
```

#### 9. Convert the HSV image back to RGB and display it..
```python
# Convert HSV back to RGB
image_hsv_to_rgb = cv2.cvtColor(image_hsv, cv2.COLOR_HSV2RGB)
```

#### 10. Access and print the value of the pixel at coordinates (100, 100). 
```python
# Modify a block of pixels (300x300) to white, starting from (200, 200)
image[200:500, 200:500] = [255, 255, 255]  # Rows: 200-499, Columns: 200-499

# Convert BGR to RGB for displaying with Matplotlib
image_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)

# Display the modified image
plt.imshow(image_rgb)
plt.title("Image with 300x300 White Block")
plt.axis("off")
plt.show()
```

#### 11. Resize the original image to half its size and display it :
```python
# Resize the image to half its size
resized_image = cv2.resize(image, (768 // 2, 600 // 2))  # (new_width, new_height)

# Convert BGR to RGB for displaying with Matplotlib
resized_image_rgb = cv2.cvtColor(resized_image, cv2.COLOR_BGR2RGB)

resized_image_rgb.shape

# Display the resized image
plt.imshow(resized_image_rgb)
plt.title("Resized Image (Half Size)")
plt.axis("off")
plt.show()
```

#### 12. Crop a region of interest (ROI) from the image (e.g., a 100x100 pixel area starting at (50, 50)) and display it..
```python
# Crop a 300x300 region starting from (50, 50)
roi = image[50:350, 50:350]  # Rows: 50-349, Columns: 50-349

# Convert BGR to RGB for displaying with Matplotlib
roi_rgb = cv2.cvtColor(roi, cv2.COLOR_BGR2RGB)

# Display the cropped region (ROI)
plt.imshow(roi_rgb)
plt.title("Cropped Region of Interest (ROI)")
plt.axis("off")
plt.show()
```

#### 13. Flip the original image horizontally and vertically display it..
```python
# Flip the image horizontally (left-right)
flipped_horizontally = cv2.flip(image, 1)

# Convert BGR to RGB for displaying with Matplotlib
flipped_horizontally_rgb = cv2.cvtColor(flipped_horizontally, cv2.COLOR_BGR2RGB)

# Horizontal flip
plt.imshow(flipped_horizontally_rgb)
plt.title("Flipped Horizontally")
plt.axis("off")

# Flip the image vertically (up-down)
flipped_vertically = cv2.flip(image, 0)

# Convert BGR to RGB for displaying with Matplotlib
flipped_vertically_rgb = cv2.cvtColor(flipped_vertically, cv2.COLOR_BGR2RGB)

# Vertical flip
plt.imshow(flipped_vertically_rgb)
plt.title("Flipped Vertically")
plt.axis("off")

```
#### 14. Merged another image displays along with original image.
```python
# 1. Read your second image
overlay_img = cv2.imread('2.png', cv2.IMREAD_COLOR)

# 2. Resize the second image so it fits nicely
# Let's make it 150x150 pixels
h_overlay, w_overlay = 100, 150
overlay_resized = cv2.resize(overlay_img, (w_overlay, h_overlay))

# 3. Convert it to RGB (matching your Matplotlib workflow)
overlay_rgb = cv2.cvtColor(overlay_resized, cv2.COLOR_BGR2RGB)

# 4. Define where you want to place it (Top-left corner coordinates)
y_offset = 40
x_offset = 40

# 5. Insert the overlay image into the base image matrix
# This modifies 'img_rgb' in place
img_rgb[y_offset:y_offset+h_overlay, x_offset:x_offset+w_overlay] = overlay_rgb

# 6. Display as usual
plt.imshow(img_rgb)
plt.axis('off')
plt.show()
```

## Output:
- **i)** Original image
 <img ![alt text](image.png)/>

- **ii)** Image with line , circle,rectangle, text.
 <img ![alt text](image-1.png) />
 <img ![alt text](image-2.png) />
 <img ![alt text](image-3.png) />
 <img ![alt text](image-4.png)/>
 
- **iii)** Image - HSV , Grayscale , YCeCb and HSV to RGB . 
  <img ![alt text](image-5.png) />
  <img ![alt text](image-6.png) />
  <img ![alt text](image-7.png) />
  <img ![alt text](image-8.png) />
  
- **iv)** Image with block .
- 
  <img ![alt text](image-9.png) />

- **v)** Image - Resized Image (Half Size) ,  Cropped Region of Interest (ROI),Flipped Horizontally ,Flipped Vertically
  <img ![alt text](image-10.png) />
  <img ![alt text](image-11.png) />
  <img ![alt text](image-12.png) />
  <img ![alt text](image-13.png) />



- **vi)** Image with merged another image.
- 
  <img ![alt text](image-14.png) />

## Result:
Thus, the images were read, displayed, brightness and contrast adjustments were made, and bitwise operations were performed successfully using the Python program.