# Modify an existing scenario
This part lists everything I have access to (e.g. position, agents, speed, towns, weather) through the scenario classes and their XML-Files and how I can use it to modify an existing scenario.

## 1.) Modify the class of a Scenario
To modify the class of a Scenario you can do this in the three different standard methods 
- Initalize(),
- CreateBehavior()
- and CreateTestCriteria()

described in [4. Writing_your_own_scenario](Writing_your_own_scenario.md).

### Initialize Method
In this method you can setup all parameters required for the scenario and its vehicles.
The initialize method is intended to setup all parameters required for the scenario and all vehicles. This includes e.g. set the desired location of a vehicle, its speed, parameters for other actors and define a timeout:
 
```
self._first_vehicle_location = 25
self._first_vehicle_speed = 10

self._other_actor_max_brake = 1.0
self._other_actor_stop_in_front_intersection = 20

self.timeout = timeout
```

### CreateBehavior method

This method should setup the behavior tree that contains the behavior of all
non-ego vehicles during the scenario. The behavior tree should use py_trees and
the atomic behaviors defined in _atomic_scenario_behavior.py_

### CreateTestCriteria method
This method setup all evaluation criteria for the scenario. The criteria are provided in the _atomic_scenario_criteria.py_ to analyze if a scenario was completed successfully or failed.

Criteria run continuously to monitor the state of a single actor, multiple
actors or environmental parameters. Hence, a termination is not required.

#### How to use the CreateTestCriteria method?

You can exchange in the function "_create_test_criteria(self)" the test criterion (e.g. CollisionTest()) through other criterion classes.
```
def _create_test_criteria(self):
    collision_criterion = CollisionTest(self.ego_vehicles[0])

    criteria.append(collision_criterion)
```

To make use of modifying the criterion and evaluate a scenario with them have a look at: [5. Record_your_test_case_and_evaluate_it](Record_your_test_case_and_evaluate_it.md).

In the following there are further criterion classes listed and described:

#### MaxVelocityTest
This class contains a test for maximum allowed velocity in m/s.
```
class MaxVelocityTest()
```

#### DrivenDistanceTest
This class checks if the actor's driven distance is more than a defined value (in meters).
```
class DrivenDistanceTest()
```

#### AverageVelocityTest
This class checks if the actor's average velocity is more than a defined value (in m/s).
```
class AverageVelocityTest()
```

#### CollisionTest
This class contains a test for collisions.
```
class CollisionTest()
```

#### ActorSpeedAboveThresholdTest
This test will fail if the actor has had its linear velocity lower than a specific value for a specific amount of time
```
class ActorSpeedAboveThresholdTest()
```

#### KeepLaneTest
This contains a test for keeping lane
```
class KeepLaneTest()
```

#### ReachedRegionTest
This class checks if the actor reaches a specified region
```
class ReachedRegionTest()
```

#### OffRoadTest
This class checks when an actor deviates from the driving lanes.
```
class OffRoadTest()
```

#### EndofRoadTest
This class checks when an actor has changed to a different road.
```
class EndofRoadTest()
```

#### OnSidewalkTest
This class checks if an actor has spent a specific time outside driving lanes.
```
class OnSidewalkTest()
```

#### OutsideRouteLanesTest
This class checks if the vehicle is either on a sidewalk or at a wrong lane
```
class OutsideRouteLanesTest()
```

#### WrongLaneTest
This class checks invasions to wrong direction lanes
```
class WrongLaneTest()
```

#### InRadiusRegionTest
This class checks if the actor is within a given radius of a specified region.
```
class InRadiusRegionTest()
```

#### InRouteTest
This class checks if the actor is never outside route. The actor can go outside of the route but only for a certain amount of distance.
```
class InRouteTest()
```

#### RouteCompletionTest
This class checks at which stage of the route is the actor at each tick.
```
class name()
```

#### RunningRedLightTest
This class checks if an actor is running a red light.
```
class RunningRedLightTest()
```

#### RunningStopTest
This class checks if an actor is running a stop sign.
```
class RunningStopTest()
```

## 2.) Modify the scenario configuration within its XML-File

You can find the corresponding XML-files of the scenario classes in the following path:
"/scenario_runner/srunner/examples".

To modify the scenarios configurations you can change the following parameters in the XML-File:

- Scenarios name, type and town
```
<scenario name="FollowLeadingVehicle_1" type="FollowLeadingVehicle" town="Town01">
```
- Ego Vehicle position (x, y, z, yaw) and its model
```
<ego_vehicle x="107" y="133" z="0.5" yaw="0" model="vehicle.lincoln.mkz2017" />
```
- Weather conditions
```
 <weather cloudiness="0" precipitation="0" precipitation_deposits="0" wind_intensity="0" sun_azimuth_angle="0" sun_altitude_angle="75" />
```
- Other actors, their position and model 
```
<other_actor x="264.4" y="16.3" z="-500" yaw="-179" model="vehicle.tesla.model3" />
```

 

## 3.) Next references
You can find how a Test Scenario is recorded, where it is stored and how it can be evaluated by replaying it or reading information from it:
[5. Record_your_test_case_and_evaluate_it](Record_your_test_case_and_evaluate_it.md)