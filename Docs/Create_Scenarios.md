# Create scenarios

This tutorial is based on the CARLA [documentation](https://github.com/carla-simulator/scenario_runner/blob/master/Docs/creating_new_scenario.md) but is extended by section 2.) patterns of frequently used parameters and objects for these classes. This answers the question "what" can be used to create a scenario. To prepare for the following section, "how" the scenarios can be modified. Finally, it describes how to add the scenario configuration.

## 1.) Create a Scenario Class
Go to the Scenarios folder and create a new Python class with the name
_NewScenario_ in a new Python file (_new_scenario.py_). The class should be
derived from the _BasicScenario_ class.

The class basically consists of the three methods:
- Intitialize()
- CreateBehavior()
- CreateTestCriteria()

### Initialize Method
The initialize method is intended to setup all parameters required
for the scenario and all vehicles. This includes selecting the correct vehicles,
spawning them at the correct location, etc. To simplify this, you may want to
use the _setup_vehicle()_ function defined in basic_scenario.py

### CreateBehavior method
This method should setup the behavior tree that contains the behavior of all
vehicles during the scenario. The behavior tree should use py_trees and
the atomic behaviors defined in _atomic_scenario_behavior.py_

### CreateTestCriteria method
This method should setup a list with all evaluation criteria for the scenario.
The criteria should be based on the atomic criteria defined in
_atomic_scenario_criteria.py_.

As a result, the class should look as follows:

   ```
   class NewScenario(BasicScenario):
       """
       Some documentation on NewScenario
       :param world is the CARLA world
       :param ego_vehicles is a list of ego vehicles for this scenario
       :param config is the scenario configuration (ScenarioConfiguration)
       :param randomize can be used to select parameters randomly (optional, default=False)
       :param debug_mode can be used to provide more comprehensive console output (optional, default=False)
       :param criteria_enable can be used to disable/enable scenario evaluation based on test criteria (optional, default=True)
       :param timeout is the overall scenario timeout (optional, default=60 seconds)
       """

       # some ego vehicle parameters
       # some parameters for the other vehicles

       def __init__(self, world, ego_vehicles, config, randomize=False, debug_mode=False, criteria_enable=True,
                    timeout=60):
           """
           Initialize all parameters required for NewScenario
           """

           # Call constructor of BasicScenario
           super(NewScenario, self).__init__(
             name="NewScenario",
             ego_vehicles,
             config,
             world,
             debug_mode,
             criteria_enable=criteria_enable))


       def create_behavior(self):
           """
           Setup the behavior for NewScenario
           """

       def create_test_criteria(self):
           """
           Setup the evaluation criteria for NewScenario
           """
   ```

## 2.) Patterns of frequently used parameters and objects 

By looking more closely and comparing the scenarios, different patterns of frequently used parameters and objects can be identified. These are presented below for the three methods introduced above:

- Initialize()
- CreateBehavior()
- CreateTestCriteria()

### 2.1) Initialize Method
This method setup parameters required for the scenario initially.

In the following a selection of frequently used parameters from the scenarios are presented:

```
#Determine the timout of the scenario in seconds
self.timeout = timeout

#Get the current map
self._map = CarlaDataProvider.get_map()

#Get the as reference the waypoints from the current map
self._reference_waypoint = self._map.get_waypoint(config.trigger_points[0].location)

#determine the distance the vehicle has to drive
self._vehicle_distance = 100

#Determine the maximal steer and throttle parameters
self._ego_vehicle_max_steer = 0.0
self._ego_vehicle_max_throttle = 1.0

#Set the velocity and its delta of the Ego Vehicle
self._velocity = 40
self._delta_velocity = 10

#Determine the distance to trigger an atomic trigger condition
self._trigger_distance = 30

#Determine the spawn location of the ego vehicle
self._first_vehicle_location = 25

#Determine the speed of the first vehicle
self._first_vehicle_speed = 10

#Set the distance when other actors have to stop in front of an intersection
self._other_actor_stop_in_front_intersection = 20
```

### 2.2) CreateBehavior method
This method setup the behavior tree that contains the behavior of all vehicles during the scenario.

#### _atomic_scenario_behaviors.py_
This module provides all atomic scenario behaviors required to realize complex, realistic scenarios such as "follow a leading vehicle", "lane change", etc.

In the following a selection of the classes from _atomic_scenario_behaviors.py_ are presented from which objects of behavior can be generated.

##### ChangeActorTargetSpeed
Change the target speed for an actor controller.
```
class ChangeActorTargetSpeed()
```

##### ChangeActorWaypoints
Change the waypoints for an actor controller.
```
class ChangeActorWaypoints()
```

##### AccelerateToVelocity
The controlled traffic participant will accelerate with _throttle_value_ until reaching a given _target_velocity_.
```
class AccelerateToVelocity()
```

##### KeepVelocity
Its a behavior to keep the provided velocity
```
class KeepVelocity()
```

##### StopVehicle
The controlled traffic participant will decelerate with _bake_value_ until reaching a full stop.
```
class StopVehicle()
```

##### SyncArrival
This class contains an atomic behavior to set velocity of actor so that it reaches location at the same time as actor_reference.
```
class SyncArrival()
```

##### AddNoiseToVehicle
This class contains an atomic jitter behavior. To add noise to steer as well as throttle of the vehicle.
```
class AddNoiseToVehicle()
```

##### WaypointFollower
This is an atomic behavior to follow waypoints while maintaining a given speed.

```
class WaypointFollower()
```

##### TrafficLightManipulator
Atomic behavior that manipulates traffic lights around the ego_vehicle to trigger scenarios.
```
class TrafficLightManipulator()
```

#### _atomic_trigger_conditions.py_
This module provides all atomic scenario behaviors that reflect trigger conditions to either activate another behavior, or to stop another behavior.

In the following a selection of the classes from _atomic_trigger_conditions.py_ are presented from which objects of behavior can be generated.

##### TriggerVelocity
Atomic containing a comparison between an actor's speed and a reference one.
```
class TriggerVelocity()
```

##### TriggerAcceleration
Atomic containing a comparison between an actor's acceleration and a reference one.
```
class TriggerAcceleration()
```

##### InTriggerDistanceToVehicle
This class contains the trigger distance (condition) between to actors of a scenario.
```
class InTriggerDistanceToVehicle()
```

##### InTriggerDistanceToNextIntersection
This class contains the trigger (condition) for a distance to the next intersection of a scenario.
```
class InTriggerDistanceToNextIntersection()
```

##### InTimeToArrivalToLocation
This class contains a check if a actor arrives within a given time at a given location
```
class InTimeToArrivalToLocation()
```

##### DriveDistance
This class contains an atomic behavior to drive a certain distance.
```
class DriveDistance()
```

##### WaitEndIntersection
Atomic behavior that waits until the vehicles has gone outside the junction. If currently inside no intersection, it will wait until one is found.
```
class WaitEndIntersection()
```

### 2.3) CreateTestCriteria method
As already mentioned this method setup a list with all evaluation criteria for the scenario.

In the following the classes from _atomic_scenario_criteria.py_ are presented from which objects of evaluation criteria can be generated.

##### MaxVelocityTest
This class contains a test for maximum allowed velocity in m/s.
```
class MaxVelocityTest()
```

##### DrivenDistanceTest
This class checks if the actor's driven distance is more than a defined value (in meters).
```
class DrivenDistanceTest()
```

##### AverageVelocityTest
This class checks if the actor's average velocity is more than a defined value (in m/s).
```
class AverageVelocityTest()
```

##### CollisionTest
This class contains a test for collisions.
```
class CollisionTest()
```

##### ActorSpeedAboveThresholdTest
This test will fail if the actor has had its linear velocity lower than a specific value for a specific amount of time
```
class ActorSpeedAboveThresholdTest()
```

##### KeepLaneTest
This contains a test for keeping lane
```
class KeepLaneTest()
```

##### ReachedRegionTest
This class checks if the actor reaches a specified region
```
class ReachedRegionTest()
```

##### OffRoadTest
This class checks when an actor deviates from the driving lanes.
```
class OffRoadTest()
```

##### EndofRoadTest
This class checks when an actor has changed to a different road.
```
class EndofRoadTest()
```

##### OnSidewalkTest
This class checks if an actor has spent a specific time outside driving lanes.
```
class OnSidewalkTest()
```

##### OutsideRouteLanesTest
This class checks if the vehicle is either on a sidewalk or at a wrong lane
```
class OutsideRouteLanesTest()
```

##### WrongLaneTest
This class checks invasions to wrong direction lanes
```
class WrongLaneTest()
```

##### InRadiusRegionTest
This class checks if the actor is within a given radius of a specified region.
```
class InRadiusRegionTest()
```

##### InRouteTest
This class checks if the actor is never outside route. The actor can go outside of the route but only for a certain amount of distance.
```
class InRouteTest()
```

##### RouteCompletionTest
This class checks at which stage of the route is the actor at each tick.
```
class name()
```

##### RunningRedLightTest
This class checks if an actor is running a red light.
```
class RunningRedLightTest()
```

##### RunningStopTest
This class checks if an actor is running a stop sign.
```
class RunningStopTest()
```


## 3.) Adding the scenario configuration
Finally the scenario configuration should be added to the examples/ folder. If you
extend an already existing scenario module, you can simply extend the corresponding
XML, otherwise add a new XML file. In this case you can use any of the existing
XML files as blueprint.

If you want to add multiple ego vehicles for a scenario, make sure that they use different
role names, e.g.
```
    <scenario name="MultiEgoTown03" type="FreeRide" town="Town03">
        <ego_vehicle x="207" y="59" z="0" yaw="180" model="vehicle.lincoln.mkz2017" rolename="hero"/>
        <ego_vehicle x="237" y="-95.0754252474" z="0" yaw="90" model="vehicle.tesla.model3" rolename="hero2"/>
    </scenario>
```

## 4.) Next references
You can find how to modify a scenario [here](Modify_Scenarios.md).