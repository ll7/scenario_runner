# Execution results of the supported scenarios

You can find the detailed description of how to execute the supported scenarios here:
[Instruction to execute the Supported scenarios](instruction_to_execute_the_supported_scenarios.md).

##I.) Overview about the supported scenarios

You can list all supported scenarios (also for Open Scenario) in the terminal:
```
python scenario_runner.py --list
```

##II.) Execution result of the supported scenarios
You can replace the "[placeholder]" with any other scenario, e.g. "ManeuverOppositeDirection_1".
```
python scenario_runner.py --scenario [placeholder] --reloadWorld
```

###Maneuver Opposite Direction
In this scenario vehicle is passing another vehicle in a rural area, in daylight, under clear
weather conditions, at a non-junction and encroaches into another
vehicle traveling in the opposite direction. The 4 possible scenarios are:
```
ManeuverOppositeDirection_1 
ManeuverOppositeDirection_2
ManeuverOppositeDirection_3
ManeuverOppositeDirection_4
```

####Notes
Only ManeuverOppositeDirection_2 and ManeuverOppositeDirection_4 are working. The others crashing by executing them.

#### Executing ManeuverOppositeDirection_2 & ManeuverOppositeDirection_4 with the autopilot
By starting the autopilot, car 1 is crashing into the obstacle while car 2 and 3 are passing the other lane.

