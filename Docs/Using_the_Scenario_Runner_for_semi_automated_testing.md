# Using the ScenarioRunner for (semi-)automated testing

The following is an overview of the project module from the chair of mechatronics from the University of Augsburg. The aim of the project module was to execute, investigate and use for test purposes the ScenarioRunner provided by CARLA.

## Preparation

This [guide](Docs/getting_scenariorunner.md) from the CARLA ScenarioRunner documentation describes how to download the ScenarioRunner and install it.

## Quick Overview

1. [Execute scenarios](Execute_Scenarios.md)
2. [Overview of scenarios](Overview_of_Scenarios.md)
3. [Create scenarios](Create_Scenarios.md) 
4. [Modify scenarios](Modify_Scenarios.md) 
5. [Record and evaluate scenarios](Record_and_evaluate_Scenarios.md) 
6. [(Semi-)automated tests](Semi_automated_tests.md)

#### Additional Work

&nbsp;&nbsp;&nbsp;a. [Basics of bash automation](Basics_of_bash_automation.md)\
&nbsp;&nbsp;&nbsp;b. [Basics of PyTrees](py_trees.md)\
&nbsp;&nbsp;&nbsp;b. [Steering wheel connection](Steering_Wheel.md)

#### Outlook

&nbsp;&nbsp;&nbsp;I.  [OpenScenario](openscenario.md)\
&nbsp;&nbsp;&nbsp;II. [Running Carla Container](run_scenario_runner_from_docker.md)

## Overview
This section gives an overview of the main topics of the project module. 

### [1. Excecute scenarios](Execute_Scenarios.md)
The first part describes the instructions how to execute the supported scenarios. Therein is shown how you have to prepare and a differentiation for the scenarios from OpenScenario.

### [2. Overview of scenarios](Overview_of_Scenarios.md)
The second part gives a detailed overview about the supported scenarios.

### [3. Create scenarios](Create_Scenarios.md)
The third part describes how to write your own scenario from scratch. Further it explains patterns of frequently used parameters and objects for these classes. Finally, it describes how to add the scenario configuration.

### [4. Modify scenarios](Modify_Scenarios.md)
The fourth part lists a lot of possibilities to modify a scenario, its behavior and its test criteria.

### [5. Record and evaluate scenarios](Record_and_evaluate_Scenarios.md)
The fifth part describes how you can record a scenario, where it can be stored and how it can be evaluated. Finally, it shows a further method to display the output of the test criteria.

### [6. (Semi-)automated tests](Semi_automated_tests.md)
The sixth part describes different ways to run scenarios (semi-)automated.

## Additional Work
The "Additional Work" part contains documentation that was not necessary for the actual project module and goes beyond the original project objective, but nevertheless provides useful pointers for further work.

### [a. Basics of bash automation](Basics_of_bash_automation.md)
The a-part describes basics of bash scripts, shows further useful topics and how you can run multiple terminals from one terminal automated.

### [b. Basics of PyTrees](py_trees.md)
The b-part describes the background information of how you can create a behavior tree for the behavior of a scenario.

### [c. Steering wheel connection](Steering_Wheel.md)
The c-part describes how you can connect a Steering Wheel with the Carla ScenarioRunner.

## Outlook
The "Outlook" part includes "failed" work packages which were not examined in detail, as their results could not significantly advance the project objective. Nevertheless, they are included here for the sake of completeness.

### [I. OpenScenario](openscenario.md)
This part describes what OpenScenario is and why the format was not investigated further in the project module.

### [II. Running CARLA Container](run_scenario_runner_from_docker.md)
This part describes what docker is, how you can install it and pull the CARLA image 0.9.9. Unfortunately, we got an error by executing the docker image which we couldn't solve. That's why till now it is just an Outlook for further work.