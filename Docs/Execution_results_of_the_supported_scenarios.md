# Execution results of the supported scenarios

You can find the detailed description of how to execute the supported scenarios here:
[Instruction to execute the Supported scenarios](Execute_the_supported_scenarios.md).

## I.) Overview about the supported scenarios

You can list all supported scenarios (also for Open Scenario) in the terminal:
```
python scenario_runner.py --list
```

## II.) Execution result of the supported scenarios
You can replace the "[placeholder]" with any other scenario, e.g. "ManeuverOppositeDirection_1".
```
python scenario_runner.py --scenario [placeholder] --reloadWorld
```

### Maneuver Opposite Direction
In this scenario vehicle is passing another vehicle in a rural area, in daylight, under clear
weather conditions, at a non-junction and encroaches into another
vehicle traveling in the opposite direction. The 4 possible scenarios are:
```
ManeuverOppositeDirection_1 
ManeuverOppositeDirection_2
ManeuverOppositeDirection_3
ManeuverOppositeDirection_4
```

#### Notes
Only ManeuverOppositeDirection_2 and ManeuverOppositeDirection_4 are working. The others crashing by executing them.

#### Executing ManeuverOppositeDirection_2 & ManeuverOppositeDirection_4 with the autopilot
By starting the autopilot, car 1 is crashing into the obstacle while car 2 and 3 are passing the other lane.

![maneuveroppositedirection](img/Images%20for%20execution%20results/ManeuverOppositeDirection.jpeg) 

### Follow Leading Vehicle
The scenario realizes a common driving behavior, in which the user-controlled
ego vehicle follows a leading car driving down a given road in Town01. At some
point the leading car slows down and finally stops. The ego vehicle has to react
accordingly to avoid a collision. The scenario ends either via a timeout, or if
the ego vehicle stopped close enough to the leading vehicle. The 22 possible scenarios are:
```
FollowLeadingVehicle_1
FollowLeadingVehicleWithObstacle_1
FollowLeadingVehicle_2
FollowLeadingVehicleWithObstacle_2
FollowLeadingVehicle_3
FollowLeadingVehicleWithObstacle_3
FollowLeadingVehicle_4
FollowLeadingVehicleWithObstacle_4
FollowLeadingVehicle_5
FollowLeadingVehicleWithObstacle_5
FollowLeadingVehicle_6
FollowLeadingVehicleWithObstacle_6
FollowLeadingVehicle_7
FollowLeadingVehicleWithObstacle_7
FollowLeadingVehicle_8
FollowLeadingVehicleWithObstacle_8
FollowLeadingVehicle_9
FollowLeadingVehicleWithObstacle_9
FollowLeadingVehicle_10
FollowLeadingVehicleWithObstacle_10
FollowLeadingVehicle_11
FollowLeadingVehicleWithObstacle_11
```
#### Difference between with or without an obstacle
The obstacle in every scenario is a cyclist (marked with a "X")  who forces the vehicle in front to stop. As soon as the cyclist is off the road, the vehicles continue their journey.

#### Executing FollowLeadingVehicle_1 and FollowLeadingVehicleWithObstacle_1
The ego vehicle follows a leading car driving down a one-lane straight road in the city.
![](img/Images%20for%20execution%20results/IMG_20200529_131326.jpg)

#### Executing FollowLeadingVehicle_2 and FollowLeadingVehicleWithObstacle_2
The ego vehicle follows a leading car driving down a one-lane straight road in the city.
![](img/Images%20for%20execution%20results/IMG_20200529_131326.jpg)

#### Executing FollowLeadingVehicle_3 and FollowLeadingVehicleWithObstacle_3
The ego vehicle follows a leading car driving down a one-lane bend in the city.
![](img/Images%20for%20execution%20results/IMG_20200529_131349.jpg)

#### Executing FollowLeadingVehicle_4 and FollowLeadingVehicleWithObstacle_4
The ego vehicle follows a leading car driving down a two-lane straight road in the city.
![](img/Images%20for%20execution%20results/IMG_20200529_131415.jpg)

