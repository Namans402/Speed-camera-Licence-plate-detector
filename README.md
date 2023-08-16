# Speed-camera-Licence-plate-detector
# Speed Camera License Plate Identifier

#### Project Goal

The goal of this project was to clean up an image of a speeding car, so we can read the license plate on the car.

#### Data Source

The data png file is in this github folder. It's a grayscale image of a car with a sort of dotty filter, in essence with a lot of noise.<br >
<br >
![image](https://github.com/JaideepPrasad/Data-Science/blob/main/Image%20Processing/Image%20Processing%20Forensics/car.png?raw=true)<br >

#### Files

There are 3 files here, a .ipynb jupyter notebook that has the code, a folder with 3 images from my code, and a .png image file.

#### Overview

  - use fourier transform to get magnitude spectrum
  - block out the noise from magnitude spectrum
  - inverse fourier transform to compare current image with input image
  - change contrast 
  - sharpen image

#### Result

After all the image processing steps, we get an image clear enough to learn a few things:
  - The license plate looks like "BHT 01Z". It's fair to say the license plate looks pretty legible.
  - We can also say the make of the car is Mazda and the model is a Miata.

#### Conclusion

Using the fourier transform on the input image, we can tell the image has a lot of noise. 
The white light/star thing in the magnitude graph shows us which frequency component contributes to the noise.<br >

![image](https://github.com/JaideepPrasad/Data-Science/blob/main/Image%20Processing/Image%20Processing%20Forensics/images/Capture.PNG?raw=true)<br >

We want to get rid of all the white stars other than the center one. You can image the magnitude graph as a graph with 2 perpendicular axes going through the middle of the graph.
We want to save the center star as that is the DC component of our image. Filtering out the stars results in our new magnitude graph.<br >

![image](https://github.com/JaideepPrasad/Data-Science/blob/main/Image%20Processing/Image%20Processing%20Forensics/images/Capture1.PNG?raw=true)<br >

At this point we dealt with the noise in the image, so we do an inverse fourier transform to get back to the real domain. Our current image looks faded so we will play with the contrast. We try gamma and log exposure functions to darken the image and find out that log was not helpful, but gamma was.
  - left image: current image
  - middle image: gamma correction
  - right image: log correction
<br >

![image](https://github.com/JaideepPrasad/Data-Science/blob/main/Image%20Processing/Image%20Processing%20Forensics/images/Capture2.PNG?raw=true)<br >

We normalize the image and try to apply a smoothing filter, but the quality of the image doesn't get better. From all the above steps (minus the smoothing filter), we cleaned the image well enough to read the license plate. 
