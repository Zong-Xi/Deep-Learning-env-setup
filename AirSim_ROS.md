# AirSim + ROS Wrapper on different machine
- AirSim project (.exe file) on Windows (win10)
- ROS-melodic on Ubuntu18.04

## Setup 
- udp address in `settings.json` (the machine ip that running ros)
- localhost address in `settings.json` (the machine ip that running Project.exe)
- the setting file need to be the same in windows machine and ubuntu machine
  - windows: (default) C:\Users\user_name\Documents\AirSim\settings.json)
  - ubuntu: (default) ~/Documents/AirSim/settings.json
  - if the setting file didn't exit in ubuntu folder, just create it 
  
## Build Tutorial and Setting Reference
- [tutorial](<https://microsoft.github.io/AirSim/airsim_ros_pkgs/>)
- [reference1](<https://github.com/microsoft/AirSim/issues/2954>)
- [reference2](<https://github.com/microsoft/AirSim/issues/2850>)