#### Executing FollowLeadingVehicle_5 and FollowLeadingVehicleWithObstacle_5
The ego vehicle follows a leading car driving down a four-lane straight road on a highway.

![](img/Images%20for%20execution%20results/IMG_20200529_131446.jpg)

#### Executing FollowLeadingVehicle_6 and FollowLeadingVehicleWithObstacle_6
The ego vehicle follows a leading car driving down a single-tracked curve with a steep climb in the mountains.
![](img/Images%20for%20execution%20results/IMG_20200529_131509.jpg)

#### Executing FollowLeadingVehicle_7 and FollowLeadingVehicleWithObstacle_7
The ego vehicle follows a leading car driving down a four-lane curve on a highway.
![](img/Images%20for%20execution%20results/IMG_20200529_131917.jpg)

#### Executing FollowLeadingVehicle_8 and FollowLeadingVehicleWithObstacle_8
The ego vehicle follows a leading car driving down a three-lane curve on a highway.
![](img/Images%20for%20execution%20results/IMG_20200529_131936.jpg)

#### Executing FollowLeadingVehicle_9 and FollowLeadingVehicleWithObstacle_9
The ego vehicle follows a leading car driving down a three-lane straight road in the middle on a highway.
![](img/Images%20for%20execution%20results/IMG_20200529_131952.jpg)

#### Executing FollowLeadingVehicle_10 and FollowLeadingVehicleWithObstacle_10
The ego vehicle follows a leading car driving down a three-lane straight road on the right lane on a highway.
![](img/Images%20for%20execution%20results/IMG_20200529_132011.jpg)

#### Executing FollowLeadingVehicle_11 and FollowLeadingVehicleWithObstacle_11
The ego vehicle follows a leading car driving down a one-lane straight road in the city.
![](img/Images%20for%20execution%20results/IMG_20200529_132027.jpg)

### Signalized Junction Left Turn
In this scenario hero vehicle is turning left in an urban area,
at a signalized intersection and cuts across the path of another vehicle
coming straight crossing from an opposite direction. The 6 possible scenarios are:
```
SignalizedJunctionLeftTurn_1
SignalizedJunctionLeftTurn_2
SignalizedJunctionLeftTurn_3
SignalizedJunctionLeftTurn_4
SignalizedJunctionLeftTurn_5
SignalizedJunctionLeftTurn_6
```

#### Executing SignalizedJunctionLeftTurn_1
The ego vehicle is approaching a singalized Junction and turns right.

![](img/Images%20for%20execution%20results/IMG_20200605_184547.jpg)

#### Executing SignalizedJunctionLeftTurn_2
The Szenario was not possible to execute.

#### Executing SignalizedJunctionLeftTurn_3
The Szenario was not possible to execute.

#### Executing SignalizedJunctionLeftTurn_4
The Szenario was not possible to execute.

#### Executing SignalizedJunctionLeftTurn_5
The ego vehicle is approaching a singalized Junction and turns left in a collision with another vehicle.
![](img/Images%20for%20execution%20results/IMG_20200605_185240.jpg)

#### Executing SignalizedJunctionLeftTurn_6
The ego vehicle is approaching a singalized Junction and drives straight ahead.
![](img/Images%20for%20execution%20results/IMG_20200605_185958.jpg)

### Signalized Junction Right Turn
In this scenario right turn of hero actor without collision at signalized intersection
is tested. Hero Vehicle is turning right in an urban area, at a signalized intersection and
turns into the same direction of another vehicle crossing straight initially from
a lateral direction. The 7 possible scenarios are:
```
SignalizedJunctionRightTurn_1
SignalizedJunctionRightTurn_2
SignalizedJunctionRightTurn_3
SignalizedJunctionRightTurn_4
SignalizedJunctionRightTurn_5
SignalizedJunctionRightTurn_6
SignalizedJunctionRightTurn_7
```

