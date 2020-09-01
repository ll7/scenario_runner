# Using the Scenario Runner for automated Tests

The following is an overview of the Project module from the chair of mechatronics from the University of Augsburg and shows how to write automated tests with the CARLA Scenario Runner.



## Quick Overview

1. [Excecute_the_supported scenarios](Execute_the_supported_scenarios.md)
2. [Execution_results_of_the_supported_scenarios](Execution_results_of_the_supported_scenarios.md)
3. [Writing_your_own_scenario](Writing_your_own_scenario.md) 
4. [Modify_an_existing_scenario](Modify_an_existing_scenario.md) 
5. [Record_your_test_case_and_evaluate_it](Record_your_test_case_and_evaluate_it.md) 
6. [Execute_a_test_case](Execute_an_automated_test_case.md)
7. [Running_route-based_scenarios_(similar_to_the_CARLA_AD_Challenge)_and_agent_evaluation](Running_route-based_scenarios_(similar_to_the_CARLA_AD_Challenge)_and_agent_evaluation.md)

#### Additional Work

a. [Basics_of_bash_script_automation](Basics_of_bash_script_automation.md)

b. [Steering_Wheel](Steering_Wheel.md)

## Overview

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

#### Additional Work

### [a. Basics_of_bash_script_automation](Basics_of_bash_script_automation.md)
The a-part describes Basics of Bash Scripts, shows further useful topics and how you can run multiple terminals from one terminal automated.

### [b. Steering_Wheel](Steering_Wheel.md)
The additional b-part describes how you can connect a Steering Wheel with the Carla Scenario Runner.