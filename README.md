# Human-Detect
In this python project, we are going to build the Human Detection and Counting System through Webcam or you can give your own video or images.

To install the required library, run the following code in your terminal.

pip install opencv-python

pip install imutils

______________________________________
import cv2
import imutils
import argparse
______________________________________
To give video file as input:

python Human_Detector.py -v ‘Path_to_video’

2. To give image file as input:

python Human_Detector.py -i ‘Path_to-image’

3. To use the camera:

python Human_Detector.py -c True

4. To save the output:

Python Human_Detector.py -c True -o ‘file_name’
