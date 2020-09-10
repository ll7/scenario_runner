# Running route-based scenarios (similar to the CARLA AD Challenge) and agent evaluation
This documentation describes how you can run a route based scenario (similar to the CARLA AD Challenge) and set up an agent for evaluation.



## I.) Running route-based scenarios (similar to the CARLA AD Challenge)
To run a route-based scenario you have to run the ScenarioRunner as follows:

```
python scenario_runner.py --route <path/to/route-file> <path/to/scenario_sample_file> [route id] --agent <path/to/agent_file>
```

Example:
```
python scenario_runner.py --route /home/carlaws19/scenario_runner/srunner/data/routes_debug.xml /home/carlaws19/scenario_runner/srunner/data/all_towns_traffic_scenarios1_3_4.json 0 --agent /home/carlaws19/scenario_runner/srunner/autoagents/npc_agent.py
```

If no route id is provided, all routes within the given file will be executed.

By doing so, ScenarioRunner will match the scenarios to the route, and they'll activate when the ego vehicle is nearby. However, routes need an autonomous agent to control the ego vehicle. Several examples are provided in "srunner/autoagents/".

With the python manual_control.py script, you are able to run the route-based scenario with an ego vehicle.:
```
python manual_control.py
```


## II.) Setting up your agent for evaluation

To have your agent evaluated by the challenge evaluation system you must define an Agent class that inherits the AutonomousAgent base class. In addition, you need to setup your environment as described in the Challenge evaluator tutorial.

On your agent class there are three main functions (setup(), sensors() and run_step()) to be overwritten that need to be defined in order to set your agent to run. Further you also should consider the route to the goal that is initially set as a variable.

### The "setup" function:

This is the function where you should make all the necessary setup for the your agent. This function receives as a parameter the path to a configuration file to be parsed by the user.

When executing the "scenario_runner.py --route" you should pass the configuration file path as a parameter.
 
For example:

```
python scenario_runner.py --route --agent=<path_to_my_agent> --config=myconfigfilename.format
```

### The "sensors" function:

This function is where you set all the sensors required by your agent. For instance, on the dummy agent sample class the following sensors are defined:
```
def sensors(self):
    sensors = [{'type': 'sensor.camera.rgb', 'x':0.7, 'y':0.0, 'z':1.60, 'roll':0.0, 'pitch':0.0, 'yaw':0.0, 'width':800, 'height': 600, 'fov':100, 'id': 'Center'},
               {'type': 'sensor.camera.rgb', 'x':0.7, 'y':-0.4, 'z': 1.60,   'roll': 0.0, 'pitch': 0.0, 'yaw': -45.0, 'width': 800, 'height': 600, 'fov': 100, 'id': 'Left'},
               {'type': 'sensor.camera.rgb', 'x':0.7, 'y':0.4, 'z':1.60, 'roll':0.0, 'pitch':0.0, 'yaw':45.0, 'width':800, 'height':600, 'fov':100, 'id': 'Right'},
               {'type': 'sensor.lidar.ray_cast', 'x': 0.7, 'y': -0.4, 'z': 1.60, 'roll': 0.0, 'pitch': 0.0, 'yaw': -45.0, 'id': 'LIDAR'},
               {'type': 'sensor.other.gnss', 'x': 0.7, 'y': -0.4, 'z': 1.60, 'id': 'GPS'},
               {'type': 'sensor.speedometer','reading_frequency': 25, 'id': 'speed'}
              ]
    return sensors
```

Every sensor is a dictionary where you should specify:
```
type: basically which is the sensor to be added, for example: 'sensor.camera.rgb' for an rgb camera or 'sensor.lidar.ray_cast' for a ray casting lidar.
id: the label that will be given to the sensor in order for it to be accessed later.
other parameters: these are sensor dependent, such as position, 'x' and 'y', or the field of view for a camera, 'fov'
```
### The "run_step" function:

This function is called on every step of the simulation from the challenge evaluation an receives some input data as parameter. This input data is a dictionary with all the sensors specified on the "sensors" function. 
This function should return a vehicle control to be applied into the ego vehicle. 

The initial route: On the beginning of the execution, the entire route that the hero agent should travel is set on the "self.global_plan" variable:
```
[({'z': 0.0, 'lat': 48.99822669411668, 'lon': 8.002271601998707}, <RoadOption.LANEFOLLOW: 4>),
({'z': 0.0, 'lat': 48.99822669411668, 'lon': 8.002709765148996}, <RoadOption.LANEFOLLOW: 4>),
...
({'z': 0.0, 'lat': 48.99822679980298, 'lon': 8.002735250105061}, <RoadOption.LANEFOLLOW: 4>)]`
```

It is represented as a list of tuples, containing the route waypoints, expressed in latitude and longitude and the current road option recommended. For an intersection, the option can be go straight, turn left or turn right. For the rest of the route the recommended option is lane follow.

## III.) Next references
The a-part from the additional work describes Basics of Bash Scripts, shows further useful topics and how you can run multiple terminals from one terminal automated: [a. Basics_of_bash_script_automation](Basics_of_bash_automation.md).