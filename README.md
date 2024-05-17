# Parking-Occupancy-Analysis
#### Vehicle counting and data analysis of occupancies for each parking zone in video

## Overview

&emsp;&emsp;This project utilizes YOLOv7 to analyze parking occupancy from youtube video footage. The objective is to automatically detect and count the number of occupied cars for each ploygon zone from video, providing valuable insights for parking management systems.<br/>
&emsp;&emsp;Using occupancy analytics, you can identify peak hours and trends, allowing you to make informed plans and adjustments for future operations

<hr/>

&emsp;At first,the youtube video is transformed into frames in order to be detected each frame.For detection the car in each zone,we will use the [Kaggle dataset](https://www.kaggle.com/datasets/braunge/aerial-view-car-detection-for-yolov5) and train with the yoloV7 model. 
<br/>
&emsp;For defining the zones, there is a Supervision’s [PolygonZone](https://supervision.roboflow.com/detection/tools/polygon_zone/?ref=blog.roboflow.com#polygonzone) feature, which we will use to detect the vehicles in each zone of the parking lot, requires a set of points in order to identify where the zone is located, which can be generated using [this online utility](https://supervision.roboflow.com/detection/tools/polygon_zone/?ref=blog.roboflow.com#polygonzone).


```
# Polygons From PolygonZone

zones = [
    {
        'name': "Zone 1",
        'polygon': np.array([[4, 90],[130, 90],[130, 675],[6, 675]]),
        'max': 38
    },
    {
        'name': 'Zone 2',
        'polygon': np.array([[200, 70],[320, 70],[320, 675],[200, 675]]),
        'max': 38
    },
    {
        'name': 'Zone 3',
        'polygon': np.array([[395, 50],[530, 50],[530, 675],[395, 675]]),
        'max': 35
    },
    {
        'name': 'Zone 4',
        'polygon': np.array([[600, 50],[725, 50],[725, 675],[600, 675]]),
        'max': 37
    },
    {
        'name': 'Zone 5',
        'polygon': np.array([[800, 43],[925, 43],[925, 675],[800, 675]]),
        'max': 40
    }
]
```
&emsp;&emsp;After defining the zones in video,we will use the following features of SuperVision : 
  - *ByteTrack*: To track the location of our vehicles, so we can assess how long they are parked
  - *InferenceSlicer*: A helper utility to run SAHI on our model
  - *TriangleAnnotator*: To help visualize the locations of the vehicles
  - *HeatMapAnnotator*: To generate heatmaps so we can identify our busiest areas
  - *PolygonZone*, *PolygonZoneAnnotator*: To help count and identify vehicles in our respective zones and the annotator to help visualize those zones.
<br /><br />
![testImage](https://github.com/KyawHtetLinn/Parking-Occupancy-Analysis/assets/70162137/9ded4b65-663f-4f16-82b6-61065e6e95fa)

> YoloV7 training , we can see [the training notebook]()<br/>
> Occupancy Analysis , we can see [the inference notebook]()

## Occupancy per zone and for all zones
```
Zone 1 had an average occupancy of 47% with a median occupancy of 47%.
Zone 2 had an average occupancy of 69% with a median occupancy of 71%.
Zone 3 had an average occupancy of 88% with a median occupancy of 89%.
Zone 4 had an average occupancy of 72% with a median occupancy of 73%.
Zone 5 had an average occupancy of 48% with a median occupancy of 48%.

The total zones in video had an average occupancy of 65% with a median occupancy of 65%.
```
## Graph 

https://github.com/KyawHtetLinn/Parking-Occupancy-Analysis/assets/70162137/521f0bcd-c06b-4404-8d4b-d59f249f44c0



## Resources

- [original walmart parking video](https://youtu.be/hBLC718adwg?si=vHdTgq4_wZAG-bdv)
- [Roboflow Blog - Occupancy Analytics](https://blog.roboflow.com/occupancy-analytics/#total-occupancy)
- [Polygon Zone](https://supervision.roboflow.com/detection/tools/polygon_zone/?ref=blog.roboflow.com#polygonzone)
