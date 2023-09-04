# Blur Detection

NOTEBOOK: [Blur Detection.ipynb](https://colab.research.google.com/drive/1PKNfRPT8aeP3uM4bCwAQMCRwgrH-maZa?usp=drive_link)

DATASET: [Blurring](https://drive.google.com/drive/folders/1qsZnHFWoTdefVivIgwiJuZFAAMYohnsQ?usp=drive_link)

## OBJECTIVES 
To develop, test, and evaluate a robust Blur Detection System that accurately identifies and classifies blurred and clear images, ensuring the system meets performance and quality criteria. This ETP aims to:
Develop a Functional Blur Detection System: Create a system capable of detecting and classifying different levels and types of image blur, contributing to improved image quality analysis.
Evaluate System Accuracy: Rigorously test and validate the system's accuracy in detecting blur, ensuring that it consistently provides reliable results under varying conditions with the optimal speed.

#### SCOPE
The blur detection is done on the videos recorded and uploaded to the C3V2 platform. It goes through every frame of the video and calculates an average score. Which then if is above a certain threshold is considered not blur and if it is under the threshold it is considered a blur video hence not usable for further processing.


#### TEST PLAN
The blur score in this code is being calculated using the Laplacian variance method, specifically by measuring the variance of the Laplacian of each frame. Here's how the blur score calculation works:

#### 1. _Laplacian Transformation:_

The Laplacian operator is applied to the grayscale version of each frame. The Laplacian is a mathematical operator that calculates the second spatial derivative of an image. In simple terms, it measures the rate of change of pixel values, which correlates with the image's sharpness.

#### 2. _Variance Calculation:_

After applying the Laplacian operator to the frame, the code calculates the variance of the resulting Laplacian image. Variance measures the spread or dispersion of pixel values in an image. In the context of blur detection, a higher variance indicates that pixel values are changing rapidly, which is a characteristic of sharper images. Conversely, a lower variance suggests smoother, blurred regions.

#### 3. _Visualizing the Blur Score:_

To visualize the blur score on each frame, the code draws a red rectangle on the frame. The width of the rectangle is determined by multiplying the variance value (fm) by a constant factor (1.6). This allows you to see, at a glance, which parts of the image are more or less blurry based on the length of the red bar. The longer the bar, the less blurry that part of the image is perceived to be.

##### 4. _Average Blur Score:_

After processing all frames, the code calculates the average blur score (avg) by summing up all the individual blur scores and dividing by the total number of frames. This average score provides an overall measure of the video's bluriness.

## KEY RESULTS
After running the code through multiple videos, you can categorise the following blur scores in the following categories:

fm < 120 -> no information is retrievable from the image whatsoever, i.e. completely blur.

![image](https://github.com/Erkesto/Nayan_internship/assets/62474995/92fd3c0c-4fcd-4db5-9776-705c18cb0ae4)

fm > 120 && fm < 640 -> somewhat information can be retrieved form the image, but the whole image is still not completely clear.

![image](https://github.com/Erkesto/Nayan_internship/assets/62474995/3f0ad005-196b-456d-9907-9ce15ec54815)

fm > 640 -> The image has enough information and is considered not blur.

![image](https://github.com/Erkesto/Nayan_internship/assets/62474995/ecb49fa6-6e7c-4fa5-97e4-a836e03aa18d)

*fm score = Blur Score
*exceptions can occur.
0 is whites in the image that is blur/ blur images and 1> is sharp images with defined borders that is not blur 
