# The car is able to drive at least 4.32 miles without incident
Car can drive more than 4.32 miles without incident. Key point to succeed this was to use sensor fusion data and find cars nearby, as well as closing the track loop when creating the next points for the path ahead.

# The car drives according to speed limit
In code I set car's max speed to 49.8 miles per hour. Based on the conditions arround the car, it decelerate or accelerates up to this max speed.

# Max Acceleration and Jerk are not Exceeded.
The max possible accelereation is found to be 0.224. Jerk in left/right lane changes are prevented by usage of spline library which produces smooth transitions.

# Car does not have collisions.
Checking the sensor fusion data and acting according to it makes the car avoid collisions with cars in front and cars on the sides.

# The car stays in its lane, except for the time between changing lanes.
Using the d coordinate from the fresnet coordinate system to check for the middle of the lane helps with keeping the car in the lane.

# The car is able to change lanes
If the car is obstructed by another car in front of it, it checks first the left lane then the right lane for options. If it is possible it changes the lane.

# Model Documentation
Model documentation can be found below.

1) Process sensor fusion data to determine cars in front, left and right
2) Find the cars close to our car to decide if we need to switch lane, keep the lane or slow down.
    * If there is car in front of us and left lane is available then switch lane
    * If there is car in front of us and left lane is NOT available but right lane is available then switch lane
    * If there is car in front of us and both left and right lanes are not available then slow down.
    * If road is available increase the speed to max speed.
3) Use previous and future data to move the car properly
    * Create list of previous and future data points
    * Convert these points to local coordinates of the car to simplify the calculation
    * Give these points to spline as an input the generate smooth movements of the car.
    * Convert back the local car coordinates to global coordinates.
