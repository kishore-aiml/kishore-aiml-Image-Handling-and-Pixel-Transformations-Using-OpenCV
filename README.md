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
- **Name:** A PRAVEEN KISHORE 
- **Register Number:** 212225220074

  ### Ex. No. 01

#### 1. Load an image from your local directory and display it.
```python
import cv2
import matplotlib.pyplot as plt

# Read the image using OpenCV
img = cv2.imread('Qno. 1.jpg', cv2.IMREAD_COLOR)

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
line_img = cv2.line(img_rgb, (0, 0), (768, 600), (0, 255, 0), 2) # cv2.line(image, start_point, end_point, color, thickness)

plt.imshow(line_img, cmap='viridis')  
plt.title("Image with Line")
plt.axis('off')  
plt.show()
```

#### 3. Draw a circle at the center of the image..
```python

circle_img = cv2.circle(img_rgb,(200,200),150,(255,25,0),10) # cv2.circle(image, center, radius, color, thickness)

plt.imshow(circle_img, cmap='viridis')  
plt.title("Image with Circle")
plt.axis('off')  
plt.show()
```

#### 4. Draw a rectangle around  the whole image.
```python

# Draw a rectangle around the Whole image
rectangle_img = cv2.rectangle(img_rgb, (0, 0), (800, 500), (0, 145, 255), 10)  # cv2.rectangle(image, start_point, end_point, color, thickness)

plt.imshow(rectangle_img, cmap='viridis')  
plt.title("Image with Rectangle")
plt.axis('off')  
plt.show()

```

#### 5. Add the text "Your text" at the top-left corner of the image.
```python
# Add text to the image
text_img = cv2.putText(img_rgb, "ambassador", (10, 30), cv2.FONT_HERSHEY_SIMPLEX, 1, (0, 255, 0), 10)  ## cv2.putText(image, text, position, font, font_scale, color, thickness)

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
 <img width="648" height="455" alt="image" src="https://github.com/user-attachments/assets/d3c86230-2ba2-44b6-8858-175ba49b45a2" />

- **ii)** Image with line , circle,rectangle, text.
 <img width="642" height="461" alt="image" src="https://github.com/user-attachments/assets/bdc890c6-25b3-435b-931b-b08bd3fb5b6f" />
 <img width="650" height="457" alt="image" src="https://github.com/user-attachments/assets/edb74f22-2771-41d2-a3c6-33c67cf475f3" />
 <img width="645" height="453" alt="image" src="https://github.com/user-attachments/assets/372d6abf-f880-4aa3-9f88-8565ee380c4a" />
 <img width="638" height="468" alt="image" src="https://github.com/user-attachments/assets/e1307db6-7e1d-40e3-8506-07ae976cda5e" />
 
- **iii)** Image - HSV , Grayscale , YCeCb and HSV to RGB . 
  <img width="650" height="455" alt="image" src="https://github.com/user-attachments/assets/37cf27ff-b58d-469d-8b38-914ae832547d" />
  <img width="661" height="447" alt="image" src="https://github.com/user-attachments/assets/39999e64-0ffa-4f91-8a35-5208f4840854" />
  <img width="635" height="460" alt="image" src="https://github.com/user-attachments/assets/479cc8ba-ee6b-4d8a-88ee-b55fbd76bb30" />
  <img width="672" height="445" alt="image" src="https://github.com/user-attachments/assets/c7ff2123-7652-4f5f-afc3-3c68b9799764" />
  
- **iv)** Image with block .
- 
  <img width="696" height="466" alt="image" src="https://github.com/user-attachments/assets/423b158e-e6db-4a00-a7f6-7f26de4252a4" />

- **v)** Image - Resized Image (Half Size) ,  Cropped Region of Interest (ROI),Flipped Horizontally ,Flipped Vertically
  <img width="632" height="507" alt="image" src="https://github.com/user-attachments/assets/d368ef4c-58c7-4be9-9a3e-80720683b822" />
  <img width="488" height="505" alt="image" src="https://github.com/user-attachments/assets/5054d9cc-878f-4764-a770-a278037e533c" />
  <img width="628" height="465" alt="image" src="https://github.com/user-attachments/assets/d189a215-7af0-4a41-9f6a-978ef56d56d3" />
  <img width="635" height="460" alt="image" src="https://github.com/user-attachments/assets/e9c8fc9b-639a-487f-8cac-375132aff855" />



- **vi)** Image with merged another image.
- 
  <img width="642" height="450" alt="image" src="https://github.com/user-attachments/assets/584bdeaf-9839-4acc-a0c5-0df5263b59ec" />

## Result:
Thus, the images were read, displayed, brightness and contrast adjustments were made, and bitwise operations were performed successfully using the Python program.
