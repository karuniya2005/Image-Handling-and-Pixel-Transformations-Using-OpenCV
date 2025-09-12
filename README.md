# Image-Handling-and-Pixel-Transformations-Using-OpenCV 

## AIM:
Write a Python program using OpenCV that performs the following tasks:

1) Read and Display an Image.  
2) Adjust the brightness of an image.  
3) Modify the image contrast.  
4) Generate a third image using bitwise operations.

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
Split the image (boy.jpg) into B, G, R components and display the channels

## Program Developed By:
- **Name:** Karuniya M
- **Register Number:**212223240068

  ### Ex. No. 01

#### 1. Read the image ('Eagle_in_Flight.jpg') using OpenCV imread() as a grayscale image.
```
import cv2
import matplotlib.pyplot as plt
import numpy as np
img_gray = cv2.imread("q1.png", cv2.IMREAD_GRAYSCALE)

```

#### 2. Print the image width, height & Channel.
```
print("Grayscale Image Shape:", img_gray.shape)
```

#### 3. Display the image using matplotlib imshow().
```
plt.imshow(img_gray, cmap='gray')
plt.title("Grayscale Image")
plt.axis("off")
plt.show()

```

#### 4. Save the image as a PNG file using OpenCV imwrite().
```
cv2.imwrite("q1_gray.png", img_gray)

```

#### 5. Read the saved image above as a color image using cv2.cvtColor().
```
img_color = cv2.imread("q1_gray.png")
img_color = cv2.cvtColor(img_color, cv2.COLOR_BGR2RGB)
```

#### 6. Display the Colour image using matplotlib imshow() & Print the image width, height & channel.
```
plt.imshow(img_color)
plt.title("Color Image (Reloaded)")
plt.axis("off")
plt.show()
print("Color Image Shape:", img_color.shape) 

```

#### 7. Crop the image to extract any specific (Eagle alone) object from the image.
```
roi = img_color[50:350, 100:400]  
plt.imshow(roi)
plt.title("Cropped ROI")
plt.axis("off")
plt.show()

```

#### 8. Resize the image up by a factor of 2x.
```
resized = cv2.resize(roi, None, fx=2, fy=2)
plt.imshow(resized)
plt.title("Resized ROI (2x)")
plt.axis("off")
plt.show()

```

#### 9. Flip the cropped/resized image horizontally.
```
flipped = cv2.flip(resized, 1)
plt.imshow(flipped)
plt.title("Flipped ROI (Horizontal)")
plt.axis("off")
plt.show()

```

#### 10. Read in the image ('Apollo-11-launch.jpg').
```
apollo = cv2.imread("q1.png")
apollo_rgb = cv2.cvtColor(apollo, cv2.COLOR_BGR2RGB)

```

#### 11. Add the following text to the dark area at the bottom of the image (centered on the image):
```
text = "Annotation Test on q1.png"
cv2.putText(apollo_rgb, text, (50, 50),
            cv2.FONT_HERSHEY_PLAIN, 2, (255, 255, 255), 2)
```

#### 12. Draw a magenta rectangle that encompasses the launch tower and the rocket.
```
cv2.rectangle(apollo_rgb, (30, 30), (300, 300), (255, 0, 255), 4)

```

#### 13. Display the final annotated image.
```
plt.imshow(apollo_rgb)
plt.title("Annotated Image (q1.png)")
plt.axis("off")
plt.show()


```

#### 14. Read the image ('Boy.jpg').
```
boy = cv2.imread("q1.png")
boy_rgb = cv2.cvtColor(boy, cv2.COLOR_BGR2RGB)

```

#### 15. Adjust the brightness of the image.
```
matrix = np.ones(boy_rgb.shape, dtype="uint8") * 50
brighter = cv2.add(boy_rgb, matrix)
darker = cv2.subtract(boy_rgb, matrix)

```

#### 16. Create brighter and darker images.
```
plt.subplot(1, 3, 1); plt.imshow(boy_rgb); plt.title("Original"); plt.axis("off")
plt.subplot(1, 3, 2); plt.imshow(darker); plt.title("Darker"); plt.axis("off")
plt.subplot(1, 3, 3); plt.imshow(brighter); plt.title("Brighter"); plt.axis("off")
plt.show()
```

