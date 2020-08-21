# Record your test case and evaluate it

The following describes how a Test Scenario is recorded, where it is stored and how it can be evaluated by replaying it or reading information from it.

## I.) Storage Location

CARLA includes now a recording and replaying API, that allows to record a simulation in a file and later replay that simulation. The file is written on the server side only, and it includes which actors are created or destroyed in the simulation, the state of the traffic lights and the position and orientation of all vehicles and pedestrians.


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


## II.) Recording
This will start recording, and optionally you can spawn several actors and define how much time you want to record. if you are in the above mentioned directory (~/CARLA_0.9.9/PythonAPI/examples) of example scripts enter the following command on the command line while starting a scenario:
```
python start_recording.py <param> "<name>" 
```

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

## III.) Evaluating
With the following 4 sample scripts you can replay a recorded scenario, retrieve its information, the collisions and the blocked actors.

### Replaying
This will start a replay of a file. We can define the starting time, duration and also an actor to follow.
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
This will show all the information recorded in file. It has two modes of detail, by default it only shows the frames where some event is recorded, the second is showing info about all frames (all positions and trafficlight states).
```
show_recorder_file_info.py <param> "<name>" 
```

You can replace the placeholder <"param"> with one of the following parameters:
```
-f: Filename
-a: Flag to show all details (optional)
```

For example show the information of a recorded scenario "test2.log".

```
python show_recorder_file_info.py -f test2.log
```


### Collision Output
This will show all the collisions hapenned while recording (currently only involved by hero actors).
```
show_recorder_collisions.py <param> "<name>" 
```

You can replace the placeholder <"param"> with one of the following parameters:
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

For example show the collisions of a recorded scenario "test2.log".

```
python show_recorder_collisions.py -f test2.log
```

### Blocked Actors Output
This will show all the actors that are blocked or stopped in the recorder. We can define the time that an actor has not been moving and travelled distance by the actor thresholds to determine if a vehicle is considered as blocked or not.
```
show_recorder_actors_blocked.py <param> "<name>" 
```

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