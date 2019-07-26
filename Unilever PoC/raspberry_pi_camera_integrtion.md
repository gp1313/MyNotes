# Accessing the Raspberry Pi Camera with OpenCV and Python

**Source : [link1](https://www.pyimagesearch.com/2015/03/30/accessing-the-raspberry-pi-camera-with-opencv-and-python/) and [link2](https://www.pyimagesearch.com/2015/02/23/install-opencv-and-python-on-your-raspberry-pi-2-and-b/)**

## 1. Introduction
    

-   This tutorial explains how to integrate camera with raspberry pi using [picamera](https://picamera.readthedocs.io/en/release-1.9/) (pi camera) library.
    
-   Picamera is a python wrapper to camera module.
    
-   We will also study how to use picamera to get opencv format images.
    

  

## 2. System configuration
    

-   Connect the camera via bus to Raspberry Pi board.
    
-   Enable camera module using sudo raspi-config.
    
-   Sanity check for camera module using [raspistill](https://www.raspberrypi.org/documentation/usage/camera/raspicam/raspistill.md) (a command line tool)
    

  

## 3. Installing picamera
    

-   Install opencv on raspberry pi with python integration.
    
-   Activate your desired python virtual environment.
    
-   Install picamera[array] module using pip
    
-   “[array]” key word is very important, it enables the images we want to read in numpy array format so that later we can using opencv to perform image processing on them.
    

## 4. Code snippet

``` python
# import the necessary packages
from picamera.array import PiRGBArray
from picamera import PiCamera
import time
import cv2
 
# initialize the camera and grab a reference to the raw camera capture
camera = PiCamera()
rawCapture = PiRGBArray(camera)
 
# allow the camera to warmup
time.sleep(0.1)
 
# grab an image from the camera
camera.capture(rawCapture, format="bgr")
image = rawCapture.array
 
# display the image on screen and wait for a keypress
cv2.imshow("Image", image)
cv2.waitKey(0)
```





<!--stackedit_data:
eyJoaXN0b3J5IjpbMTQ0MDE3MTcsLTEyNjcyOTc0NTldfQ==
-->