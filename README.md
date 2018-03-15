# DEECo Playground

DEECo Playgrond is a framework for simulation and visualization of scenarios for smart Cyber-Physical Systems. Its goal is to help in prototyping and testing of software for sCPS. In particular, it can be used for developing and testing scenarios featuring autonomous mobile entities (like robots or autonomous vehicles) that cooperate with each other, with other smart objects placed in the environment and with the environment itself.

## Execution of example scenarios

In order to run the application you need to have JDK >=8 installed.

Several example scenarios can be executed with corresponding shell scripts (on Linux systems) or batch files (on Windows). They can be found in the `demos-linux` and `demos-windows` directories respectively. 

There are two scripts for each scenario, simulation and visualization. Each scenario has to be simulated before it can be visualized, e.g.:

```
./demo-2-firefighters-simulate.sh
./demo-2-firefighters-visualize.sh
```

## Virtual machine

In order to make launching of the project as simple as possible, we have prepared a virtual machine image (for [VirtualBox](https://www.virtualbox.org/)) that can be downloaded [here](http://d3s.mff.cuni.cz/software/deeco/files/deeco-playground-vm.zip). It contains the project with all of its dependencies already installed, along with IDE and documentation files. 

## Using ant build file

If you have [Apache Ant](http://ant.apache.org/) installed, you can run simulations and visualizations with the following commands (run from the project root directory):

```
ant run.simulation -Dargs="arguments" 
ant run.visualization -Dargs="arguments"
```

In the case of simulation the `arguments` are scenario files (more than one can be specified). For visualization, the first argument has to be a simulation logs file, the second one is an optional configuration file.

The ant build file also allows to generate javadoc with the command `ant doc` and to clean the generated files from the directory with `ant clean`.


## Importing the project to IDE

The project directory can be opened as an [IntelliJ IDEA](https://www.jetbrains.com/idea/download/) project. As such it will contain several predefined run configurations. For each existing scenario, there are two of them: one for simulation, and one for visualization. In order to run the visualization of the scenario you need to simulate it first (since the simulation produces the logs, which are then supplied to the visualization). 

There are also `.project` and `.classpath` files in the project directory, that can be used to import the project to Eclipse or NetBeans. The runnable classes are `cz.cuni.mff.d3s.deeco.playground.simulation.Main` and `cz.cuni.mff.d3s.deeco.playground.visualization.Main` for imulation and visualization respectively.

## Documentation

If you are interested in creation of new scenarios with this framework, you can read the Scenario Creation Guide (**Guide.pdf**), which can be found in the repository. It contains a step-by-step tutorial illustrating the process of of scenario creation on two examples.

The architecture of the playground, its internal structure and implementation are described in detail in the  **Architecture.pdf** document.

The **manual.html** page contains a more technical description of the things that can be useful for scenario developers. It describes the formats of scenario files and configuration files; and provides an overview of the classes that user needs to use in the process of scenario creation, explaining the meaning and function of all their methods and attributes. The links in this file refer to the javadoc pages (you need to generate javadoc in order to make them work).

## Project structure

The source code of the framework and the example scenarios can be found in the `src/java` folder. The XSD schemas for scenario files and visualization configuration files are located in the `src/resources` folder. Folder `examples` contains the scenario files, the configuration files, the textures and the bitmaps of obstacles used in all the example scenarios.

## License

[Apache 2.0 License](http://www.apache.org/licenses/LICENSE-2.0.html). 
