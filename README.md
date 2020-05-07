# BSDC-Ardupilot_and_Mavros
The mavros_msgs package is taken as it is from mavros. It contains all required msg and srv files.
The mavros_py package includes launch, scripts, waypointfiles folders.

The launch folder contains apm.launch, which is used to launch mavros topics and services. Note that this apm.launch is edited accordingly so that it can connect with ardupilot sitl, as mentioned in docs (FCU ID).

The scripts folder contains the python scripts of which mavarm, mavmode, mavtakeoff are subsidiary files. mavmission.py is main file which coordinates whole mission from start to end.

The scripts folder also contains the pymavlink folder containing python files which use the pymavlink package to coordinate the  mission.

## Order of execution of files:
1.  sim_vehicle.py -v ArduPlane --console --map (In Terminal 1)
2.  (Wait for the map to open.)
3.  (source the workspace (In Terminal 2))
4.  Roslaunch mavros apm.launch (In Terminal 2)
5.  (source the workspace (In Terminal 3)
6.  rosrun mavros (name of whichever mission py file to be run here)

In Step 6 above, the py file to be run can be different, and depends on the method chosen (pymavlink or Mavros)

## For PyMavlink
There are two important files here mission.py and dynamicwp.py. First run mission.py which uses waypoint file waypoint2.txt. Then in the middle of the ongoing mission run dynamicwp.py file which uses waypoint3.txt. Thus plane pauses current ongoing mission and starts new mission, complete it  first and then resume original mission. (In Step 6 of the Above)

## For Mavros
Use the mavmission.py file in Step 6 above
