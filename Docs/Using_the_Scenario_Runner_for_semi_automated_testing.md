# Using the ScenarioRunner for (semi-)automated testing

The following is an overview of the project module from the chair of mechatronics from the University of Augsburg designed in summer term 2020. 

## Goal of the project module

The goal of the project module was to execute, investigate and use for test purposes the ScenarioRunner provided by CARLA.

## Preparation

This [guide](Docs/getting_scenariorunner.md) from the CARLA ScenarioRunner documentation describes how to download the ScenarioRunner and install it.

## Quick overview

1. [Execute scenarios](Execute_Scenarios.md)
2. [Overview of scenarios](Overview_of_Scenarios.md)
3. [Create scenarios](Create_Scenarios.md) 
4. [Modify scenarios](Modify_Scenarios.md) 
5. [Record and evaluate scenarios](Record_and_evaluate_Scenarios.md) 
6. [(Semi-)automated tests](Semi_automated_tests.md)

#### Additional work

&nbsp;&nbsp;&nbsp;a. [Basics of bash automation](Basics_of_bash_automation.md)\
&nbsp;&nbsp;&nbsp;b. [Basics of PyTrees](py_trees.md)\
&nbsp;&nbsp;&nbsp;b. [Steering wheel connection](Steering_Wheel.md)

#### Outlook

&nbsp;&nbsp;&nbsp;I.  [OpenScenario](openscenario.md)\
&nbsp;&nbsp;&nbsp;II. [Running Carla Container](run_scenario_runner_from_docker.md)

## Main work packages
This section gives an overview of the main work packages of the project module. 

### [1. Excecute scenarios](Execute_Scenarios.md)
The first part describes describes how to run the scenarios in python and OpenScenario format after following the installation guide from CARLA.

### [2. Overview of scenarios](Overview_of_Scenarios.md)
The second part gives a detailed overview about the supported scenarios written in python and OpenScenario.

### [3. Create scenarios](Create_Scenarios.md)
The third part describes "what" you can use to write your own scenario from scratch. Further it explains patterns of frequently used parameters and objects for these classes. Finally, it describes how to add the scenario configuration.

### [4. Modify scenarios](Modify_Scenarios.md)
The fourth part answers the question "how" the possibilities to create a scenario from the previous chapter can be used to modify an (existing) scenario.

### [5. Record and evaluate scenarios](Record_and_evaluate_Scenarios.md)
The fifth part describes how you can record a scenario, where it can be stored and how it can be evaluated. Finally, it shows a further method to display the output of the test criteria.

### [6. (Semi-)automated tests](Semi_automated_tests.md)
The sixth part describes  options of running your scenario runner (semi-)automated.

## Additional work
The "Additional work" part contains documentation that was not necessary for the actual project module and goes beyond the original project objective, but nevertheless provides useful pointers for further work.

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