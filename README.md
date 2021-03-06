# TCAS SIM

The code is structured into 4 independent applications: the autopilot, the TCAS, the motion simulator and radar.

## Compile
These executables are obtained by compiling, respectively: "auto_pilot.cpp", "TCAS.cpp", "motion.cpp" and "radar.cpp".

To do it in gcc create a folder in the main directory and command:

*g++ -std=c++11 -g -Iinclude ../Autopilot/auto_pilot.cpp ../Airplane/airplane.cpp ../Checksum/checksum.cpp ../Converts/converts.cpp ../Autopilot/determine_velocity.cpp  -o autop*

*g++ -std=c++11 -g -Iinclude ../Motion/motion.cpp ../Checksum/checksum.cpp ../Converts/converts.cpp ../Autopilot/determine_velocity.cpp ../Airplane/airplane.cpp -o simulator*

*g++ -std=c++11 -g -Iinclude ../TCAS/TCAS.cpp ../Checksum/checksum.cpp ../Airplane/airplane.cpp ../Converts/converts.cpp   -o tcas*

*g++ -std=c++11 -g -Iinclude ../Radar/radar.cpp ../Airplane/airplane.cpp ../Converts/converts.cpp ../Checksum/checksum.cpp   -o radar*


## Run
To run the program in separate terminal windows run each of the executables. (ONLY ON UNIX SYSTEMS)
Each airplane is composed by all four executables that communicate with each other accordingly.

To run a different airplane the ports should be changed not to interfere with each other. For example:

*./autop 9004 9001* 

*./mux 9003 9004 9005* 

*./radar 9000* 

*./tcas 9000 9005 9006* 

*./simulator 9003 9001*

*./preout 9001 9002*

(Should choose the ports as the example above. Correspondence and order.)

The path choosen can be edited in the file flight.path that is in the autopilot directory.  Each line is a waypoint as follows
Latitude(deg) Longitude(deg) Altitude(m) Airspeed(knots) VerticalSpeed(ft/min)




**NOTE:**
This is not quite polished for general use, hence the complicated running steps and not perfect end product.
**NOTE:**
This version is undergoing some changes so it is not very clean right now.
