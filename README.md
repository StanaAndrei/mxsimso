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
- Forked: There are two submodules named simso-forked and simso-gui-forked which points to the forks made from the original SimSo simulator, which extends it to support mixed-criticality tasks scheduling.
- Patch: Contains the patches of both projects. Here we can see the actual modifications made to the original SimSo within the current extension.
- Already patched: In the mxsimso-patched and mxsimso-gui-patched directories we can find both projects having the above patches already applied.

# Setup for local development
For the forked approach, please follow these steps:
1. Click on the submodules links (simso-forked and simso-gui-forked), which will redirect you to the forked repositories.
2. Make a clone for each repository locally.

If you want to manually apply the changes made to the original SimSo, follow these steps:
1. Clone the original SimSo's repositories, using the links from the top of the file.
2. Download both patches (from the patch directory) and apply them to their specific project by using the `git apply <.patch file>` command.

Steps to follow in case you want to use this extension with the changes already applied:
1. Download both projects patched directories (mxsimso-patched and mxsimso-gui-patched)

## Instalation
After having both projects locally, follow these steps in order to be able to use this extension:
1. Create a virtual environment for simso-gui repository using the following command: `python -m venv /path/to/new/virtual/environment`
2. Activate the virtual environment: `source /path/to/new/virtual/environment/bin/activate`
3. Install SimSo's GUI dependencies in the new virtual environment by running the `pip install .` command.
4. In the second repository (simso) select to use the above virtual environment as well, by using the `source /path/to/new/virtual/environment/bin/activate` command.
5. Now install also the necessary dependencies for the second project with the `pip install .` command.
6. Execute `simso` command in order to run the application.

Notes: 
- After making any changes to the code, in any project, run `python setup.py install` command in order to apply them.
- Because both projects are installed in the same virtual environment, any changes made on one of them, will be automatically visible in the other one as well.

# Usage
For making a mixed-criticality task scheduling simulation, using GUI (graphical user interface), please follow the next steps:
1. Run `simso` command in order to open the GUI.
2. After the window opened, configure simulation's parameters, select the scheduler and add processors.
3. In the `Tasks` tab, press `Add task` to add a new task in the simulation.
4. For the newly added task select the `Mixed-Criticality` option from the task class column. Configure the general parameters and specific ones. More information for general parameters can be found in the SimSo's original repository. The specific parameters required by a mixed-criticality task are:
    - `Nr. Crit. levels`: the number of criticality levels the task can have
    - `Criticality level`: the actual criticality level of the task
    - `List of WCETS`: list with WCETS, one for each criticality level
    - `List of WCET deviations`: list with deviations, one for each criticality level, representing by how much the jobs of the task may exceed its WCET.
5. Repeat steps 3 and 4 until the simulation's configuration is completed.

Note: `WCET` parameter is disabled for mixed-criticality tasks, because it is automatically set by the WCET of task's own criticality level.

## Sample of mixed-criticality tasks configuration using EDF-VD uniprocessor scheduler

<img width="1477" alt="Screenshot 2024-04-24 at 21 54 57" src="https://github.com/andreib99/mxsimso/assets/58254999/040a9e4c-3bab-414d-a38d-76efa1014772">

## Possible Gantt chart for above sample

<img width="1103" alt="Screenshot 2024-04-24 at 23 06 00" src="https://github.com/andreib99/mxsimso/assets/58254999/3eeb746f-dadc-42e1-bad0-2f38dc55662c">
