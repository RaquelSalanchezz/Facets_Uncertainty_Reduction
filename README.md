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
* `Clustering_Algorithms:` in this folder we can find the Clustering_Algorithm.ipynb file, which contains the code of the clustering algorithm.
* `Experiments_Visualization:` in this folder we can find the Experiments_Visualization.ipynb file, which contains the code to simulate some experiments and generate the graphs.
* `Vehicles_Data:` in this folder we can find the data and configuration files and PRISM models (PRISM_models folder) used to run the experiments.
  * `vehicles_X.csv`: data files used to run the algorithms in the experiments.
  * `configuration_vehicles.json`: configuration file for vehicles scenario.

## Configuration File Structure
The configuration files define a standardized schema for modeling resource allocation scenarios, such as electric vehicle charging or robotic patient feeding. Each file describes two main classes: a **Consumer** (e.g., ElectricVehicle, Patient, Crop) and a **Resource** (e.g., Charger, Robot), including their attributes and methods.

The configuration sets key parameters like the number of entities and resources, their states (AVAILABLE, ACTIVE, DONE), progress tracking variables, speed and capacity values, and action labels (start_action, release_action, action) that drive transitions in the PRISM model. It also includes reward options (e.g., reward_acum, reward_timespan) and specifies the output file name.

This modular design allows the generator to easily adapt to different domains by simply changing the input file, supporting flexibility, reusability, and scalability.

## Running the Experiments
To run the code, you need to do it within Eclipse IDE for Java and Visual Studio Code for Python or similar environment.The following explains how to run algorithms, with the environments previously installed:

### Download and import the Java project from GitHub into Eclipse
1. First, go to the GitHub repository, click on Code, and select Download ZIP. Extract the downloaded ZIP file to your preferred folder. Alternatively, if you have Git installed, you can clone the repository by using the command "git clone" <repository URL> in your terminal.

2. Once you have the project files, open Eclipse and navigate to File > Import > Existing Projects into Workspace. In the dialog that appears, choose Select root directory and browse to the folder where you extracted the project. Then, click Finish to import it into Eclipse.

3. If the project is not recognized as a Java Project, right-click on it in the Project Explorer, go to Configure > Convert to Java Project, and Eclipse will set it up as a Java Project. Additionally, make sure all required dependencies are configured in the Build Path to avoid errors.

### Execution of the code to generate the charts
You can also execute some of the experiments and generate charts using the code found in evaluation_charts.ypinb. To achieve this, simply run the cells in Google Colab or similar environment in order, and various graphs will be displayed as output. If you wish to modify the data or the parameters to create new experiments and grapg graphs, you can do so by editing the parameters and the data structures at the beginning of the code that generates each graph.

