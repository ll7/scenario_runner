# Examination of the scenario manager using the example of the scenario FollowLeadingVehicle
In this documentation the Scenario Manager will be examined using the example Scenarios FollowLeadingVehicle. Furthermore, it is shown how a traffic light scenario can be influenced on the basis of the Scenario Manager.

## 1.) Modules of the Scenario Manager
The scenario manager consists of several Python classes divided into 3 folder structures.

- actorcontrols (a)
- scenarioatomics (s)
- without assignment (w)

The abbreviations in curly brackets are used in the following section for better classification.

## 2.) Examination of the FollowLeadingVehicle scenario

In the scenario FollowLeadingVehicle the following submodules of the Scenario Manager are accessed which will be described in the following:

- carla_data_provider (a)
- atomic_behaviors (s)
- atomic_criteria (s)
- atomic_trigger_conditions (s)
- timer (w)

These were taken from the scenario's imports:
```
from srunner.scenariomanager.carla_data_provider import CarlaDataProvider
from srunner.scenariomanager.scenarioatomics.atomic_behaviors import (ActorTransformSetter,
                                                                      ActorDestroy,
                                                                      KeepVelocity,
                                                                      StopVehicle,
                                                                      WaypointFollower)
from srunner.scenariomanager.scenarioatomics.atomic_criteria import CollisionTest
from srunner.scenariomanager.scenarioatomics.atomic_criteria import DrivenDistanceTest
from srunner.scenariomanager.scenarioatomics.atomic_trigger_conditions import (InTriggerDistanceToVehicle,
                                                                               InTriggerDistanceToNextIntersection,
                                                                               DriveDistance,
                                                                               StandStill)
from srunner.scenariomanager.timer import TimeOut
```

#### carla_data_provider.py

This module provides all frequently used data from CARLA via local buffers to avoid blocking calls to CARLA.

The following is a selection of functions from these:
```
def get_velocity(actor): 
    "returns the absolute velocity for the given actor"

def get_location(actor): 
    "returns the location for the given actor"

def get_next_traffic_light(actor, use_cached_location=True): 
    "returns the next relevant traffic light for the provided actor"

def reset_lights(reset_params): 
    "Reset traffic lights"

def update_light_states(ego_light, annotations, states, freeze=False, timeout=1000000000): 
    "Update traffic light states"
```

#### atomic_behaviors.py
This module provides all atomic scenario behaviors required to realize complex, realistic scenarios such as "follow a leading vehicle", "lane change", etc.


#### atomic_criteria.py
This module provides all the possible criteria for evaluation use cases as described in [1.) Modify the class of a scenario](Modify_an_existing_scenario.md).

#### atomic_trigger_conditions
This module provides all atomic scenario behaviors that reflect
trigger conditions to either activate another behavior, or to stop
another behavior.

For example, such a condition could be "InTriggerRegion", which checks
that a given actor reached a certain region on the map, and then starts/stops
a behavior of this actor.
    
#### timer
This module provides access to the CARLA game time and contains a py_trees
timeout behavior using the CARLA game time


## 3.) An example to modify a traffic light scenario (SignalizedJunctionLeftTurn) with the Scenario Manager

- To DO
- Ampel auf grün setzen/ andere Zeit setzen



