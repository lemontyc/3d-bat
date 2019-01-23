# Installation
1. Clone repository: git clone https://github.com/walzimmer/3D_BoundingBox_Annotation_Tool_3D_BAT.git
2. Install npm: $sudo apt-get install npm
3. Install required packages: $npm install
4. Install PHP Storm (IDE with integrated server): https://www.jetbrains.com/phpstorm/download/download-thanks.html
5. Open index.html with chromium-browser (Linux) or Chrome (Windows) within the IDE
6. Install WhatPulse to measure the number of clicks and key strokes while labeling 
 
# 3D Boundingbox Annotation Instructions
1. Step: Draw bounding box in the Bird's-Eye-View (BEV)
2. Step: Move/Scale it in BEV using 3D arrows (drag and drop) or sliders
3. Step: Choose one of the 5 classes (Car, Pedestrian, Cyclist, Motorbike, Truck)
4. Step: Interpolate if necessary
    1. Select Object to interpolate by clicking on a Bounding Box
    2. Active Interpolation Mode in the menu (checkbox) -> start position will be saved
    3. Move to desired frame by skipping x frames
    4. Click on the 'Interpolate' button in the menu
5. Step: Repeat steps 1-4 for all objects in the sequence
6. Step: Download labels to your computer (JSON file)
7. Step: Stop the time after labeling is done.

# Keyboard Shortcuts
| Key | Description   | |
| --- | ------------- |---|
|  N  | Next frame     ||
|  P  | Previous frame   ||
|  I  | Interpolate    ||
|  CTRL+move bounding box  | Snap to grid in 0.5m steps   ||
|  T  | Enable/Disable Translation mode||
|     |  W  | Move selected object forward (TODO)|
|     |  A  | Move selected object to left (TODO)|
|     |  S  | Move selected object backward (TODO)|
|     |  D  | Move selected object to right (TODO)|
|     |  Q  | Move selected object down (TODO)|
|     |  E  | Move selected object up (TODO)|
|  R  | Enable/Disable Rotation mode||
|     |  LEFT | Rotate selected object counter-clock-wise (TODO)|
|     |  RIGHT  | Rotate selected object clock-wise (TODO)|
|  Y  | Enable/Disable Scaling mode ||
|     | UP | Increase length along longitudinal axis (y-axis) (TODO)|
|     | DOWN | Decrease length along longitudinal axis (y-axis) (TODO)|
|     |  LEFT  | Decrease width along lateral axis (x-axis) (TODO)|
|     |  RIGHT  | Increase width along lateral axis (x-axis) (TODO)|
|     |  SHIFT-RIGHT  | Increase height along vertical axis (z-axis) (TODO)|
|     |  CTRL-RIGHT | Decrease height along vertical axis (z-axis) (TODO)|
|  +  | Increase arrow size ||
|  -  | Decrease arrow size ||
|  X  | Show/Hide X-axis ||
|  Y  | Show/Hide Y-axis ||
|  Z  | Show/Hide Z-axis (only in 3D mode)||
|  Spacebar  | Enable/Disable Transform Controls ||
|  TAB  | Select next object (TODO)||
| DEL | Delete selected object (TODO)||
|  M  | Marking mode (TODO)||
|     | LEFT | Move orientation of object counter-clock-wise (TODO)|
|     | RIGHT| Move orientation of object clock-wise (TODO)|
|  1  | Select class CAR (TODO)||
|  2  | Select class Truck (TODO)||
|  3  | Select class Motorcycle (TODO)||
|  4  | Select class Bicycle (TODO)||  
|  5  | Select class Pedestrian (TODO)||





Hints:
+ Select 'Copy label to next frame' checkbox if you want to keep the label (position, size, class) for next frame 
+ Use helper views to align object along z-axis (no need to switch into 3D view)
+ Label one object from start to end (using interpolation) and then continue with next object 
+ **Do not** apply more than one box to a single object.
+ Check every cuboid in every frame, to make sure all points are inside the cuboid and **look reasonable in the image view**.