#### 17. Modify the image contrast.
```
higher1 = cv2.convertScaleAbs(boy_rgb, alpha=1.1, beta=0)
higher2 = cv2.convertScaleAbs(boy_rgb, alpha=1.2, beta=0)
```

#### 18. Display the images (Original, Lower Contrast, Higher Contrast).
```
plt.subplot(1, 3, 1); plt.imshow(boy_rgb); plt.title("Original"); plt.axis("off")
plt.subplot(1, 3, 2); plt.imshow(higher1); plt.title("Contrast 1.1x"); plt.axis("off")
plt.subplot(1, 3, 3); plt.imshow(higher2); plt.title("Contrast 1.2x"); plt.axis("off")
plt.show()
```

#### 19. Split the image (boy.jpg) into the B,G,R components & Display the channels.
```
b, g, r = cv2.split(boy)
plt.subplot(1, 3, 1); plt.imshow(b, cmap="gray"); plt.title("Blue Channel"); plt.axis("off")
plt.subplot(1, 3, 2); plt.imshow(g, cmap="gray"); plt.title("Green Channel"); plt.axis("off")
plt.subplot(1, 3, 3); plt.imshow(r, cmap="gray"); plt.title("Red Channel"); plt.axis("off")
plt.show()

```

#### 20. Merged the R, G, B , displays along with the original image
```
merged_bgr = cv2.merge((b, g, r))
merged_rgb = cv2.cvtColor(merged_bgr, cv2.COLOR_BGR2RGB)
plt.imshow(merged_rgb)
plt.title("Merged RGB Image")
plt.axis("off")
plt.show()
```

#### 21. Split the image into the H, S, V components & Display the channels.
```
hsv = cv2.cvtColor(boy_rgb, cv2.COLOR_RGB2HSV)
h, s, v = cv2.split(hsv)
plt.subplot(1, 3, 1); plt.imshow(h, cmap="gray"); plt.title("Hue"); plt.axis("off")
plt.subplot(1, 3, 2); plt.imshow(s, cmap="gray"); plt.title("Saturation"); plt.axis("off")
plt.subplot(1, 3, 3); plt.imshow(v, cmap="gray"); plt.title("Value"); plt.axis("off")
plt.show()

```
#### 22. Merged the H, S, V, displays along with original image.
```
merged_hsv = cv2.merge((h, s, v))
back_rgb = cv2.cvtColor(merged_hsv, cv2.COLOR_HSV2RGB)
plt.imshow(back_rgb)
plt.title("Merged HSV → RGB")
plt.axis("off")
plt.show()

```

## Output:
- **i)** Read and Display an Image.
  
  <img width="346" height="461" alt="image" src="https://github.com/user-attachments/assets/c0a0457e-15d5-4efc-ad67-13c323ded636" />

- **ii)** Adjust Image Brightness.

<img width="602" height="278" alt="image" src="https://github.com/user-attachments/assets/230f04d9-81c4-4652-b72f-f05c2c1980aa" />

- **iii)** Modify Image Contrast.

  <img width="561" height="249" alt="image" src="https://github.com/user-attachments/assets/a9c556f3-1295-488c-86d3-5ec82bbc8522" />

- **iv)** Generate Third Image Using Bitwise Operations.

 <img width="616" height="265" alt="image" src="https://github.com/user-attachments/assets/59205138-bc17-480c-825c-afebcc9a6c41" />

  
  <img width="357" height="457" alt="image" src="https://github.com/user-attachments/assets/a2df19eb-1aba-4e37-a737-55bdcf115067" />

 
  <img width="609" height="263" alt="image" src="https://github.com/user-attachments/assets/b9b0a087-9e58-48f4-9c09-a630bb4c4f3a" />
  

  <img width="393" height="467" alt="image" src="https://github.com/user-attachments/assets/edb4ac51-cc89-412e-bc50-6f5b64188899" />




## Result:
Thus, the images were read, displayed, brightness and contrast adjustments were made, and bitwise operations were performed successfully using the Python program.

