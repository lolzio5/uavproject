# Project UAV

_Project last continued February 2022_

This project aimed to answer the research question "How can we make obstacle avoidance faster?", focusing on providing an autonomous, on-board obstacle detection and avoidance solution for small Unmanned Aerial Vehicles (UAVs).

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

In the last line of [detect.py](https://github.com/lolzio5/uavproject/blob/main/detect.py), the function get_angles() from the [plan.py](https://github.com/lolzio5/uavproject/blob/main/plan.py) file is called and prints the angle to follow for each frame.

This function outputs a bearing that the UAV could then follow to get around the obsctacle.

## Working Principle of the path planning algorithm

The path planning algorithm is provided a tuple of the coordinates of all the obstacles in each frame. 

The algorithm follows a number of steps:

---

1. Knowing that a forward facing angle of 0˚ means the UAV would continue straight on, the algorithm first calculates the angle to each obstacle from this 0˚, forward facing reference
2. Next, it determines whether there is sufficient space for the drone to pass through
    2.1. If all obstacles are at least ±10˚ from the forward direction with no obstacles, the UAV would continue forward
3. Should there be insufficient space, the algorithm finds the closest obstacle edge, and calculates the angle the drone should take to avoid the obstacle, while travelling in a straight line
4. If this is once again not possible to avoid, it checks the 2nd furthest obstacle
    4.1. This continues until a suitable amount of space has been found
5. This process is repeated for each frame, continuously adjusting the angle of travel of the drone (since the angle determined in the previous frame is now the forward facing 0˚ angle)

<br>

The advantage of this solution is the very low computational cost, as it is a very simple algorithm, perfect for on-board computing, and speedy, real time obstacle avoidance.

<br>

---

## Further work and improvement

The project can be further improved, by allowing the drone to avoid obstacles by flying higher or lower, which has not yet been implemented in the path planning algorithm. Moreover, the project must be extensively tested in a physical build. 

<br>

Preliminary research has been conducted on how to build a prototype. Data was collected to determine how to build a faster UAV, studying materials engineering and aerodynamics of quadcopters. This must, however, be put into action and fully tested at a scale.
