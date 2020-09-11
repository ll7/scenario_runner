# Open Scenario

This tutorial describes what OpenScenario is and why the format was not investigated further in the project module 


## 1.) What is OpenScenario?

OpenSCENARIO is an open file format for the description of dynamic contents in driving simulation applications. In the following there is a quick overview where you can find which information:

- How you can execute the supported scenarios in OpenScenario format is described [here](Execute_Scenarios.md).

- Furthermore if you want to use its evaluation criteria you can have a look in the [documentation](openscenario_support.md) from CARLA

- For further information you also can have a look on their [homepage](http://www.openscenario.org/).


## 2.) Reasons why the format was not investigated further in the project module

OpenScenario is only partially supported by ScenarioRunner. First, there are fewer scenarios in OpenScenario than in python format. Secondly, only a few of the existing scenarios are executable at all. Thirdly, the development is less modular than Python development and therefore more difficult to modify.