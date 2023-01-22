# develop a cell2fire windows plugin

## setup c++ windows build environment
- Download & install Visual Studio 2022 (or community). Tested with `17.4.4`. 
	- Enable the "Desktop development with c++" & "python development" workloads.
	- Unselect "live share"

- Open Visual Studio, log to github, 
	- Clone https://www.github.com/itoledo/cell2fire
	- Change branch windows
	- Open solution cell2fire/Cell2FireC/Cell2fireC.sln

- Build requirements
	- Download Eigen 3.4.0 from official [Eigen site](https://eigen.tuxfamily.org/index.php?title=Main_Page#Compiler_support) and uncompress on folder `C:\dev\eigen-3.4.0`	
( get latest stable release.zip like https://gitlab.com/libeigen/eigen/-/archive/3.4.0/eigen-3.4.0.zip )

	- Download Dirent for Windows from official [site](https://github.com/tronkko/dirent) and uncompress on folder `C:\dev\dirent` (get like https://github.com/tronkko/dirent/archive/refs/tags/1.23.2.zip )

	- Download & install precompiled Boost from official [site](https://sourceforge.net/projects/boost/files/boost-binaries/). Tested with `1.81.0` (like https://sourceforge.net/projects/boost/files/boost-binaries/1.81.0/boost_1_81_0-msvc-14.3-64.exe/download)

- Setup Debug & Release project properties to test the .exe
	Debug -> Cell2Fire Debug Properties:
		- Command Arguments: --input-instance-folder ..\data\Sub40x40/ --output-folder ..\..\results\Sub40x40 --ignitions --sim-years 1 --nsims 5 --finalGrid --weather rows --nweathers 1 --Fire-Period-Length 1.0 --output-messages --ROS-CV 0.0 --seed 123 --stats --allPlots --IgnitionRad 5 --grids --combine  

		- Working Directory: $(MSBuildProjectDirectory)\..

NOW YOU CAN PRESS PLAY AND DEBUG THE COMPILING BINARY!

## Setup Qgis Environment

- Donwload Qgis with OsGeo4W 
	- https://www.qgis.org/en/site/forusers/alldownloads.html#osgeo4w-installer
	- https://download.osgeo.org/osgeo4w/v2/osgeo4w-setup.exe
	- run the downloaded file
	- select advanced install 
	- select packages : qgis & pip (click over the skip button)

- Install requirements on qgis python
	- win button -> type "osgeo4wshell" > open file location > open as administrator
	- C:\OSGeo4W>pip install -r C:\Users\fdo\Source\repos\cell2fire\cell2fire\requirements.txt
	- Install binary distribution of imread from [this repo](https://www.lfd.uci.edu/~gohlke/pythonlibs/#imread). 
	- Tested with `imread‑0.7.4‑cp39‑cp39‑win_amd64.whl`
		- `pip install c:\Users\fdo\Downloads\imread-0.7.4-cp39-cp39-win_amd64.whl`

- Setup the same python as qGis on the system (for testing)
	- open folder C:\OSGeo4W\apps\Python39
	- doble click python.exe
	- read the python version : 3.9.5 to install
	- Open powershell
		- $ winget search python
		- copy id corresponding to the python version
		- $ winget install Python.Python.3.9
		- a new shell will reflect the changes (test python -V on a new shell)