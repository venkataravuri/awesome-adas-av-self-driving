# Mapping & Localization

## Mapping Overview

Maps includes elements such as road boundaries, lane delimiters, centerlines, direction of travel and crosswalks.

Mapping is a process of predicting map elements for a given set of surround view images and lidar point clouds.

## Map Categores

- Toplogical Maps (Traditional)
- HD Maps
 - Offline
 - Online 
- Mapless Autonomous Driving

### Topological Maps (Traditional)

Topological maps includes attributes like road topology, lane topology (number of lanes), building footprints, street segments, direction of travel, parking lots. They are useful to know how to get from point A to point B.

Data used to assemble these maps are produced from cameras mounted on dashboards (can be crowdsourced), aerial imagery from satelites, planes and drones.

#### What are different approaches to assemble toplogical maps?

- Segmentation followed by Heuristics - Usually done through Road pixel binary semantic segmentation on aerial imagery followed by heuristic to get the road network. It is subjected to challenges such as partial occlusion or an unexpected angle in areal imagery.
- Engergy based
- Neural Network

### HD Maps

High-definition (HD) maps offer an intricate and precise depiction of the road, encompassing lane markings, traffic signs, and other critical features.

HD Maps contain both geometric structure information as well as semantics.

<img src="https://geospatialmedia.s3.amazonaws.com/wp-content/uploads/2016/04/here-1.jpg" height="50%" width="50%" />

#### What are different HD map layers?

HD Map is organized into layers. 

<img src="https://geospatialmedia.s3.amazonaws.com/wp-content/uploads/2019/01/HD-Maps-Layers-20190107.png" height="30%" width="30%" />

| Layer | Mappying Information | ? |
| --- | --- | --- |
| 1 | Topological Representation | Topology captures how roads, lanes, intersections, and other features are connected |
| 2 | Geometric Representation | Geometric features include the shapes and positions of roads, lanes, sidewalks, buildings, and terrain. These features are typically represented using a vector data structure, which describes simplified geometric shapes such as points, lines, curves, circles, and polygon. |
| 3 | Semantic Representation | Semantic representation includes various traffic 2D and 3D objects such as lane boundaries, intersections, crosswalks, parking spots, stop signs, traffic lights, road speed limits, lane information, and road classification |
| 4 | Dynamic elements |  Dynamic elements like pedestrians, obstacles, and vehicles need to be updated for the HD map to be always precise and accurate. The dynamic element layer of HD maps captures and represents these time-varying aspects of the environment, which are essential for safe and efficient path planning and decision-making. |
| 5 | Feature-Based Map Layers | HD maps rely heavily on advanced feature-based map layers for accurate localization and navigation. These layers use various techniques to identify and match features in the environment to ensure precise vehicle positioning. |

### What are different HD Maps formats?

| Format | Description File | Format Representations |
| --- | --- | --- |
| OpenDRIVE | Standard for logical description of road networks | XML Geometric primitives |
| Lanelet2 | HD map format for autonomous driving XML, OSM | Points |
| NDS | Global standard for automotive map data | Binary Vector data |

### HD Map Generation Techniques

4 techniques are used to perform point cloud registration: optimization-based approaches, probabilistic-based approaches, feature-based approaches, and deep learning techniques.

- [HDMapNet: An Online HD Map Construction and Evaluation Framework](https://arxiv.org/pdf/2107.06307)
- [MapTRv2: An End-to-End Framework for Online Vectorized HD Map Construction](https://arxiv.org/pdf/2308.05736)

 PoseNet and VLocNet++, are some of the frameworks that use point data to estimate the 3D position and orientation. These estimated 3D positions and orientations can be used to derive scene semantics, as seen in the image below.

### Online HD Maps

- [HDMapNet: An Online HD Map Construction and Evaluation Framework - 2022](https://arxiv.org/abs/2107.06307)


## Mapless Autonomous Driving

Mapless autonomous driving leverages a combination of cameras and sensors to create a dynamic perception map of the vehicle’s surroundings without relying on pre-loaded HD maps.

Companies like Imagry, Deeproute, Tesla was the frontrunner among OEMs adopting Mapless AD for its lineup using FSD, other OEMs such as Xpeng, Huawei AITO, GAC Aion and Li Auto have also adopted Mapless.

Map-based AD systems depend on detailed pre-loaded HD maps, which are regularly updated to ensure accuracy and reliability. Major players like Google, HERE, and TomTom provide these comprehensive maps, which enhance navigation and route guidance. 

[MapVision: CVPR 2024 Autonomous Grand Challenge Mapless Driving Tech Report](https://arxiv.org/pdf/2406.10125v1)


## Localization

Localization module tells the car where you are in the 3D space, and what’s actually around you.

Localization algorithms in self-driving cars calculate the position and orientation of the vehicle as it navigates – a science known as Visual Odometry (VO).

VO works by matching key points in consecutive video frames. With each frame, the key points are used as the input to a mapping algorithm. The mapping algorithm, such as Simultaneous localization and mapping (SLAM), computes the position and orientation of each object nearby with respect to the previous frame and helps to classify roads, pedestrians, and other objects around.

### References

- [A Comprehensive Survey on High-Definition Map Generation and Maintenance](https://www.mdpi.com/2220-9964/13/7/232)
