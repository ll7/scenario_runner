# Record and evaluate scenarios

The following describes how you can record a scenario, where it is stored and how it can be evaluated by replaying it or reading information from it. Finally, it shows a further method to display the output of the test criteria.

## 1.) Storage Location

CARLA includes a recording and replaying API, that allows to record a simulation in a file and later replay that simulation. The file is written on the server side only, and it includes which actors are created or destroyed in the simulation, the state of the traffic lights and the position and orientation of all vehicles and pedestrians. For more information have a look [here](https://carla.readthedocs.io/en/0.9.6/recorder_and_playback/).


### Storage Location of the recorded Scenarios
All the recorded scenarios are stored in the following path as a ".log"-file:
```
~/.config/Epic/CarlaUE4/Saved
```

### Storage Location of sample Scripts
The following path contains 5 sample scripts for recording and evaluating a scenario:
```
~/CARLA_0.9.9/PythonAPI/examples
```


## 2.) Recording
Before you execute the next command to record a scenario you have to execute the known commands as described [here](Execute_Scenarios.md): 

_in brief_: (1) start the Carla Server, (2) execute a scenario and (3) execute manual_control.py.

Then you can enter the following command in the above mentioned directory (~/CARLA_0.9.9/PythonAPI/examples) while starting a scenario:
```
python start_recording.py <param> "<name>" 
```
This will start recording, and optionally you can spawn several actors and define how much time you want to record. 

You can replace the placeholder <"param"> with one of the following parameters:

```
-f: Filename to write
-n: Vehicles to spawn (optional, 10 by default)
-t: Duration of the recording (optional)
```

For example recording a Scenario "test1.log" without additional spawned vehicles.

```
python start_recording.py -f "test1.log" -n "0"
```

## 3.) Evaluating through sample scripts
With the following 4 sample scripts you can replay a recorded scenario, retrieve its information, the collisions and the blocked actors.

### Replaying
Be aware that you have to execute the same 3 instructions as described in "II.) Replay" at the beginning.

Then you can start a replay of a file. We can define the starting time, duration and also an actor to follow.
```
python start_replaying.py <param> "<name>" 
```

You can replace the placeholder <"param"> with one of the following parameters:
```
-f: Filename
-s: Starting time (optional, by default from start)
-d: Duration (optional, by default all)
-c: Actor to follow (id) (optional)
```

For example replay a recorded scenario "test2.log" from the camera perspective of the actor with the id "828".

```
python start_replaying.py -f "test2.log" -c "828"
```

### Information Output
In Contrast to Record and Replay you only have to execute Carla as a preparation to execute the following commands.

Then you can enter the following command in the above mentioned directory (~/CARLA_0.9.9/PythonAPI/examples) while starting a scenario:

```
show_recorder_file_info.py <param> "<name>" 
```
This will show all the information recorded in file. It has two modes of detail, by default it only shows the frames where some event is recorded, the second is showing info about all frames (all positions and trafficlight states).

You can replace the placeholder <"param"> with one of the following parameters:
```
-f: Filename
-a: Flag to show all details (optional)
```

For example show the information of a recorded scenario "test2.log".

```
python show_recorder_file_info.py -f test2.log
```

For example, a section of the information that can be output for the actor with the ID "828", which in turn can be used for a replay.
```
 Create 828: vehicle.lincoln.mkz2017 (1) at (10700, 13300, 3.65615)
  number_of_wheels = 4
  sticky_control = true
  object_type = 
  color = 15,11,44
  role_name = hero
```



### Collision Output
In Contrast to Record and Replay you only have to execute Carla as a preparation to execute the following commands.

Then you can enter the following command in the above mentioned directory (~/CARLA_0.9.9/PythonAPI/examples) while starting a scenario:

```
show_recorder_collisions.py <param> "<name>" 
```
This will show all the collisions hapenned while recording (currently only involved by hero actors).

In simulations with a hero actor, the collisions are automatically saved, so we can query a recorded file to see if any hero actor had collisions with some other actor. You can replace the placeholder <"param"> with one of the following parameters:
```
-f: Filename
-t: Two letters definning the types of the actors involved, for example: -t aa
    h = Hero
    v = Vehicle
    w = Walker
    t = Traffic light
    o = Other
    a = Any
```
The collision query needs to know the type of actors involved in the collision. If we do not want to specify it, we can specify a (any) for both. Currently, only hero actors record the collisions. Therefore, we have considered that the first actor will be the hero always.:
```
    a a: Will show all collisions recorded
    v v: Will show all collisions between vehicles
    v t: Will show all collisions between a vehicle and a traffic light
    v w: Will show all collisions between a vehicle and a walker
    v o: Will show all collisions between a vehicle and other actor, like static meshes
    h w: Will show all collisions between a hero and a walker
```

For example show the collisions of a recorded scenario "test2.log".

```
python show_recorder_collisions.py -f test2.log
```
The Output would look like the following.
```
Version: 1
Map: Town01
Date: 08/20/20 13:20:28

    Time  Types     Id Actor 1                                 Id Actor 2                            

Frames: 607
Duration: 17.5917 seconds
```
There we can see that for each collision the time when happened, the type of the actors involved, and the id and description of each actor is shown.

### Blocked Actors Output
In Contrast to Record and Replay you only have to execute Carla as a preparation to execute the following commands.

Then you can enter the following command in the above mentioned directory (~/CARLA_0.9.9/PythonAPI/examples) while starting a scenario:

```
show_recorder_actors_blocked.py <param> "<name>" 
```
This will show all the actors that are blocked or stopped in the recorder. We can define the time that an actor has not been moving and travelled distance by the actor thresholds to determine if a vehicle is considered as blocked or not.   C

You can replace the placeholder <"param"> with one of the following parameters:
```
-f: Filename
-t: Minimum seconds stopped to be considered as blocked (optional)
-d: Minimum distance to be considered stopped (optional)
```

For example show the blocked Actors of a recorded scenario "test2.log".

```
python show_recorder_collisions.py -f test2.log
```
The Output would look like the following.
```
Version: 1
Map: Town01
Date: 08/20/20 13:20:28

    Time     Id Actor                                 Duration

Frames: 607
Duration: 17.5917 seconds
```
There we can see when an actor was stopped for at least the minimum time specified.

## 4.) Evaluate the output of the executed Scenario
To evaluate the test criteria of a scenario as described [here](Create_Scenarios.md) and [there](Modify_Scenarios.md). You can use the parameter "--output" by executing your scenario to get an evaluation output on terminal.
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

In Addition, here you can see the output result of a scenario evaluated for the two criterions "CollisionTest" and "CheckDrivenDistance".

![](img/Images%20for%20execution%20results/outpus.jpg)


## 5.) Next references
The next section shows how you can run [(semi-)automated tests](Semi_automated_tests.md) in different ways: