# Basics of Bash script automation
Bash scripts are suitable for combining programs according to your needs and they play a central role in the everyday life of system administration and automation. 

This documentation describes first the very fundamental basics of Bash Scripts. Second it shows where you can find further useful topics and third how you can run multiple terminals from one terminal automated.


## 1.) Basics of Bash Scripts

Bash Scripts have the file format:
```
.sh
```

You can open any editor to create a bash file. Here, nano editor is used to create the file and filename is set as ‘MyScript.sh’
```
$ nano MyScript.sh
```

After initialized you first script add the following to the file and save the file:
```
#!/bin/bash
echo "Hello World"
```

Then you can run the bash script from command line (if you are in the right directory):
```
$ bash MyScript.sh
```

## 2.) Further useful topics

More useful topics with examples to work with a bash script can be found under the following [link](https://linuxhint.com/30_bash_script_examples/). 

These include topics such as loops, if/else statements, retrieving command line arguments, functions, etc. 

## 3.) Run multiple Terminals from one bash script

For the carla use case it was a consideration to call several separate command lines from a bash script to execute the respective scripts (Carla Server, Scenario, Manual Control, Record, etc.) Due to a memory overflow (more about this in [chapter](Semi_automated_tests.md)) this idea was abandoned. 

However, the command for this is the following:
```
#gnome-terminal -e <command>
```
Replace the <command> with the following path:
```
/home/carlaws19/CARLA_0.9.9/CarlaUE4.sh
```