#### Executing SignalizedJunctionRightTurn_1
The ego vehicle is approaching a singalized Junction and turns left after the green light appeared.

![](img/Images%20for%20execution%20results/IMG_20200605_190200.jpg)

#### Executing SignalizedJunctionRightTurn_2
The ego vehicle drives to a signalized Junction and stops till another vehicle crosses the Junction.

![](img/Images%20for%20execution%20results/IMG_20200605_190200.jpg)

#### Executing SignalizedJunctionRightTurn_3
The ego vehicle drives to a signalized Junction and stops till another vehicle crosses the Junction.

    ![](img/Images%20for%20execution%20results/IMG_20200605_190200.jpg)

#### Executing SignalizedJunctionRightTurn_4
The Szenario was not possible to execute.

![]()

#### Executing SignalizedJunctionRightTurn_5
The ego vehicle drives to a signalized Junction and stops till another vehicle crosses the Junction.

![](img/Images%20for%20execution%20results/IMG_20200605_190200.jpg)

#### Executing SignalizedJunctionRightTurn_6
The ego vehicle drives to a signalized Junction and stops till another vehicle crosses the Junction.

![](img/Images%20for%20execution%20results/IMG_20200605_190200.jpg)

#### Executing SignalizedJunctionRightTurn_7
The ego vehicle drives to a signalized Junction and stops till another vehicle crosses the Junction.

![](img/Images%20for%20execution%20results/IMG_20200605_190200.jpg)

### Vehicle Turning Right
In this scenario the ego vehicle takes a right turn from an intersection where
a cyclist suddenly drives into the way of the ego vehicle,which has to stop
accordingly. After some time, the cyclist clears the road, such that ego vehicle
can continue driving. The 8 possible scenarios are:
```
VehicleTurningRight_1
VehicleTurningRight_2
VehicleTurningRight_3
VehicleTurningRight_4
VehicleTurningRight_5
VehicleTurningRight_6
VehicleTurningRight_7
VehicleTurningRight_8
```

#### Executing VehicleTurningRight_1
The ego vehicle drives to a signalized Junction and stops till the green light turns on. Then the vehicle turns left.

![](img/Images%20for%20execution%20results/IMG_20200605_190654.jpg)

#### Executing VehicleTurningRight_2
The ego vehicle drives to a signalized Junction and stops till the green light turns on. Then the vehicle turns left.

![](img/Images%20for%20execution%20results/IMG_20200605_190654.jpg)

#### Executing VehicleTurningRight_3
The ego vehicle drives to a signalized Junction and stops till the green light turns on. Then the vehicle turns right.

![](img/Images%20for%20execution%20results/IMG_20200605_191207.jpg)

#### Executing VehicleTurningRight_4 and VehicleTurningRight_5 and VehicleTurningRight_6
In this Szenario's the vehicle is only driving to the sinalized Junction and stops.

#### Executing VehicleTurningRight_7
The ego vehicle drives to a Junction and stops till a bycycle can drive over the street and then the vehicle turns right.

![](img/Images%20for%20execution%20results/IMG_20200605_192512.jpg)

### Vehicle Turning Left
This scenario is similar to 'VehicleTurningRight'. The difference is that the ego
vehicle takes a left turn from an intersection. The 8 possible scenarios are:
```
VehicleTurningLeft_1
VehicleTurningLeft_2
VehicleTurningLeft_3
VehicleTurningLeft_4
VehicleTurningLeft_5
VehicleTurningLeft_6
VehicleTurningLeft_7
VehicleTurningLeft_8
```

#### Executing VehicleTurningLeft_1 and VehicleTurningLeft_6
The ego vehicle takes a left turn from an intersection after the green signal turns on. In Addition the vehicle stops as a cyclist (marked with a "X") crosses the road.

![](img/Images%20for%20execution%20results/IMG_20200606_124757.jpg)

#### Executing VehicleTurningLeft_2
The ego vehicle takes a right turn from an intersection after the green signal turns on. 

