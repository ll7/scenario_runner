# Instruction how to execute the supported Scenarios

You can find the detailed description of the supported scenarios here:
[List of Supported Scenarios](list_of_scenarios.md).

##I.) Preparation

### Start the Carla Server
```
./CarlaUE4.sh
```

###Get to know useful parameters of the Scenario Runner
Before starting the scenario runner get aware of the "--help" parameter, it could be useful.
```
python scenario_runner.py --help
```
Especially the "--output" is very useful to provide results on stdout after the execution of a scenario.
###List the supported scenarios
With this command you get an overview about the supported scenarios you can execute.
```
python scenario_runner.py --list
```

##II.) Execute the Scenario Runner

###Start the Scenario Runner with a supported Scenario
You can replace "FollowLeadingVehicle_1" with any other scenario, which was listed with the command before. The parameter "--reloadWorld" is optional and not necessary if you already in the right world.
```
python scenario_runner.py --scenario FollowLeadingVehicle_1 --reloadWorld
```

After that command the scenario spawns the required objects (e.g. cars). You have to navigate in the world to the scenario to observe it. Use your mouse by pressing the left button to change your view. In Addition you can use "W", "A", "S", "D" to move.

###Open the Manual Control to start the Scenario Runner
With this command another window opens with the view from the spawned car.
```
python manual_control.py
```
Now you have two options to execute the scenario runner with the supported scenario. 

###Option 1: Execute the Scenario by the Autopilot
You can press "P" in the pygame window to execute the scenario with the Autopilot.


###Option 2: Execute the Scenario by yourself
Use the keyboard buttons which are shown in the terminal after you executed the "manual_control.py" command to execute the scenario by yourself.


##III.) Excecute the Scenario with OpenScenario

###Start the Scenario Runner with a supported Scenario
You can also used the prepared Scenarios from OpenScenario by running this command instead of "python scenario_runner.py --scenario FollowLeadingVehicle_1 --reloadWorld".
```
python scenario_runner.py --openscenario srunner/examples/FollowLeadingVehicle.xosc
```


##IV.) Evaluate the output of the executed Scenario
As mentioned in Section I.) you can use the parameter "--output" by executing you scenario the get an evaluation output on terminal.
```
python scenario_runner.py --scenario FollowLeadingVehicle_1 --reloadWorld --output
```
There you can see an example for an output of an scenario which failed ("Result: FAILURE") because we manually created a collision with the other vehicle.
```
Scenario: FollowVehicle --- Result: FAILURE
Start time: 2020-05-28 14:35:17
End time: 2020-05-28 14:36:17
Duration: System Time 60.08s --- Game Time 60.02s
Ego vehicle:  Actor(id=300, type=vehicle.lincoln.mkz2017)
Other actors: Actor(id=301, type=vehicle.nissan.patrol); 


                Actor             |            Criterion           |   Result    | Actual Value | Expected Value 
-----------------------------------------------------------------------------------------------------------------
         lincoln.mkz2017 (id=300) |         CheckCollisions (Req.) |     FAILURE |         1.00 |         0.00 
                                  |                       Duration |     FAILURE |        60.02 |        60.00 
```

##V.) Next references
You can find the execution results of the supported scenarios here: 
[execution results of supported scenarios](execution_results_of_the_supported_scenarios.md).