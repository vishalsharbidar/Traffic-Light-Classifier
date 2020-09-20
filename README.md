# Traffic-Light-Classifier
The aim of this project is to classify the Red Green and Yellow lights from given set of images

Project Overview

In this project,I have used knowledge of computer vision techniques to build a classifier for images of traffic lights! 
In the dataset of traffic light images, one of three lights is illuminated: red, yellow, or green.

## Classification Steps:
### 1. Loading and Visualizing the Traffic Light Dataset

This traffic light dataset consists of 1484 number of color images in 3 categories - red, yellow, and green. As with most human-sourced data, the data is not evenly distributed among the types. There are:
* 904 red traffic light images
* 536 green traffic light images
* 44 yellow traffic light images

### 2. Pre-processing. 

Each image has a particular label (Red, Yellow, Green) and all the images are of different sizes. The input images and output labels need to be standardized. That is, all the input should be of the same type of data and of the same size, and the output should be a numerical label. So all the images will be preprocessed to a defined shape of 32 x 32 px and assigned a one-hot encoded label. 

![preprocessing](/figure/Std_img.PNG)

### 3. Feature extraction

On analyzing the image data, I found that sharp changes in saturation could be seen around the traffic light. This makes sense, because the color of the light significantly changes the saturation around it. I developed an edge detection, which allowed me to visualize these changes. The problem was there was a lot of noise in the edge detection, and it was difficult to go from edges to a mask. I solved this by blurring the edges using another filter until the detected edges bled into each other. Areas with lots of edges in saturation now became bright spots after blurring edges. I used these bright spots to create a mask, which I applyed to value. Then I summed up value in the top, middle and bottom thirds. A bright top third indicates a red light, a bright middle indicates yellow, and a bright bottom indicates green

![FE](/figure/HSV.PNG)


![FE2](/figure/H_mask.PNG)

### 4. Classification and visualizing error
Here I have created a function to sort the missclassified images and saved it in MISCLASSIFIED. Missclassification can occur due to bad image quality, distorted images, etc

![Cla](/figure/Miss.PNG)

### 5. Evaluate your model
Classifier classified the images with an accuracy of 97.6% and never classify any red lights as green.
Both the goals have been achieved.
