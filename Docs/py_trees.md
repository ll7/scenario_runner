# Py_trees behavior tree

To create a behavior tree for the behavior of a scenario you can use the composite data structure from py_trees.

Composites are the decision makers of a behaviour tree. They are responsible for shaping the branches.

A composite data structure can take on three different forms:

![](img/Images%20for%20execution%20results/py_tree.png)

Composite behaviours typically manage children and apply some logic to the way they execute and return a result, but generally don’t do anything themselves.

- Sequence: execute children sequentially 

- Selector: select a path through the tree, interruptable by higher priorities

- Parallel: manage children concurrently

For more detailed information about the syntax have a look [here](https://py-trees.readthedocs.io/en/devel/composites.html).

An application for the ScenarioRunner is shown in the following section

## 1.) Use of py_tree composite structure sequence and parallel
In the following the two structures sequence and parallel are used and explained using the example SignalizedJunctionRightTurn.

#### Example: Extract from the behavior method of the scenario SignalizedJunctionRightTurn
The idea is to create a "plan" of waypoints. This plan is used to create atomic behavior objects which are aggregated to py_tree branch structures. Finally these branches are added to the behaviour tree as children and the behaviour is defined.

```
# Selecting straight path at intersection
target_waypoint = generate_target_waypoint(CarlaDataProvider.get_map().get_waypoint(self.other_actors[0].get_location()), 0)

# Generating waypoint plan till next intersection
plan = []
wp_choice = target_waypoint.next(1.0)
while not wp_choice[0].is_intersection:
    target_waypoint = wp_choice[0]
    plan.append((target_waypoint, RoadOption.LANEFOLLOW))
    wp_choice = target_waypoint.next(1.0)

# Create an atomic Object move_actor with a atomic behavior method to follow waypoints while maintaining a given speed
move_actor = WaypointFollower(self.other_actors[0], self._target_vel, plan=plan)

# Create an atomic Object waypoint_follower_end with a atomic triger condition to determine the distance to a fixed location of the scenario
waypoint_follower_end = InTriggerDistanceToLocation(self.other_actors[0], plan[-1][0].transform.location, 10)

# Create a Parallel py_tree structure
move_actor_parallel = py_trees.composites.Parallel(policy=py_trees.common.ParallelPolicy.SUCCESS_ON_ONE)

# Add the atomic objects to the py_tree parallel structure
move_actor_parallel.add_child(move_actor)
move_actor_parallel.add_child(waypoint_follower_end)

# Create the behavior tree as a py_tree composite sequence structure
sequence = py_trees.composites.Sequence()

# Add the parallel structure to the composite sequence structure
sequence.add_child(move_actor_parallel)
```