![](img/Images%20for%20execution%20results/IMG_20200606_125358.jpg)

#### Executing VehicleTurningLeft_3 and VehicleTurningLeft_4 and VehicleTurningLeft_5
The ego vehicle takes a right turn from an intersection after the green signal turns on. 

![](img/Images%20for%20execution%20results/IMG_20200606_125358.jpg)


#### Executing VehicleTurningLeft_7 and Vehicle TurningLeft_8
The ego vehicle drives to an intersection and stops. In Addition in the scenario VehicleTUrningLeft7 the vehicle stops as a cyclist (marked with a "X") crosses the road.

![](img/Images%20for%20execution%20results/IMG_20200606_130214.jpg)


### Opposite Vehicle Running Red Light
In this scenario an illegal behavior at an intersection is tested. Another
vehicle waits at an intersection, but illegally runs a red traffic light. The
approaching ego vehicle has to handle this situation correctly, i.e. despite of
a green traffic light, it has to stop and wait until the intersection is clear
again. Afterwards, it should continue driving. The 5 possible scenarios are:
```
OppositeVehicleRunningRedLight_1
OppositeVehicleRunningRedLight_2
OppositeVehicleRunningRedLight_3
OppositeVehicleRunningRedLight_4
OppositeVehicleRunningRedLight_5
```

### Executing OppositeVehicleRunningRedLight_1
Another vehicle waits at an intersection, but illegally runs a red traffic light. The approaching ego vehicle stops and turns right after the other vehicle passed the intersection.

![](img/Images%20for%20execution%20results/IMG_20200606_133630.jpg)

### Executing OppositeVehicleRunningRedLight_2
Another vehicle waits at an intersection, but illegally runs a red traffic light. The approaching ego vehicle stops and drives straight on after the other vehicle passed the intersection.

![](img/Images%20for%20execution%20results/IMG_20200606_133855.jpg)

### Executing OppositeVehicleRunningRedLight_3
Another vehicle waits at an intersection, but illegally runs a red traffic light. The approaching ego vehicle stops and turns right after the other vehicle passed the intersection.

![](img/Images%20for%20execution%20results/IMG_20200606_134016.jpg)

### Executing OppositeVehicleRunningRedLight_4
The scenario works not correctly.

### Executing OppositeVehicleRunningRedLight_5
Another vehicle waits at an intersection, but illegally runs a red traffic light. The approaching ego vehicle stops and drives straight on after the other vehicle passed the intersection.

![](img/Images%20for%20execution%20results/IMG_20200606_134041.jpg)


### Other Leading Vehicle
The scenario realizes a common driving behavior, in which the user-controlled ego
vehicle follows a leading car driving down a given road.
At some point the leading car has to decelerate. The ego vehicle has to react
accordingly by changing lane to avoid a collision and follow the leading car in
other lane. The scenario ends via timeout, or if the ego vehicle drives certain
distance. The 10 possible scenarios are:
```
OtherLeadingVehicle_1
OtherLeadingVehicle_2
OtherLeadingVehicle_3
OtherLeadingVehicle_4
OtherLeadingVehicle_5
OtherLeadingVehicle_6
OtherLeadingVehicle_7
OtherLeadingVehicle_8
OtherLeadingVehicle_9
OtherLeadingVehicle_10
```

### Executing OtherLeadingVehicle_1 and OtherLeadingVehicle_2 and OtherLeadingVehicle_8 and OtherLeadingVehicle_9 and OtherLeadingVehicle_10
The user-controlled ego vehicle (shown in the rectangle) follows a leading car driving down a three-lane given road. Next to the leading car is another car.
At some point the leading cars decelerate. The ego vehicle reacts by decelearting too.
![](img/Images%20for%20execution%20results/IMG_20200608_173401.jpg)

### Executing OtherLeadingVehicle_3 and OtherLeadingVehicle_7
Its in fact the same scenarios as in the both Scenarios above. The little difference now is that there is a two-lane instead of a three-lane given.

