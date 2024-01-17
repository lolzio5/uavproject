# Project UAV

This project consisted of two parts. The first was rewarded at the Vienna International Science Fair 2021 with the Superior Ribbon (the highest distinction achievable), as well as the Best in Category Mathematics and Computer Science Award and the Best in Division (14 Year old and above) Award, making it the overall winner of the Vienna International Science Fair 2021.

The report for this part of the project can be seen in the file [Science Fair 2021 Project Report - Lolézio Viora-Marquet](Science Fair 2021 Project Report - Lolézio Viora-Marquet).

The project was later extended to include a path planning algorithm, the description of the part of the project is therefore found below.

## Abstract

Fast flying drones able to autonomously travel, while avoiding obstacles, can have many applications in industry. Numerous methods have been developed to tackle this problem, using a wide range of sensors, but I present a stereo-based approach, using a convolutional neural network to detect natural obstacles, in real-time, for fast and accurate obstacle detection. The model was tested on a test dataset representative of a coniferous forest environment, and outputted a mAP of 0.1209, indicating that it currently has a low success rate, however, that the approach could function with more training and a larger training dataset. My approach to obstacle detection is a valid solution to the problem, however, it needs to be significantly improved in order to be considered a reliable method for its real-world applications.

### 
This project uses Yolov3-tiny to detect obstacles on images using the detect.py file. It is currently trained for a forest environment with numerous trees. This can be seen on the demonstration1.mp4 file. 

The plan.py file is then able to plan the most efficient path around an obstacle, and prints it out. 

This project is still a work in progress, having to use the output of the plan.py file to control a real drone. 
