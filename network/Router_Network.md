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

#### Using ifmetric to set network priority

First see the metrics using route command:

```
$ route -n

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.42.0.1       0.0.0.0         UG    100    0        0 eth0
0.0.0.0         10.42.0.2       0.0.0.0         UG    600    0        0 wlan0
```

Here, eth0 has lower metric, so it will be preferred over wlan0. If you want to prefer wlan0, then lower its metric:

```
sudo ifmetric wlan0 50
```

```
$ route -n

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.42.0.2       0.0.0.0         UG    50     0        0 wlan0
0.0.0.0         10.42.0.1       0.0.0.0         UG    100    0        0 eth0
```

[Adapted From Here](https://superuser.com/questions/331720/how-do-i-set-the-priority-of-network-connections-in-ubuntu)




