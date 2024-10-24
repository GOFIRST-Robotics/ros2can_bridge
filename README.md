## ROS 2 to CAN Bridge

# Overview

For easy access to the CAN bus, a bridge between ROS 2 topics and the CAN bus was implemented. The CAN Bus is included in the Linux operating system as a network socket with the socket CAN driver. Therefore the CAN bus is included in the software similar to an Ethernet socket using the “asio” library. The node functions as a bidirectional bridge that listens to the CAN bus and publishes the received messages to a ROS 2 topic called:

- "CAN/" + CAN socket name + "/receive"

Equally the messages on a ROS 2.0 topic called:

- "CAN/" + CAN socket name + "/transmit"

are monitored and forwarded to the CAN bus. Examples of the topic names are:

- "CAN/can1/receive"
- "CAN/can0/transmit"

The topic names are structured in 2 field names and the transmit and receive topic. The first field name “CAN” identifies the topic within ROS 2 as a CAN Topic. The ‘CAN socket name’ identifies the CAN bus within a building block, because multiple CAN buses can be connected. A ROS 2 to CAN Bridge node is always coupled to one CAN bus.

# Build this Package

```
sudo apt install ros-${ROS_DISTRO}-can-msgs
colcon build --packages-select ros2socketcan_bridge
```

# Usage

The ros2 CAN bridge can be run using the command:

```
ros2 run ros2socketcan_bridge ros2socketcan
```

By default, it will start the CAN Bridge with the CAN socket "can0".

<ins>Note:</ins> This ROS node is meant to be used on a Linux machine and may not work with other operating systems!

# ROS2 Message Type

The message type used for topics is the ROS2 "can_msgs/msg/Frame" message type.
