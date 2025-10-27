# The Many Facets of Uncertainty Reduction

## Abstract
Uncertainty management is key to successful achievement of system goals in self-adaptation. An important aspect to such management is employing various mechanisms to reduce uncertainty. Although reducing uncertainty does in theory result in a better characterization of the current and future states of the system and the environment, the tradeoffs and multiple facets associated with employing such mechanisms are often nuanced and not always easily understood. In this paper, we articulate a description of some of the abstruse facets entailed by uncertainty reduction, illustrating them on a self-adaptive CPS in the electric vehicle charging domain.

## Dependencies

The project is implemented using the latest version of Python (3.12.1) and Java (JDK23). 
The Java project relies on the following libraries and tools to function correctly:
1. **Jython**: A Java implementation of Python, required to bridge the execution of Python scripts within the Java environment. Ensure that `jython-standalone-X.X.X.jar` is included in the project build path.
2. **PRISM Library**: The project utilizes PRISM, a probabilistic model checker, including its components such as `Prism`, `PrismLog`, and related modules for parsing models (`parser.ast`), simulating modules (`simulator`), and handling properties files. To execute the project you must have the PRISM libraries integrated and accessible in the project setup. For more information check https://github.com/prismmodelchecker/prism-api and https://github.com/prismmodelchecker/prism prism.

Python files require the installation of the following libraries for its development and execution:
1. **NumPy** 1.26.2
2. **Matplotlib** 3.8.2

## Repository structure
This repository contains the following items:
* `Readme.md`: this file explaning the code of the project
* `PythonFiles`: this folder contains four files where we can find the clases and the functions needed to execute the algorithms.  
  * `MILP_algorithm.py`: this file contains the code of the MILP algorithm, that solve the vehicle charging planning problem without considering uncertainty. This algorithm is used as baseline for the experiments.
  * `Genetic_algorithm.py `: this file contains the code of the original genetic algorithm, that solve the vehicle charging planning problem considering uncertainty.
  * `Classes_generator.py`: this file contains the functions responsible for generating the specific resource and consumer classes required by the algorithms.
  * `Generated_classes.py`: this file includes an example of the generated classes for the vehicles scenario.
  * `ClassesAG.py`: this file contains the functions that the new Genetic Statistical Model Checking Algorithm (GSMCA) needs to work.
  * `RunGA.py`: this file contains the code to run the new version of the genetic algorithm using Python.
* `JavaAlgorithms`: this folder contains the Java project where de  is implemented. In the src package we can find three files:
  * `ExecuteGeneticAlgorithm.java`: this file handles the execution of the GSMCA.
  * `ExecuteMILP.java`: this file is responsible for launching the MILP algorithm from Java.
  * `ModelCheckFromFiles.java`: this file is responsible for evaluate the model launching PRISM. It consist on a version of a PRISM API example adapted to our project.