### Executing OtherLeadingVehicle_4 and OtherLeadingVehicle_5 and OtherLeadingVehicle_6
Same Scenarios as the mentioned scenario above. The difference here ist that there is a four-lane given.

### Control Loss
In this scenario control loss of a vehicle is tested due to bad road conditions, etc
and it checks whether the vehicle is regained its control and corrected its course. The 15 possible scenarios are:
```
ControlLoss_1
ControlLoss_2
ControlLoss_3
ControlLoss_4
ControlLoss_5
ControlLoss_6
ControlLoss_7
ControlLoss_8
ControlLoss_9
ControlLoss_10
ControlLoss_11
ControlLoss_12
ControlLoss_13
ControlLoss_14
ControlLoss_15
```

### Executing ControlLoss_1 and ControlLoss_15
In this Scenario the ego vehicle has to drive over a poorly maintained road (marked with rectangles).

![](img/Images%20for%20execution%20results/IMG_20200608_183445.jpg)

### Executing ControlLoss_2 and ControlLoss_3 and ControlLoss_7 and ControlLoss_8
They are the same Scenario as described before. The difference is that after the second bad condition there is immediately followed another one.

### Executing ControlLoss_4 and ControlLoss_5 and ControlLoss_6
In this scenarios the car starts jerking, but there is no bad condition visible.

### Executing ControlLoss_9 and ControlLoss_12
In this Scenario the ego vehicle has to drive over a poorly maintained road (marked with rectangles).

![](img/Images%20for%20execution%20results/IMG_20200608_183842(1).jpg)

### Executing ControlLoss_10 and ControlLoss_11
In this Scenario the ego vehicle has to drive over a poorly maintained road (marked with rectangles). The three bad entities have approximately the same distance from each other.

![](img/Images%20for%20execution%20results/IMG_20200608_184709.jpg)

### Executing ControlLoss_10 and ControlLoss_13
In this Scenario the ego vehicle has to drive over a poorly maintained road (marked with rectangles).

![](img/Images%20for%20execution%20results/IMG_20200608_190227.jpg)

### Executing ControlLoss_10 and ControlLoss_14
In this Scenario the ego vehicle has to drive over a poorly maintained road (marked with rectangles).

![](img/Images%20for%20execution%20results/IMG_20200608_190302.jpg)

### Stationary Object Crossing
In this scenario a container is stationary waiting in the middle of the road and
blocking the way for the ego vehicle. Hence, the ego vehicle has to stop in
front of the container. The 8 possible scenarios are:
```
StationaryObjectCrossing_1
StationaryObjectCrossing_2
StationaryObjectCrossing_3
StationaryObjectCrossing_4
StationaryObjectCrossing_5
StationaryObjectCrossing_6
StationaryObjectCrossing_7
StationaryObjectCrossing_8
```

### Executing StationaryObjectCrossing_1 and StationaryObjectCrossing_2 and StationaryObjectCrossing_7
In this Scenario the ego vehicle collides against a container in the middle of the road.

![](img/Images%20for%20execution%20results/IMG_20200614_203545.jpg)

### Executing StationaryObjectCrossing_3
In this Scenario the container is on a intersection.

![](img/Images%20for%20execution%20results/IMG_20200614_203851(1).jpg)

### Executing StationaryObjectCrossing_4
In this Scenario the container is in the middle of a curve.

![](img/Images%20for%20execution%20results/IMG_20200614_203642.jpg)

### Executing StationaryObjectCrossing_5 and StationaryObjectCrossing_6
In this Scenario the container is on a highway.

![](img/Images%20for%20execution%20results/IMG_20200614_203941.jpg)

### Executing StationaryObjectCrossing_8
This Scenario is not possible to execute.

