# Running AirSim on two machine
### Description
- when training drone using reinforcement learning in Ubuntu18.04, UE4 sometimes break or shut down
- the lab server(Ubuntu 18.04) is much more powerful than my own computer
- win10 for drone rendering, and training script on ubuntu

### Need to create a client from ubuntu to win10
- check the ip address for both win10 and ubuntu
- change the setting.json in win10

### Setting.json file
- "LocalHostIp": win10 local ip -> 127.0.0.1
- "UdpIp": "ubuntu ipve address"

### Testing Result
- success
- but need to trun off the Windows Defender

### Next step
- using ROS_Package for AirSim
