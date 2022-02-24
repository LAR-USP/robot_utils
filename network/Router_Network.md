# Use a Router to connect the Robot and other computers

### Connect the robot to the Router's network. 

If you have access to a GUI, you can set this up as a normal Wi-Fi connection
If you don't, you may need to access the robot through SSH using the access point or set up the network config when flashing the computer

#### Env vars that need to be set on the robot

Check the robot's IP address using `ifconfig`

You can use `nmap -sP 192.168.x.0/24` to search all devices connected to the network.

```
export ROS_IP=ROBOT's IP
export ROS_MASTER_URI=http://BASE_STATION_IP:11311
```

#### Create a .sh file to automate this

```
#!/bin/sh
ROS_IP=ROBOT's IP
ROS_MASTER_URI=http://BASE_STATION_IP:11311
```

Other computers that will not run `roscore` will have a similar setup.

#### Env vars that need to be set on the Base Station computer

```
export ROS_IP=BASE_STATION_IP
export ROS_MASTER_URI=http://ROS_IP:11311
```

Similarly, you can create a .sh file to automate this

```
source /path/to/env.sh
roscore
```
