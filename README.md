# SimSo Mixed-Criticality extension
This repository represents an extension of one of the most widely used real-time scheduling simulator called
SimSo. This extension allows users to generate and schedule mixed criticality real-time tasks, while also
providing support for developing and running customized mixed criticality task scheduling algorithms.

SimSo's base links:
- Backend repository: https://github.com/MaximeCheramy/simso
- GUI repository: https://github.com/MaximeCheramy/simso-gui

# Content
In this repository you will find three possible ways to use the mixed-criticality extension.<br/>
The logic of the original SimSo simulator is divided into two repository. One is responsible for the GUI (frontend)
and the other one, for the actual logic (backend).<br/> The current repository is also following the above approach, so this is 
why we have two folders for each way of using the extension. Possible approaches:
- Forked:
- Applying patches:
- Already patched:

# Setup for local development
After making any change to the code, run `python setup.py install` command in order to apply them.

# Usage
For making a mixed-criticality task scheduling simulation, using GUI (graphical user interface), please follow the next steps:
1. Run `simso` command in order to open the GUI.
2. After the window opened, configure simulation's model, select the scheduler and add processors.
3. In the `Tasks` tab, press `Add task` to add a new task in the simulation.
4. Configure the newly added task by selecting the `Mixed-Criticality` option from the task class column, followed by the common parameters and specific ones. The specific parameters required by a mixed-criticality task are:
    - `Nr. Crit. levels`: the number of criticality levels the task can have
    - `Criticality level`: the actual criticality level of the task
    - `List of WCETS`: list with WCETS, one for each criticality level
    - `List of WCET deviations`: list with deviations, one for each criticality level, representing by how much the jobs of the task may exceed its WCET.
5. Repeat steps 3 and 4 until the simulation's configuration is completed.

Note: `WCET` parameter is disabled for mixed-criticality tasks, because it is automatically set by the WCET of task's criticality level.

## Sample of mixed-criticality tasks configuration using EDF-VD uniprocessor scheduler

<img width="1477" alt="Screenshot 2024-04-24 at 21 54 57" src="https://github.com/andreib99/mxsimso/assets/58254999/040a9e4c-3bab-414d-a38d-76efa1014772">

## Possible Gantt chart for above sample

<img width="1103" alt="Screenshot 2024-04-24 at 23 06 00" src="https://github.com/andreib99/mxsimso/assets/58254999/3eeb746f-dadc-42e1-bad0-2f38dc55662c">
