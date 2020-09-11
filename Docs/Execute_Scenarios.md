# Execute scenarios

This documentation describes how to run the scenarios in python and OpenScenario format after following the installation guide from CARLA, which can be found [here](Docs/getting_scenariorunner.md) in detail.

## 1.) Preparation

#### Start the Carla Server
Move to the the Directory "CARLA_0.9.9" and execute the following command in the Terminal:
```
./CarlaUE4.sh
```

#### Get to know useful parameters of the ScenarioRunner
To execute the ScenarioRunner commands you have to move to the Directory "scenario_runner".
Before starting the ScenarioRunner get aware of the "--help" parameter, it could be useful.
```
python scenario_runner.py --help
```
Especially the "--output" is very useful to provide results on stdout after the execution of a scenario. For more information have a look in the chapter [5. Record and evaluate scenarios](Record_and_evaluate_Scenarios.md).

#### List the supported scenarios
With this command you get an overview about the supported scenarios you can execute.
```
python scenario_runner.py --list
```

## 2.) Execute the ScenarioRunner for python
This part describes how you can execute the ScenarioRunner for the scenarios written in python.

#### Start the ScenarioRunner with a supported scenario
You can replace "FollowLeadingVehicle_1" with any other scenario, which was listed with the command before. The parameter "--reloadWorld" is optional and not necessary if you already in the right world. Be aware that you are in the "scenario_runner" directory when you want to execute this command.
```
python scenario_runner.py --scenario FollowLeadingVehicle_1 --reloadWorld
```

After that command the scenario spawns the required objects (e.g. cars). You have to navigate in the world to the scenario to observe it. Use your mouse by pressing the left button to change your view. In Addition you can use "W", "A", "S", "D" to move.

#### Open the manual control to start the ScenarioRunner
With this command another window opens with the view from the spawned car.
```
python manual_control.py
```
Now you have two options to execute the ScenarioRunner with the supported scenario. 

#### Option 1: Execute the scenario by the autopilot
You can press "P" in the pygame window to execute the scenario with the autopilot.


#### Option 2: Execute the scenario by yourself
Use the keyboard buttons which are shown in the terminal after you executed the "manual_control.py" command to execute the scenario by yourself.


## 3.) Excecute the scenario with OpenScenario
This part describes how you can execute the ScenarioRunner for the scenarios written in OpenScenario. For more information about OpenScenario have a look [here](openscenario.md).

#### Start the ScenarioRunner with a supported scenario
You can also used the prepared Scenarios from OpenScenario by running this command instead of "python scenario_runner.py --scenario FollowLeadingVehicle_1 --reloadWorld".

```
python scenario_runner.py --openscenario srunner/examples/FollowLeadingVehicle.xosc
```

## 4.) Next references
You can find an detailed overview of the supported scenarios 
[here](Overview_of_Scenarios.md).