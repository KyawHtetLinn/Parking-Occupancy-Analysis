# Parking-Occupancy-Analysis
#### Vehicle counting and occupancy for each parking zone in video

## Overview

&emsp;&emsp;This project utilizes YOLOv7 to analyze parking occupancy from youtube video footage. The objective is to automatically detect and count the number of occupied cars for each ploygon zone from video, providing valuable insights for parking management systems.
&emsp;&emsp;Using occupancy analytics, you can identify peak hours and trends, allowing you to make informed plans and adjustments for future operations

<hr/>

At first,the youtube video is transformed into frames in order to be detected each frame.For detection the car in each zone,we will use the [Kaggle dataset](https://www.kaggle.com/datasets/braunge/aerial-view-car-detection-for-yolov5) and train with the yoloV7 model.For defining the zones, there is a Supervision’s [PolygonZone](https://supervision.roboflow.com/detection/tools/polygon_zone/?ref=blog.roboflow.com#polygonzone) feature, which we will use to detect the vehicles in each zone of the parking lot, requires a set of points in order to identify where the zone is located, which can be generated using [this online utility](https://supervision.roboflow.com/detection/tools/polygon_zone/?ref=blog.roboflow.com#polygonzone).

## How it work

1. **Training with YOLOv5** : 
2. **video to frames** :
3. 

## Resources

- [original walmart parking video](https://youtu.be/hBLC718adwg?si=vHdTgq4_wZAG-bdv)
- [roboflow Occupancy Analytics](https://blog.roboflow.com/occupancy-analytics/#total-occupancy)
- [Polygon Zone](https://supervision.roboflow.com/detection/tools/polygon_zone/?ref=blog.roboflow.com#polygonzone)
