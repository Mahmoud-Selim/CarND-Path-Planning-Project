# **Path Planning**


**Path Planning Project**

The goals / steps of this project are the following:
* Make a prediction model from the sensor fusion data 
* Use a path planning methods to plan the next state of the car
* generate the points which the car actually passes through
* Test that the model on the simulator.
* Summarize the results with a written report



## Rubric Points
### Here I will consider the [rubric points](https://review.udacity.com/#!/rubrics/1971/view) individually and describe how I addressed each point in my implementation.  

---
### Compilation

#### 1. The code compiles correctly.
My project includes the following files:
* main.cpp file which includes the path planner code + the code required for the interfacing with the simulator
* spline.h file which include the code required for the points generation.
* a cmake file that compiles the project successfully.
* A writeup file addressing how the project was implemented.

### Valid Trajectories.
#### 2. The car is able to drive at least 4.32 miles without incident.	
The car was tested and it drove over 15 miles on my local machine. It was also tested many times to ensure the quality of the path planner.

#### 3. The car drives according to the speed limit.
Yes, The car didn't pass the 50 MPH. It also stayed within the jerk and acceleration limits specified by the project.

#### 4. Max Acceleration and Jerk are not Exceeded.
The car doesn't exceed the limits of 10 m/s^2 or 10 m/s^3 for acceleration and jerk respectively.

#### 5.Car does not have collisions.
The car didn't make any collisions on my machine.

### 6. The car stays in its lane, except for the time between changing lanes.
The car doesn't go out of the lane boundries unless it's changing lanes.

### 7. The car is able to change lanes
The car changes lanes when it's safe and beneficial for the effeciency or the speed of the car, but, safety comes first.


### Model Architecture and Strategy
The model consists of three modules:

#### 1. Prediction Model
The car uses the data from the sensor fusion module to make predictions about other vehicles on the road. It makes these predictions every time it generates new points.

The prediction function is the `make_prediction()` function.
 
#### 2. Path Planner 
Regargind the planner of the car, it starts with the fuction `choose_next_state()` this function makes a call the the `make_prediction()` functions and then computes the cost by calling the `compute_cost()` function it then selects the state associated with the lowest cost

### 3. Cost Functions
The planner has two functions. the first one computes the inefficeiency of the car with is the speed. the lower the speed, the higher the inefficiency of the car. The second one is the `distance_cost()` function. This one is responsible for making costs for the states when the state is unsafe. the compute_cost() function computes both costs but, penalizes the `dist_cost` with higher weight and that's because safety is considered more important than the speed of the car. 

### 4. Spline And The Path Generator
The pathplanner only selects the state of the car, that is the lane in which the car drives. Then, it sends this information to the spline module. We use it to generate points for the car and sends these points to the simulator.

### Finally, some screen shots of the car surpassing 15 miles and changing lanes.

![alt text](https://github.com/Mahmoud-Selim/CarND-Path-Planning-Project/blob/master/Screenshots/Screenshot%20from%202018-12-27%2005-21-24.png)

![alt text](https://github.com/Mahmoud-Selim/CarND-Path-Planning-Project/blob/master/Screenshots/Screenshot%20from%202018-12-27%2005-23-09.png)

![alt text](https://github.com/Mahmoud-Selim/CarND-Path-Planning-Project/blob/master/Screenshots/Screenshot%20from%202018-12-27%2005-23-59.png)

![alt text](https://github.com/Mahmoud-Selim/CarND-Path-Planning-Project/blob/master/Screenshots/Screenshot%20from%202018-12-27%2005-27-11.png)
