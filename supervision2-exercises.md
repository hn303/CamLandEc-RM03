# Supervision 2

## Short presentation by supervisors (10min)
1. The slides are available on: [CamLandEc-RM03](https://hn303.github.io/CamLandEc-RM03/).

## Instructions
1. This supervision builds on Supervision 2 Assignment. If you haven't completed this for some reason, please open [Supervision 2 Assignment](https://hn303.github.io/CamLandEc-RM03/supervision2-assignment_.md) and ask for one of the supervisors' help.
2. Read through the instruction carefully. You may face problems if you overlook any of the steps.
3. Remember to save the QGIS document regularly. 
4. When running tasks on QGIS, leave the settings as default unless instructed.

Note: functions and filename are `highlighted` in this document.

## Supervision overview
In this exercise, you will familiarise yourself with geoprocessing raster data on QGIS software as well as basic features of NetLogo software and how to use the GIS extension to input raster maps. 

### Resuming the QGIS exercise (20min)
1. Open `supervision2.qgz` file in your working directory `rm03_YourCRSid_sup2`.

#### Importing DEM data in `txt` as delimited text layer
#### Interpolation
#### Generating slope map in percent from the interpolated raster
#### Converting file format from `.tif` to `.asc`

### Setup work enviornment for NetLogo (5min)
1. Please download and install `NetLogo (6.1.1)` according to your platform. We recommend downloading `Windows (64-bit)`, `Mac OS X`, or `Linux (64-bit)`: [NetLogo Download Page](https://ccl.northwestern.edu/netlogo/6.1.1/). 
2. Continue using `rm03_YourCRSid_sup2` as your working directory.
3. Launch NetLogo. The interface will be explained along with exercises. Note: You can refer to [NetLogo User Manual (6.1.1)](https://ccl.northwestern.edu/netlogo/docs/) for more detailed information.
4. In `File` > `Models Library`, you can find a collection of sample models to explore. There are many sample models available on the User Community Models web page.

### Exercise 1: Wolf Sheep Predation (5min)
1. Open `Wolf Sheep Predation` from `Models Library` under `Biology` folder.
![](statics/Sup2_wolfsheep1.PNG)
2. Click `setup` > `go` to start the simulation, and click `go` agin to stop the simulation.
3. Try running the model with following changes and explain what happens:
- Change the `model-version` to `sheep-wolves-grass`.
- Decrese wolf poplulation.
- What other sliders/switches can you adjust to help out the sheep population?
- Can you find any parameters that generate a stable ecosystem?
![](statics/Sup2_wolfsheep2.PNG)

### Exercise 2: Game of Life (10min)
1. Open `Life` from `Models Library` under `Computer Science` > `Cellular Automata`.
2. Game of Life is a simple cellular automata (CA) model where the state of the cells change according to behavioral rules. As the simulation runs, you can find recurring shapes like gliders and blinkers. Note: You can refer to [Conway's Game of Life](https://en.wikipedia.org/wiki/Conway%27s_Game_of_Life) for more detailed information.
3. Click `setup-random` > `go-forever` to start the simulation, and click `go-forever` again to stop the simulation.
