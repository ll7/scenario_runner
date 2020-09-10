# Modify scenarios
This part follows on from the previous [part](Create_Scenarios.md), which described "what" possibilities there are for creating a scenario. Therefore this part answers the question "how" these possibilities can be used to modify an (existing) scenario.

The great difficulty in modifying a scenario is that a scenario is executed once by scenario_runner.py and is therefore already "precompiled". The behaviour of the scenario is therefore already defined by manual_control.py in the form of a py_tree data structure before the actual Ego Vehicle is executed, which is why dynamic reaction to traffic events is only possible to a limited extent. 

In general it is possible to modify a scenario class according to the same scheme as it is created ([3. Create scenarios](Create_Scenarios.md)). Therefore we distinguish between the following three methods in the modification possibilities.
1. Initalize(),
2. CreateBehavior()
3. and CreateTestCriteria()


## 1.) Initialize Method
This modification option is useful if you want to change the scenario initially,e.g. set the desired location of a vehicle, its speed, parameters for other actors and define a timeout. If you want to access traffic situations during the scenario, it is better to adjust the behaviour method in section 2) below.

#### Example 1.1: setup parameters

Modification examples of setup parameters required for the scenario and its vehicles:
 
```
#Modify the spawn location of the Ego_Vehicle
self._first_vehicle_location = 25

#Modify the speed of the first vehicle
self._first_vehicle_speed = 10

#Modify the max brake of the other actors
self._other_actor_max_brake = 1.0

#Modify the distance when other actors have to stop in front of an intersection
self._other_actor_stop_in_front_intersection = 20

#Modify the timeout of the scenario
self.timeout = timeout
```

#### Example 1.2: change traffic light

Modification example of a specific scenario (SignalizedJunctionLeftTurn) where we changed the light from the next traffic light initially.

```
1 self._traffic_light = CarlaDataProvider.get_next_traffic_light(self.ego_vehicles[0], False)
2        traffic_light_other = CarlaDataProvider.get_next_traffic_light(self.other_actors[0], False)
3
4 self._traffic_light.set_state(carla.TrafficLightState.Green)
5 self._traffic_light.set_green_time(self.timeout)
```

Replace line 4 and 5 with the following lines to set the traffic light in front of the ego vehicle on red light initially.

```
1 self._traffic_light.set_state(carla.TrafficLightState.Red)
2 self._traffic_light.set_red_time(self.timeout)
```

### 2.) CreateBehavior method

This method processes the behaviour of the scenario through a behaviour tree. The behavior tree should use [py_trees](py_trees.md) and the atomic behaviors defined in _atomic_scenario_behavior.py_ and _atomic_trigger_conditions.py_ to influence the scenarios.

Further detailed background information about the syntax and usage on py_trees can be found under [py_trees](py_trees.md).

The two possibilities already mentioned are how to modify the behaviour:

- _atomic_scenario_behavior.py_
- _atomic_trigger_conditions.py_

What these two scripts contain in terms of modification possibilities has already been discussed in chapter [3. Writing_your_own_scenario](Create_Scenarios.md). Now it will be explained how they can be used.

For simplification, five steps of use are proposed in the following and presented using the example of "SignalizedJunctionRightTurn".

#### Five steps of use

1. Create a py_tree structure

2. Create an atomic object

3. Add the atomic object to the py_tree structure

4. Create the final behavior tree as a py_tree composite structure

5. Add the first created py_tree structure to the behavior tree

#### Example: SignalizedJunctionRightTurn
We used the atomic scenario behavior "TrafficLightManipulator" from _atomic_behaviors.py_ to manipulate the traffic lights around the ego vehicle. 

This is done by setting 2 of the traffic light at the intersection to green with some complex precomputation.

In the following a section of the modified code is shown:

```
# Create a Parallel py_tree structure
move_actor_parallel = py_trees.composites.Parallel(policy=py_trees.common.ParallelPolicy.SUCCESS_ON_ONE)

# Create an atomic Object manipulate_traffic_light with a atomic behavior method to manipulate the traffic lights around the ego vehicle
manipulate_traffic_light = TrafficLightManipulator(self.ego_vehicles[0], "S7right")

# Add the atomic objects to the py_tree parallel structure
move_actor_parallel.add_child(manipulate_traffic_light)

# Create the behavior tree as a py_tree composite sequence structure
sequence = py_trees.composites.Sequence()

# Add the parallel structure to the composite sequence structure
sequence.add_child(move_actor_parallel)
```

To understand: "move_actor_parallel" and the "behavior tree" are already in the original code. Just another atomic object "manipulate_traffic_light" was created and added to the already existing py_tree structure "move_actor_parallel". Which in turn was finally inserted into the already existing behavior tree.


## 3.) CreateTestCriteria method
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

In the following there are three instructions listed how you can make use of modifying the criterion to evaluate your scenarios.

Per default there is the criterion "CollisionTest" in the scenario class "FollowLeadingVehicle" implemented. For a better understanding we compare this during the instructions with the new added criterion "DrivenDistanceTest".

### Example: Add the criterion "DrivenDistanceTest"

#### 1 Select the criterion and the desired scenario
First you have to look which criterion you want to add to your desired scenario. In this example we choose the scenario "FollowLeadingVehicle" with the criterion "DrivenDistanceTest", which checks if the actor's driven distance is more than a defined value (in meters).

#### 2 Add the imports in your selected scenario
Second you have to import to your selected scenario (e.g. FollowLeadingVehicle) the criterion "DrivenDistanceTest".
```
from srunner.scenariomanager.scenarioatomics.atomic_criteria import CollisionTest
from srunner.scenariomanager.scenarioatomics.atomic_criteria import DrivenDistanceTest
```

#### 3 Modify the _create_test_criteria() function
Third you have to modify the following criteria function in the selected scenario class.

In this example we added the lines 8 and 9 analogous to the lines 5 and 6 with the small difference that the DrivenDistanceTest() class in line 8 require an additional argument.

For the information which arguments you have to add to your choosen criterion just have a look in the _atomic_scenario_criteria.py_ script. 

```
1 def _create_test_criteria(self):
2
3    criteria = []
4
5    collision_criterion = CollisionTest(self.ego_vehicles[0])
6    criteria.append(collision_criterion)
7
8    distance_criterion = DrivenDistanceTest(self.ego_vehicles[0],1)
9    criteria.append(distance_criterion)
10
11   return criteria
```


## 4.) Modify the scenario configuration within its XML-File

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

 

## 5.) Next references
You can find how to record an evaluate a scenario [here](Record_and_evaluate_Scenarios.md).