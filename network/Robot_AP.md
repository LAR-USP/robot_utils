### ROS communication between robot and base station using the robot as an Acess Point

#### Create access point hotspot from your Robot's computer

TODO: ADD IMAGES

#### Env vars that need to be set on the robot

```
export ROS_HOSTNAME=$(hostname).local
export ROS_MASTER_URI=http://$ROS_HOSTNAME:11311
```

#### Create a .sh file to automate this

```
#!/bin/sh
ROS_HOSTNAME=$(hostname).local
ROS_MASTER_URI=http://$ROS_HOSTNAME:11311
```

#### Run ROS Core on the Robot

```
source /path/to/env.sh
roscore
```

#### Env vars that need to be set on your computer

First, access the Wi-Fi network the robot created and check your IP address with `ifconfig`

```
export ROS_IP=YOUR_IP
export ROS_MASTER_URI=http://ROBOT_IP:11311
```

`ROBOT_IP` will probably be `10.42.0.1`.

Similarly, you can create a .sh file to automate this


```
source /path/to/env.sh
rostopic list # you should be able to conect to Master and view the existing topics
```
