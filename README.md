# Project UAV

This project consisted of two parts. The first was rewarded at the Vienna International Science Fair 2021 with the Superior Ribbon (the highest distinction achievable), as well as the Best in Category Mathematics and Computer Science Award and the Best in Division (14 Year old and above) Award, making it the overall winner of the Vienna International Science Fair 2021.

<br>

The report with motivations, methodology and working principles for this part of the project can be seen in the file [Science Fair 2021 Project Report - Lolézio Viora-Marquet](https://github.com/lolzio5/uavproject/blob/main/Science%20Fair%202021%20Project%20Report%20-%20%20Lolézio%20Viora-Marquet.pdf).

<br>

The project was later extended to include a path planning algorithm, the description of the part of the project is therefore found below.



## Repository Organisation

<br>

- cfg
  - Contains all YOLOv3 config files to be used by the files to run the model
- detect.py
  - outputs bounding boxes on an input video file
- plan.py
  - returns the best angle for the drone based on the location of bounding boxes in its field of view 
 
## How to use

Run the [detect.py](https://github.com/lolzio5/uavproject/blob/main/detect.py) file to output the detection of obstacles on a video file, and print the angle the UAV must take

> To do this, change the path in the line
> ``` python
>  vidcap=cv2.VideoCapture("/Users/loleziov2022/Desktop/test_data/film4.MOV")
> ```
> to the path to your input video file (in mp4 or MOV format).

<br>

The output video in format .mp4 would then include the bounding box of the obstacles detected, with the confidence (1 being perfect confidence) of the detection.

> Note that the model is trained to detect trees, mostly Alpine spruce and pine trees. Other obstacles such as rocks, foliage and dirt can also be detected.
> The project primarily focuses on autonomous flight in the Austrian Alps.

<br>

In the last line of [detect.py](https://github.com/lolzio5/uavproject/blob/main/detect.py), the function get_angles() from the [plan.py](https://github.com/lolzio5/uavproject/blob/main/plan.py) file is called.

This function outputs a bearing that the UAV could then follow to get around the obsctacle

## Working Principle of the path planning algorithm


## Further work and improvement
