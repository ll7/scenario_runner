[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
![GitHub tag (latest SemVer)](https://img.shields.io/github/tag/carla-simulator/scenario_runner.svg)
[![Build Status](https://travis-ci.com/carla-simulator/scenario_runner.svg?branch=master)](https://travis-ci.com/carla/scenario_runner)

ScenarioRunner for CARLA
========================
This repository contains traffic scenario definition and an execution engine
for CARLA. It also allows the execution of a simulation of the CARLA Challenge.
You can use this system to prepare your agent for the CARLA Challenge.

Scenarios can be defined through a Python interface, and with the newest version
the scenario_runner also the upcoming [OpenSCENARIO](http://www.openscenario.org/) standard is supported.

[![Scenario_Runner for CARLA](Docs/img/scenario_runner_video.png)](https://youtu.be/ChmF8IFagpo?t=68)

Getting the ScenarioRunner
---------------------------

Use `git clone` or download the project from this page. Note that the master
branch contains the latest fixes and features, and may be required to use the latest features from CARLA.

It is important to also consider the release version that has to match the CARLA version.

* [Version 0.9.9](https://github.com/carla-simulator/scenario_runner/releases/tag/v0.9.9) and the 0.9.9 Branch: Compatible with [CARLA 0.9.9](https://github.com/carla-simulator/carla/releases/tag/0.9.9)
* [Version 0.9.8](https://github.com/carla-simulator/scenario_runner/releases/tag/v0.9.8) and the 0.9.8 Branch: Compatible with [CARLA 0.9.8](https://github.com/carla-simulator/carla/releases/tag/0.9.8)
* [Version 0.9.7](https://github.com/carla-simulator/scenario_runner/releases/tag/v0.9.7) and the 0.9.7 Branch: Compatible with [CARLA 0.9.7](https://github.com/carla-simulator/carla/releases/tag/0.9.7) but not with the later release patch versions. For these please use the current master of ScenarioRunner.
* [Version 0.9.6](https://github.com/carla-simulator/scenario_runner/releases/tag/v0.9.6) and the 0.9.6 Branch: Compatible with [CARLA 0.9.6](https://github.com/carla-simulator/carla/releases/tag/0.9.6)
* [Version 0.9.5](https://github.com/carla-simulator/scenario_runner/releases/tag/v0.9.5) and [Version 0.9.5.1](https://github.com/carla-simulator/scenario_runner/releases/tag/v0.9.5.1): Compatible with [CARLA 0.9.5](https://github.com/carla-simulator/carla/releases/tag/0.9.5)
* [Version 0.9.2](https://github.com/carla-simulator/scenario_runner/releases/tag/0.9.2): Compatible with [CARLA 0.9.2](https://github.com/carla-simulator/carla/releases/tag/0.9.2)

To use a particular version you can either download the corresponding tarball or simply checkout the version tag associated to the release (e.g. git checkout v0.9.5)

Currently no build is required, as all code is in Python.

Using the ScenarioRunner
------------------------

Please take a look at our [Getting started](Docs/getting_scenariorunner.md)
documentation.

Challenge Evaluation
---------------------

You can evaluate your own agents using a reproduction
of the CARLA Challenge by following [this tutorial](Docs/challenge_evaluation.md)

Contributing
------------

Please take a look at our [Contribution guidelines](http://carla.readthedocs.io/en/latest/CONTRIBUTING).

FAQ
------

If you run into problems, check our
[FAQ](http://carla.readthedocs.io/en/latest/faq/).

License
-------

ScenarioRunner specific code is distributed under MIT License.

Using the ScenarioRunner for (semi-)automated tests
-------
In context of a student project module from the University of Augsburg they investigated the scenario runner. The aim of the project module was to execute, investigate and use for test purposes the ScenarioRunner provided by CARLA. You can find the detailed documentation 
[here](https://github.com/ll7/scenario_runner/blob/master/Docs/Using_the_Scenario_Runner_for_semi_automated_testing.md).