# Special Rules
+ **Minimum LIDAR Points** : 
    + Label any target object containing **at least 10 LIDAR point**, as long as you can be reasonably sure you know the location and shape of the object. Use your best judgment on correct cuboid position, sizing, and heading. 
+ **Cuboid Sizing** : 
    + **Cuboids must be very tight.** Draw the cuboid as close as possible to the edge of the object without excluding any LIDAR points. There should be almost no visible space between the cuboid border and the closest point on the object. 
+ **Extremities** : 
    + **If** an object has extremities (eg. arms and legs of pedestrians), **then** the bounding box should include the extremities. 
    + **Exception**: Do not include vehicle side view mirrors. Also, do not include other vehicle extremities (crane arms etc.) that are above 1.5 meters high. 
+ **Carried Object** : 
    + If a pedestrian is carrying an object (bags, umbrellas, tools etc.), such object will be included in the bounding box for the pedestrian. If two or more pedestrians are carrying the same object, the bounding box of only one of them will include the object.
+ **Use Pictures**:
    + For objects with few LIDAR points, use the images to make sure boxes are correctly sized. If you see that a cuboid is too short in the image view, adjust it to cover the entire object based on the image view.

# Labels 
**For every bounding box, include one of the following labels:**
1. **[Car](#car)**: Vehicle designed primarily for personal use, e.g. sedans, hatch-backs, wagons, vans, mini-vans, SUVs, jeeps and pickup trucks (A pickup truck is a light duty truck with an enclosed cab and an open or closed cargo area. A pickup truck can be intended primarily for hauling cargo or for personal use).   

2. **[Truck](#truck)**: Vehicles primarily designed to haul cargo including lorrys, trucks. 
 
3. **[Motorcycle](#motorcycle)**: Gasoline or electric powered 2-wheeled vehicle designed to move rapidly (at the speed of standard cars) on the road surface. This category includes all motorcycles, vespas and scooters. It also includes light 3-wheel vehicles, often with a light plastic roof and open on the sides, that tend to be common in Asia. If there is a rider and/or passenger, include them in the box.

4. **[Bicycle](#bicycle)**: Human or electric powered 2-wheeled vehicle designed to travel at lower speeds either on road surface, sidewalks or bicycle paths. If there is a rider and/or passenger, include them in the box.

5. **[Pedestrian](#pedestrian)**: An adult/child pedestrian moving around the cityscape. Mannequins should also be annotated as Pedestrian.  
 
 # Detailed Instructions and Examples 
 
Bounding Box color convention in example images: 
 + **Green**: Objects like this should be annotated 
 + **Red**: Objects like this should not be annotated 

 
## Car
+ Vehicle designed primarily for personal use, e.g. sedans, hatch-backs, wagons, vans, mini-vans, SUVs and jeeps.   
    + If it is primarily designed to haul cargo it is a truck.
     
    ![](https://www.nuscenes.org/public/images/taxonomy_imgs/personal_vehicle_2.jpg)
    ![](https://www.nuscenes.org/public/images/taxonomy_imgs/personal_vehicle_4.jpg)

## Truck 
+ Vehicles primarily designed to haul cargo including lorrys, trucks, pickup truck (+ A pickup truck is a light duty truck with an enclosed cab and an open or closed cargo area. A pickup truck can be intended primarily for hauling cargo or for personal use).

    ![](https://www.nuscenes.org/public/images/taxonomy_imgs/truck_2.jpg)
    ![](https://www.nuscenes.org/public/images/taxonomy_imgs/truck_3.jpg)
    ![](https://www.nuscenes.org/public/images/taxonomy_imgs/truck_4.jpg)
    ![](https://www.nuscenes.org/public/images/taxonomy_imgs/truck_5.jpg)
    ![](https://www.nuscenes.org/public/images/taxonomy_imgs/pickup_truck_2.jpg)
    ![](https://www.nuscenes.org/public/images/taxonomy_imgs/pickup_truck_3.jpg)
    ![](https://www.nuscenes.org/public/images/taxonomy_imgs/pickup_truck_4.jpg)
    ![](https://www.nuscenes.org/public/images/taxonomy_imgs/pickup_truck_5.jpg)
    ![](https://www.nuscenes.org/public/images/taxonomy_imgs/front_of_semi_truck_2.png)
    ![](https://www.nuscenes.org/public/images/taxonomy_imgs/front_of_semi_truck_3.png)
    ![](https://www.nuscenes.org/public/images/taxonomy_imgs/front_of_semi_truck_5.png)
    ![](https://www.nuscenes.org/public/images/taxonomy_imgs/front_of_semi_truck_6.png)
    ![](https://www.nuscenes.org/public/images/taxonomy_imgs/front_of_semi_truck_7.png)
    ![](https://www.nuscenes.org/public/images/taxonomy_imgs/front_of_semi_truck_8.png)

 ## Motorcycle 
+ Gasoline or electric powered 2-wheeled vehicle designed to move rapidly (at the speed of standard cars) on the road surface. This category includes all motorcycles, vespas and scooters. It also includes light 3-wheel vehicles, often with a light plastic roof and open on the sides, that tend to be common in Asia. 
    + If there is a rider, include the rider in the box.
    + If there is a passenger, include the passenger in the box. 
    + If there is a pedestrian standing next to the motorcycle, do NOT include in the annotation. 

    ![](https://www.nuscenes.org/public/images/taxonomy_imgs/motorcycle_1.jpg)
    ![](https://www.nuscenes.org/public/images/taxonomy_imgs/motorcycle_2.jpg)
    ![](https://www.nuscenes.org/public/images/taxonomy_imgs/motorcycle_3.jpg)
    ![](https://www.nuscenes.org/public/images/taxonomy_imgs/motorcycle_4.jpg)
    ![](https://www.nuscenes.org/public/images/taxonomy_imgs/motorcycle_5.jpg)
    ![](https://www.nuscenes.org/public/images/taxonomy_imgs/motorcycle_6.jpg)
    ![](https://www.nuscenes.org/public/images/taxonomy_imgs/motorcycle_7.jpg)
    ![](https://www.nuscenes.org/public/images/taxonomy_imgs/motorcycle_8.jpg)

## Bicycle 
+ Human or electric powered 2-wheeled vehicle designed to travel at lower speeds either on road surface, sidewalks or bicycle paths. 
    + If there is a rider, include the rider in the box 
    + If there is a passenger, include the passenger in the box 
    + If there is a pedestrian standing next to the bicycle, do NOT include in the annotation 

    ![](https://www.nuscenes.org/public/images/taxonomy_imgs/bicycle_1.jpg)
    ![](https://www.nuscenes.org/public/images/taxonomy_imgs/bicycle_2.jpg)
    ![](https://www.nuscenes.org/public/images/taxonomy_imgs/bicycle_3.jpg)
    ![](https://www.nuscenes.org/public/images/taxonomy_imgs/bicycle_4.jpg) 


## Adult/child Pedestrian 
+ An adult/child pedestrian moving around the cityscape. 
    + Mannequins should also be treated as pedestrian. 

    ![](https://www.nuscenes.org/public/images/taxonomy_imgs/mannequin_1.png)
    ![](https://www.nuscenes.org/public/images/taxonomy_imgs/adult_pedestrian_2.jpg)
    ![](https://www.nuscenes.org/public/images/taxonomy_imgs/adult_pedestrian_3.jpg)
    ![](https://www.nuscenes.org/public/images/taxonomy_imgs/adult_pedestrian_4.jpg)
    ![](https://www.nuscenes.org/public/images/taxonomy_imgs/adult_pedestrian_5.jpg) 
    ![](https://www.nuscenes.org/public/images/taxonomy_imgs/child_pedestrian_1.jpg)
    ![](https://www.nuscenes.org/public/images/taxonomy_imgs/child_pedestrian_3.jpg)
    ![](https://www.nuscenes.org/public/images/taxonomy_imgs/child_pedestrian_4.jpg)
    ![](https://www.nuscenes.org/public/images/taxonomy_imgs/child_pedestrian_5.jpg)
