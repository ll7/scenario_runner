# Open Scenario

This tutorial describes what OpenScenario is and why the format was not investigated further in the project module 


## I.) What is OpenScenario?

OpenSCENARIO is an open file format for the description of dynamic contents in driving simulation applications. In the following there is a quick overview where you can find which information:

- How you can execute the supported scenarios in OpenScenario format is described in [Execute_the_supported_scenarios.md](Execute_the_supported_scenarios.md).

- Furthermore if you want to use its evaluation criteria you can have a look in the documentation from the origional scenario_runner [openscenario_support.md](openscenario_support.md).

- For further information you also can have a look on their homepage [http://www.openscenario.org/](http://www.openscenario.org/).


## II.) Reasons why the format was not investigated further in the project module

OpenScenario is only partially supported by ScenarioRunner. First, there are fewer scenarios in OpenScenario than in Python format. Secondly, only a few of the existing scenarios are executable at all. Thirdly, the development is less modular than Python development and therefore more difficult to modify.