![maneuveroppositedirection](https://github.com/ll7/scenario_runner/blob/master/Docs/img/Images%20for%20execution%20results/ManeuverOppositeDirection.jpeg) 

###Follow Leading Vehicle
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
The obstacle in every scenario is a cyclist who forces the vehicle in front to stop. As soon as the cyclist is off the road, the vehicles continue their journey.

#### Executing FollowLeadingVehicle_1 and FollowLeadingVehicleWithObstacle_1
The ego vehicle follows a leading car driving down a one-lane straight road in the city.
![](https://github.com/ll7/scenario_runner/blob/master/Docs/img/Images%20for%20execution%20results/IMG_20200529_131326.jpg)

#### Executing FollowLeadingVehicle_2 and FollowLeadingVehicleWithObstacle_2
The ego vehicle follows a leading car driving down a one-lane straight road in the city.
![](https://github.com/ll7/scenario_runner/blob/master/Docs/img/Images%20for%20execution%20results/IMG_20200529_131326.jpg)

#### Executing FollowLeadingVehicle_3 and FollowLeadingVehicleWithObstacle_3
The ego vehicle follows a leading car driving down a one-lane bend in the city.
![](https://github.com/ll7/scenario_runner/blob/master/Docs/img/Images%20for%20execution%20results/IMG_20200529_131349.jpg)

#### Executing FollowLeadingVehicle_4 and FollowLeadingVehicleWithObstacle_4
The ego vehicle follows a leading car driving down a two-lane straight road in the city.
![](https://github.com/ll7/scenario_runner/blob/master/Docs/img/Images%20for%20execution%20results/IMG_20200529_131415.jpg)

#### Executing FollowLeadingVehicle_5 and FollowLeadingVehicleWithObstacle_5
The ego vehicle follows a leading car driving down a four-lane straight road on a highway.

![](https://github.com/ll7/scenario_runner/blob/master/Docs/img/Images%20for%20execution%20results/IMG_20200529_131446.jpg)

#### Executing FollowLeadingVehicle_6 and FollowLeadingVehicleWithObstacle_6
The ego vehicle follows a leading car driving down a single-tracked curve with a steep climb in the mountains.
![](https://github.com/ll7/scenario_runner/blob/master/Docs/img/Images%20for%20execution%20results/IMG_20200529_131509.jpg)

#### Executing FollowLeadingVehicle_7 and FollowLeadingVehicleWithObstacle_7
The ego vehicle follows a leading car driving down a four-lane curve on a highway.
![](https://github.com/ll7/scenario_runner/blob/master/Docs/img/Images%20for%20execution%20results/IMG_20200529_131917.jpg)

#### Executing FollowLeadingVehicle_8 and FollowLeadingVehicleWithObstacle_8
The ego vehicle follows a leading car driving down a three-lane curve on a highway.
![](https://github.com/ll7/scenario_runner/blob/master/Docs/img/Images%20for%20execution%20results/IMG_20200529__131936.jpg)

#### Executing FollowLeadingVehicle_9 and FollowLeadingVehicleWithObstacle_9
The ego vehicle follows a leading car driving down a three-lane straight road in the middle on a highway.
![](https://github.com/ll7/scenario_runner/blob/master/Docs/img/Images%20for%20execution%20results/IMG_20200529__131952.jpg)

#### Executing FollowLeadingVehicle_10 and FollowLeadingVehicleWithObstacle_10
The ego vehicle follows a leading car driving down a three-lane straight road on the right lane on a highway.
![](https://github.com/ll7/scenario_runner/blob/master/Docs/img/Images%20for%20execution%20results/IMG_20200529__132011.jpg)

#### Executing FollowLeadingVehicle_11 and FollowLeadingVehicleWithObstacle_11
The ego vehicle follows a leading car driving down a one-lane straight road in the city.
![](https://github.com/ll7/scenario_runner/blob/master/Docs/img/Images%20for%20execution%20results/IMG_20200529__132027.jpg)

###Signalized Junction Left Turn
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

###Signalized Junction Right Turn
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

###Vehicle Turning Right
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

###Vehicle Turning Left
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

###Opposite Vehicle Running Red Light
In this scenario an illegal behavior at an intersection is tested. An other
vehicle waits at an intersection, but illegally runs a red traffic light. The
approaching ego vehicle has to handle this situation correctly, i.e. despite of
a green traffic light, it has to stop and wait until the intersection is clear
again. Afterwards, it should continue driving. The 5 possible scenarios are:
```
OppositeVehicleRunningRedLight011
OppositeVehicleRunningRedLight021
OppositeVehicleRunningRedLight031
OppositeVehicleRunningRedLight032
OppositeVehicleRunningRedLight033
```

###Other Leading Vehicle
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

###Control Loss
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

###Stationary Object Crossing
In this scenario a cyclist is stationary waiting in the middle of the road and
blocking the way for the ego vehicle. Hence, the ego vehicle has to stop in
front of the cyclist. The 8 possible scenarios are:
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

###Dynamic Object Crossing
This is similar to 'StationaryObjectCrossing', but with the difference that the
cyclist is dynamic. It suddenly drives into the way of the ego vehicle, which
has to stop accordingly. After some time, the cyclist will clear the road, such
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

###No Signal Junction Crossing
This scenario tests negotiation between two vehicles crossing cross each other
through a junction without signal.
The ego vehicle is passing through a junction without traffic lights
And encounters another vehicle passing across the junction. The ego vehicle has
to avoid collision and navigate across the junction to succeed. The 1 possible scenarios is:
```
NoSignalJunctionCrossing
```

###Change Lane
??????
```
ChangeLane
ChangeLane_2
```

###Challenge Basic
???
```
Challenge_Basic_00
Challenge_Basic_01
Challenge_Basic_03
Challenge_Basic_04
```

###Background Activity
???
```
BackgroundActivity_1
```

###Cut in from left Lane
???
```
CutInFrom_left_Lane
```
###Cut in from right Lane
???
```
CutInFrom_right_Lane
```


###Free Ride Town
???
```
FreeRideTown01
FreeRideTown02
FreeRideTown03
FreeRideTown04
```

###MultiEgoTown
???
```
MultiEgoTown01
MultiEgoTown03
```

###VehicleTurnLeftAtJunction
???
```
VehicleTurnLeftAtJunction_1
VehicleTurnLeftAtJunction_2
VehicleTurnLeftAtJunction_3
VehicleTurnLeftAtJunction_4
VehicleTurnLeftAtJunction_5
VehicleTurnLeftAtJunction_6
```

##III.) Execution result of the supported scenarios for Open Scenario
You can replace the "[placeholder]" with any other scenario, e.g. "LaneChaneSimple".
```
python scenario_runner.py --openscenario srunner/examples/[placeholder].xosc
```

###Lane Change Simple
???
```
LaneChangeSimple
```

###Pedestrian Crossing
???
```
Pedestrian Crossing
```

###Follow Leading Vehicle
???
```
FollowLeadingVehicle
```


###Cyclist Crossing
???
```
CyclistCrossing
```