### Dynamic Object Crossing
This is similar to 'StationaryObjectCrossing', but with the difference that the
Container is a running human, who suddenly drives into the way of the ego vehicle, which
has to stop accordingly. After some time, the human will clear the road, such
that the ego vehicle can continue driving. The 9 possible scenarios are:
```
DynamicObjectCrossing_1
DynamicObjectCrossing_2
DynamicObjectCrossing_3
DynamicObjectCrossing_4
DynamicObjectCrossing_5
DynamicObjectCrossing_6
DynamicObjectCrossing_7
DynamicObjectCrossing_8
DynamicObjectCrossing_9
```

### Executing DynamicObjectCrossing_1 and DynamicObjectCrossing_2 and DynamicObjectCrossing_3 and DynamicObjectCrossing_4 and DynamicObjectCrossing_7 and DynamicObjectCrossing_9
In this Scenario a human is running into the way of the ego vehicle, which has to stop accordingly.

![](img/Images%20for%20execution%20results/IMG_20200614_204035.jpg)

### Executing DynamicObjectCrossing_5 and DynamicObjectCrossing_6 and DynamicObjectCrossing_8
This Scenarios are not working correctly. 

### No Signal Junction Crossing
This scenario tests negotiation between two vehicles crossing cross each other
through a junction without signal.
The ego vehicle is passing through a junction without traffic lights
And encounters another vehicle passing across the junction. The ego vehicle has
to avoid collision and navigate across the junction to succeed. The 1 possible scenarios is:
```
NoSignalJunctionCrossing
```
![](img/Images%20for%20execution%20results/IMG_20200606_133018(3).jpg)


### Change Lane
This Scenario was not possible to execute.
```
ChangeLane
ChangeLane_2
```

### Challenge Basic
This Scenario was not possible to execute.
```
Challenge_Basic_00
Challenge_Basic_01
Challenge_Basic_03
Challenge_Basic_04
```

### Background Activity
This Scenario was not possible to execute.
```
BackgroundActivity_1
```

### Cut in from left Lane
This Scenario was not possible to execute.
```
CutInFrom_left_Lane
```
### Cut in from right Lane
In this scenario, the Ego Vehicle drives in the middle lane on the highway while another vehicle overtakes it from the right and pulls into the middle lane so that the Ego Vehicle has to brake down briefly.
```
CutInFrom_right_Lane
```
![](img/Images%20for%20execution%20results/IMG_20200628_184223.jpg)

### Free Ride Town
This Scenario were not possible to execute.
```
FreeRideTown01
FreeRideTown02
FreeRideTown03
FreeRideTown04
```

### MultiEgoTown
This Scenarios were not possible to execute.
```
MultiEgoTown01
MultiEgoTown03
```

### VehicleTurnLeftAtJunction
This Scenarios were not possible to execute.
```
VehicleTurnLeftAtJunction_1
VehicleTurnLeftAtJunction_2
VehicleTurnLeftAtJunction_3
VehicleTurnLeftAtJunction_4
VehicleTurnLeftAtJunction_5
VehicleTurnLeftAtJunction_6
```

## III.) Execution result of the supported scenarios for Open Scenario
You can replace the "[placeholder]" with any other scenario, e.g. "LaneChaneSimple".
```
python scenario_runner.py --openscenario srunner/examples/[placeholder].xosc
```

### Lane Change Simple
In this scenario, the Ego Vehicle (far left) has to brake down when driving onto the middle vehicle, a little later the middle vehicle passes the vehicle in front on the left lane.
```
LaneChangeSimple
```
![](img/Images%20for%20execution%20results/IMG_20200628_184208.jpg)

### Pedestrian Crossing
This Scenario was not possible to execute.
```
Pedestrian Crossing
```

### Follow Leading Vehicle
This scenario is the same procedure as the "Follow Leading Vehicle Scenario" described above.
```
FollowLeadingVehicle
```


### Cyclist Crossing
This Scenario is not working correctly. After a traffic light the car has is driving right while a Cyclist is Crossing the street. However the car is crashing against this cyclist.
```
CyclistCrossing
```

## IV.) Next references
You can find "how to write your own scenarios" here: 
[3. Writing_your_own_scenario](Writing_your_own_scenario.md).
