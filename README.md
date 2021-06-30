# Initialization
1. Install PlatformIO
2. run ```git submodule update --init --recursive``` to init submodule
3. Flash the code with PlatformIO

# Mechanism
The synapse main operation is basically a big loop:
1. Get target state (steer and speed) ```whizz_target``` from raven
2. Move towards that target state, by giving commands to actuators, and monitor current state ```whizz_current```
3. Send payload and current state and any additional data like battery-percentage to raven

![whizz-diagram-full](https://user-images.githubusercontent.com/42895451/85547309-59e46280-b650-11ea-806e-1c8a1485859b.png)
# Code Structure
Entry Point is main.cpp --> stateMachine/stateMachine.cpp
<center>


  | Sub-folder    | Content       |
  | ------------- |-------------|
  | auxiliary     | - Lights, fan, battery |
  | comms      | - Sending data to Raven<br/>- Getting target state from Raven |
  | config | - Global Variables/Constants and Pins |
  | stateMachine | - State Machine |
  | utils | - Debug Serial Port (not used in dual vesc) </br> - Signal Processing (Filters/ Sensor Fusion)|
  | vehicle| - Motion, speed and steer|

</center>

