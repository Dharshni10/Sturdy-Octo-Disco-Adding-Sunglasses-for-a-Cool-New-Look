# Sturdy-Octo-Disco-Adding-Sunglasses-for-a-Cool-New-Look

Sturdy Octo Disco is a fun project that adds sunglasses to photos using image processing.

Welcome to Sturdy Octo Disco, a fun and creative project designed to overlay sunglasses on individual passport photos! This repository demonstrates how to use image processing techniques to create a playful transformation, making ordinary photos look extraordinary. Whether you're a beginner exploring computer vision or just looking for a quirky project to try, this is for you!

## Features:
- Detects the face in an image.
- Places a stylish sunglass overlay perfectly on the face.
- Works seamlessly with individual passport-size photos.
- Customizable for different sunglasses styles or photo types.

## Technologies Used:
- Python
- OpenCV for image processing
- Numpy for array manipulations

## How to Use:
1. Clone this repository.
2. Add your passport-sized photo to the `images` folder.
3. Run the script to see your "cool" transformation!

## Applications:
- Learning basic image processing techniques.
- Adding flair to your photos for fun.
- Practicing computer vision workflows.

## Program:
### Name : Dharshni V M
### Register Number : 212223240029
```
import cv2
import numpy as np
import matplotlib.pyplot as plt
faceImage = cv2.imread('photo.JPG')
plt.imshow(faceImage[:,:,::-1]);plt.title("Face")
faceImage.shape
glassPNG = cv2.imread('photog.png',-1)
plt.imshow(glassPNG[:,:,::-1]);plt.title("glassPNG")
glassPNG = cv2.resize(glassPNG,(310,150))
print("image Dimension ={}".format(glassPNG.shape))
glassBGR = glassPNG[:,:,0:3]
glassMask1 = glassPNG[:,:,3]
plt.figure(figsize=[10,10])
plt.subplot(121);plt.imshow(glassBGR[:,:,::-1]);plt.title('Sunglass Color channels');
plt.subplot(122);plt.imshow(glassMask1,cmap='gray');plt.title('Sunglass Alpha channel');
faceWithGlassesNaive = faceImage.copy()
faceWithGlassesNaive[310:460, 230:540]=glassBGR
plt.imshow(faceWithGlassesNaive[...,::-1])
glassMask = cv2.merge((glassMask1,glassMask1,glassMask1))
glassMask = np.uint8(glassMask/255)
faceWithGlassesArithmetic = faceImage.copy()
eyeROI= faceWithGlassesArithmetic[310:460, 230:540]
maskedEye = cv2.multiply(eyeROI,(1-  glassMask ))
maskedGlass = cv2.multiply(glassBGR,glassMask)
eyeRoiFinal = cv2.add(maskedEye, maskedGlass)
plt.figure(figsize=[10,10])
plt.subplot(131);plt.imshow(maskedEye[...,::-1]);plt.title("Masked Eye Region")
plt.subplot(132);plt.imshow(maskedGlass[...,::-1]);plt.title("Masked Sunglass Region")
plt.subplot(133);plt.imshow(eyeRoiFinal[...,::-1]);plt.title("Augmented Eye and Sunglass")
faceWithGlassesArithmetic[310:460, 230:540]=eyeRoiFinal
plt.figure(figsize=[20,20]);
plt.subplot(121);plt.imshow(faceImage[:,:,::-1]); plt.title("Original Image");
plt.subplot(122);plt.imshow(faceWithGlassesArithmetic[:,:,::-1]);plt.title("With Sunglasses");
```
## Output:
### Original Image
![original image](https://github.com/user-attachments/assets/7ab10c0c-8481-4f08-a983-12ae297b0ad8)

### Glass
![glass](https://github.com/user-attachments/assets/89094fa3-be4d-4fbc-9bc7-7f81e12c9087)

### Glass Color Channel
![glass color channel](https://github.com/user-attachments/assets/96df7867-61c9-4a7b-a066-87a3b365d4b7)

### Face With Glass
![face with glass](https://github.com/user-attachments/assets/ff9f8a0a-3e55-422a-8aab-df18997fac92)

### Eye And Glass Region
![eye and glass region](https://github.com/user-attachments/assets/359b0203-5ab4-4324-a6f5-4780f0ce9f66)

### Final Image With Glass
![final image with glass](https://github.com/user-attachments/assets/c39b05de-4851-4fa9-91da-fbd0c8379043)

## Result:
Thus, the creative project designed to overlay sunglasses on individual passport size photo has been successfully executed.

