# DEECo Playground

DEECo Playgrond is a framework for simulation and visualization of scenarios for smart Cyber-Physical Systems (sCPS). Its goal is to help in prototyping and testing of software for sCPS. In particular, it can be used for developing and testing scenarios featuring autonomous mobile entities (like robots or autonomous vehicles) that cooperate with each other, with other smart objects placed in the environment and with the environment itself.

## Execution of example scenarios

In order to run the application you need to have Java 8 or newer installed.

There are three prepared and ready-to-run example scenarions. They can be executed with shell scripts (on Linux systems) or batch files (on Windows), which are in the `demos-linux` resp. `demos-windows` directories. 

There are always two scripts for each scenario, simulation and visualization.
Each scenario has to be simulated before it can be visualized, i.e., the correct sequence of execution is :

```
./name-of-scenario-simulate.sh
./name-of-scenarion-visualize.sh
```
The `*-simulate.sh` script launches the simulator. It continuously outputs information about simulation progress and in the end, it prints statistics about the simulation.

The `*-visualize.sh` script launches the visualizer configured with data produced by the simulator. It opens a window, in which the visualization runs. It can be controlled via the following keys:
- left arrow - skip several steps back
- right arrow - skip several steps forward
- space - pause/resume visualization

### Scenario 1

The scenario features two types of robots. There is a one robot of the type PredatorRobot, which moves randomly through
the field. All the other robots are of the type PreyRobot, and are programmed to run away from the predator, if it
appears near them. The prey robots receive the information about the position of the predator through an ensemble.
The scenario also show the default visualization without any additional layers.

Its configuration is in the file `examples/scenarios/predator.xml`.

### Scenario 2

The Firefighters scenario presents a case in which a team of firefighter robots has an objective to extinguish fires
appearing on the field. The leader of the firefighter team collects information about each robot's situation, and issues
orders to its teammates based on that information. The scenario shows usage of an additional layer of the environment,
the temperature layer, in which the fires appear. Robots in this scenario are equipped with additional temperature
sensors and fire extinguishers to interact with this layer. There is also the recharge station charging the robors (for movements and extinguishing, the robors consumes energy).

Its configuration is in the file `examples/scenarios/firefighters.xml`.

### Scenario 3

In the Competition scenario, two teams of robots compete with each other for items appearing on the screen. The items
are interactive objects programmed to disappear when a robot shows up near them, and to reappear later at a different
location. A team receives a point for each item collected in this way. The simulation stops when a team receives a
defined number of points. In this scenario, robots' movements consume energy stored in their batteries, which can be
recharged at charging stations of each team.

Its configuration is in the file `examples/scenarios/competition.xml`.

## Virtual machine

In order to make launching of the project as simple as possible, we have prepared a virtual machine image (for [VirtualBox](https://www.virtualbox.org/)) that can be downloaded [here](http://d3s.mff.cuni.cz/software/deeco/files/deeco-playground-vm.zip). It contains a Linux installation with the project and all of its dependencies already installed, along with IDE and documentation files. On the desktop of the VM you can find a readme file with instructions on running the project, using IDE, etc.

To run the above described scenarios
* open the terminal (third icon on the left toolbar)
* change the current directory with the command `cd Desktop/deeco-playground/demos-linus`
* run the launching scripts, i.e:
  * `./demo-1-predator-simulate.sh`
  * `./demo-1-predator-visualize.sh`
  * `./demo-2-firefighters-simulate.sh`
  * `./demo-2-firefighters-visualize.sh`
  * `./demo-3-competition-simulate.sh`
  * `./demo-3-competition-visualize.sh`

## Using ant build file

If you have [Apache Ant](http://ant.apache.org/) installed, you can run simulations and visualizations with the following commands (run from the project root directory):

```
ant run.simulation -Dargs="arguments" 
ant run.visualization -Dargs="arguments"
```

In the case of simulation the `arguments` are scenario files (more than one can be specified). For visualization, the first argument has to be a simulation logs file, the second one is an optional configuration file.

The ant build file also allows to generate javadoc with the command `ant doc` and to clean the generated files from the directory with `ant clean`.


## Opening the project in IDE

The project directory can be opened as an [IntelliJ IDEA](https://www.jetbrains.com/idea/download/) project. As such it will contain several predefined run configurations. For each existing scenario, there are two of them: one for simulation, and one for visualization. In order to run the visualization of the scenario you need to simulate it first (since the simulation produces the logs, which are then supplied to the visualization).

These launch configurations are available in the combo-box on the top toolbar in IDE. You can just choose the desired configuration in the combo-box and then hit the launch button (the green triangle on the right side of the combo-box).

There are also `.project` and `.classpath` files in the project directory, that can be used to import the project to Eclipse or NetBeans. The runnable classes are `cz.cuni.mff.d3s.deeco.playground.simulation.Main` and `cz.cuni.mff.d3s.deeco.playground.visualization.Main` for simulation and visualization respectively.

## Documentation

There are three main documents.

**Guide.pdf** contains the Scenario Creation Guide. It is a step-by-step tutorial illustrating the process of a scenario creation on two examples.

**Architecture.pdf** describes the architecture of the playground framework and its internal structures and detailes the implementation.

**manual.html** page contains a technical description of scenario creation and configuration. It describes the formats of scenario files and configuration files. Also it provides an overview of the classes (i.e., components and ensembles) that a user needs to create in the process of scenario creation, explaining the meaning and behavior of all their methods and fields. The links in the file may refer to the javadoc documentation (you need to generate javadoc with the `ant doc` command in order to make them work).

## Project structure

The source code of the framework and the example scenarios can be found in the `src/java` folder.

The XSD schemas for scenario files and visualization configuration files are located in the `src/resources` folder.

Folder `examples` contains the scenario files, the configuration files, the textures and the bitmaps of obstacles used in all the example scenarios.

## License

[Apache 2.0 License](http://www.apache.org/licenses/LICENSE-2.0.html). 
