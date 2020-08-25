# Execute an automated test case

This documentation describes how you can run a test case automatically by running multiple scenarios in a test and evaluating them against certain metrics.

## I.)  Running all scenarios of one scenario class
It is also possible to execute a sequence of scenarios, that belong to the same class, e.g. the "FollowLeadingVehicle" class.

```
python scenario_runner.py --scenario group:<scenario-class>
```

Example:
```
python scenario_runner.py --scenario group:FollowLeadingVehicle
```

Then the scenarios of the selected class (e.g. FollowLeadingVehicle) are executed. After finishing a scenario the manual_control.py script must be restarted again and again. The scenarios of the selected class are automatically counted up and executed.

```
python manual_control.py
```

## II.) Next references
You can find "how to run a route based scenario (similar to CARLA AD Challenge) and set up an agent for evaluation".
[7. Running_route-based_scenarios_(similar_to_the_CARLA_AD_Challenge)_and_agent_evaluation](Running_route-based_scenarios_(similar_to_the_CARLA_AD_Challenge)_and_agent_evaluation.md)