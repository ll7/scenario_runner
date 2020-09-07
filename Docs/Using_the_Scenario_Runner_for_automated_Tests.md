# Using the Scenario Runner for automated Tests

The following is an overview of the Project module from the chair of mechatronics from the University of Augsburg and shows how to write automated tests with the CARLA Scenario Runner.

## Preparation

The documentation [Getting started](Docs/getting_scenariorunner.md) from the original ScenarioRunner describes how to download the ScenarioRunenr and install it.

## Quick Overview

1. [Excecute_the_supported scenarios](Execute_the_supported_scenarios.md)
2. [Execution_results_of_the_supported_scenarios](Execution_results_of_the_supported_scenarios.md)
3. [Writing_your_own_scenario](Writing_your_own_scenario.md) 
4. [Modify_an_existing_scenario](Modify_an_existing_scenario.md) 
5. [Record_your_test_case_and_evaluate_it](Record_your_test_case_and_evaluate_it.md) 
6. [Execute_a_test_case](Execute_an_automated_test_case.md)
7. [Running_route-based_scenarios_(similar_to_the_CARLA_AD_Challenge)_and_agent_evaluation](Running_route-based_scenarios_(similar_to_the_CARLA_AD_Challenge)_and_agent_evaluation.md)

#### Additional Work

&nbsp;&nbsp;&nbsp;a. [Basics_of_bash_script_automation](Basics_of_bash_script_automation.md)\
&nbsp;&nbsp;&nbsp;b. [Steering_Wheel](Steering_Wheel.md)


#### Outlook

&nbsp;&nbsp;&nbsp;I. [OpenScenario](openscenario.md)\
&nbsp;&nbsp;&nbsp;II. [ROS](Steering_Wheel.md)\
&nbsp;&nbsp;&nbsp;III. [Docker Image](Steering_Wheel.md)

## Overview
The "Overview" part gives an overview of the main topics of the project module. The overall goal of the module was to be able to use the Scenario Runner at the end to run scenarios automatically.

### [1. Excecute_the_supported scenarios](Execute_the_supported_scenarios.md)
The first Part describes the Instructions how to execute the supported Scenarios. Therein is shown how you have to prepare and a differentiation for the Scenarios from OpenScenario.

### [2. Execution_results_of_the_supported_scenarios](Execution_results_of_the_supported_scenarios.md)
The second Part describes the Execution results of the supported scenarios. Further, it gives an overview about the supported scenarios and differentiated as well as the first part with OpenScenario.

### [3. Writing_your_own_scenario](Writing_your_own_scenario.md)
The third Part describes how to write your own scenario from scratch. It explains how to create an empty python class and how you have to fill these class. Finally, it describes how to add the scenario configuration.

### [4. Modify_an_existing_scenario](Modify_an_existing_scenario.md)
The fourth part lists everything I have access to (e.g. traffic lights, agents, position, etc.) and how I can use it to modify an existing scenario.

### [5. Record_your_test_case_and_evaluate_it](Record_your_test_case_and_evaluate_it.md)
The fifth part briefly describes how the automated tests can be recorded and evaluated.

### [6. Execute_an_automated_test_case](Execute_an_automated_test_case.md)
The sixth part describes how I can run a test case automatically by running multiple scenarios in a test and evaluating them against certain metrics.

### [7. Running_route-based_scenarios_(similar_to_the_CARLA_AD_Challenge)_and agent_evaluation](Running_route-based_scenarios_(similar_to_the_CARLA_AD_Challenge)_and_agent_evaluation.md)
The seventh part describes how you can run a route based scenario and set up an agent for evaluation.

## Additional Work
The "Additional Work" part contains documentation that was not necessary for the actual project module and goes beyond the original project objective, but nevertheless provides useful pointers for further work.

### [a. Basics_of_bash_script_automation](Basics_of_bash_script_automation.md)
The a-part describes Basics of Bash Scripts, shows further useful topics and how you can run multiple terminals from one terminal automated.

### [b. Steering_Wheel](Steering_Wheel.md)
The b-part describes how you can connect a Steering Wheel with the Carla Scenario Runner.

### [c. Docker Image](run_scenario_runner_from_docker.md)
The c-part describes how you can run the scenario run from a docker image.

## Outlook
The "Outlook" part includes "failed" work packages which were not examined in detail, as their results could not significantly advance the project objective. Nevertheless, they are included here for the sake of completeness.

### [I. OpenScenario](Basics_of_bash_script_automation.md)
This part describes what OpenScenario is and why the format was not investigated further in the project module.

### [II. ROS](ros.md)
This part gives an Outlook how you can use ROS with the Scenario Runner.
