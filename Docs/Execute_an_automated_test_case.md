# Execute an automated test case

This documentation describes three options of running your scenario runner automated.

The first option is how you can run multiple scenarios of one class successively automated. 

The second and third option is to run a fully- or an semi-automated scenario including recording and evaluation.

In addition the semi-automated approach is extended to run a list of scenarios automated.

Finally, the penultimate section briefly explains why a semi-automated approach is preferred over an automated approach.

## I.)  Running all scenarios of one scenario class
It is possible to execute a sequence of scenarios, that belong to the same class, e.g. the "FollowLeadingVehicle" class.

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

## II.) Running an fully-automated Test Scenario including recording and evaluation
To run a fully-automated Test scenario we provide a bash script that executes 
- (1) the Carla Server, 
- (2) the Scenario Runner,
- (3) the Manual Control for a Steering Wheel ([Steering_Wheel.md](Steering_Wheel.md)) and
- (4) the Recording of a Scenario.

Navigate to the following directory: 
```
/home/carlaws19/scenario_runner
```
Then execute the following script:
```
bash scenario_runner_with_carla.sh
```

The script in detail:
```
#!/bin/bash
echo "Start the Carla Server, the Scenario Runner, the Manual Control for Steering Wheel and the Record"

#1) Start the Carla Server
/home/carlaws19/CARLA_0.9.9/CarlaUE4.sh &

#2) Start the Scenario Runner
python scenario_runner.py --scenario FollowLeadingVehicle_1 --output --reloadWorld &

#3) Start the Manual Control for Steerin Wheel
python manual_control_steering_wheel.py &

#4) Optional Record the Scenario
python /home/carlaws19/CARLA_0.9.9/PythonAPI/examples/start_recording.py -f "FollowLeadingVehicle_1.log" -n "0"
```


## III.) Running an semi-automated Test Scenario including recording and evaluation
We call this third option semi-automated, because you have to start the carla Server (as known) separately.

So After starting the Carla Server navigate to the following path:
```
/home/carlaws19/scenario_runner/scenario_runner_with_carla.sh
```
In Contrast you have to execute this file with two additional arguments
- The first argument $1 is the desired scenario, e.g. FollowLeadingVehicle_1
- The second argument $2 (true or false) defines if you want to record it or not. It will be saved with the name of the first argument as a "log"-file.

Of course, this possibility could also be built into the fully-automated script mentioned in paragraph II.).

Then you can execute the following script from the scenario runner directory:
```
scenario_runner.sh <param1> <param2>
```

The Script in detail:
```
#!/bin/bash
#1) Start the Scenario Runner
echo "The $1 scenario will be executed"
python scenario_runner.py --scenario $1 --output --reloadWorld &

#2) Start the Manual Control for Steerin Wheel
echo "The manual control will be executed"
python manual_control_steering_wheel.py &

#3) Optional Record the Scenario
if $2; then
    echo "The file will be recorded"
    python /home/carlaws19/CARLA_0.9.9/PythonAPI/examples/start_recording.py -f "$1.log" -n "0"
else
    echo "The file will not be recorded"
fi
```

##IV.) Running a list of multiple Scenarios with the semi-automated approach
In addition to the previous semi-automated approach, we are extending it to be able to run a list of scenarios semi-automatically.

First the Carla server must be started again separately.

Then you just have to execute the bash script:

```
bash automated_scenario_runner.sh <param>
```
The parameter placeholder "param" can be replaced with a parameter (e.g. a number) in command line to assign the execution to a certain person.

This bash script in turn executes the bash script "scenario_runner.sh" introduced in section III.)

The difference is that it holds a list "listScenarios" in which the desired scenarios are declared.

In Addition the script executes the "scneario_runner.sh" with four parameters instead of two.

1. The first is the scenario_name from the list "listScenarios"
2. The second is per default "true" and determines if the scenario will be recorded or not
3. The third is a count variable for the scenarios if you want to the test the same scenario 2 times in the same execution
4. The fourth is an additional argument from command line to count the person and identify which scenario was executed by whom.


```
#!/bin/bash
#listScenarios := list of test scenarios
#scenario_name := a scenario from the list "listScenarios"
#scenario := Count Variable for the scenarios if you want to the test the same scenario 2 times in the same execution
#person := an additional argument from command line to count the person and identify which scenario was executed by whom.


scenario=1
person=$1

listScenarios="FollowLeadingVehicle_3 FollowLeadingVehicle_3 DynamicObjectCrossing_1 SignalizedJunctionLeftTurn_5 FollowLeadingVehicle_1 ManeuverOppositeDirection_2"

for scenario_name in $listScenarios; do

    #execute the scenario_runner.sh with the 4 arguments (name, true/false, scenario count, which person)
    bash scenario_runner.sh $scenario_name true $scenario $person

    echo "Press any key to continue with the next scenario"

    while [ true ] ; do
        read -t 3 -n 1
        if [ $? = 0 ] ; then
        echo "Press any Key to continue with the next scenario"
        break
        #bash scenario_runner.sh $scenario_name true $scenario $person
        else
        echo "Waiting for the keypress to continue with the next scenario"
        fi
    done
    let "scenario++"

done
```



## V.) Pros and Cons of fully- and semi-automated Test Scenario
This section explains why we use a semi-automated test scenario once in paragraph III.)/ IV.) and a fully-automated test scenario once in paragraph II.)

The main reason is that with the fully-automated Test Scenario we receive the following memory error message after about 3 executions and and then restart the computer:

```
Exception thrown: bind: Address already in use
Signal 11 caught.
Malloc Size=65538 LargeMemoryPoolOffset=65554 
CommonUnixCrashHandler: Signal=11
Malloc Size=65535 LargeMemoryPoolOffset=131119 
Malloc Size=147680 LargeMemoryPoolOffset=278816 
Engine crash handling finished; re-raising signal 11 for the default handler. Good bye.
```

On the other hand, the big advantage of the fully-automated version is that only one command has to be executed for a full test scenario.

Besides this big advantage we found it more exciting to work with a semi-automated script and to make the whole thing modular and yet easy to handle. Therefore we recommend to use the semi-automated script for the Scenario Runner, especially the approach to run a list of scenarios semi-automated as described in pararaph IV).


## VI.) Next references
You can find "how to run a route based scenario (similar to CARLA AD Challenge) and set up an agent for evaluation".
[7. Running_route-based_scenarios_(similar_to_the_CARLA_AD_Challenge)_and_agent_evaluation](Running_route-based_scenarios_(similar_to_the_CARLA_AD_Challenge)_and_agent_evaluation.md)