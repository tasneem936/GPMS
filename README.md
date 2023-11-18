
# GPMS 
In this project we’ll develop a General-Purpose Modbus Slave (GPMS) library, this library can be used
by device hardware developers to make their device support Modbus protocol.
Let’s assume we need to develop a sensor that detects motion, measure room temperature and turn
On/Off a light (3 parameters in total), as a hardware developer we can use the GPMS software while
adding our own logic so any user can read/write from/to this sensor thought Modbus protocol.

# Design overview
We’ll separate our code to three main components:
- Transport: as we know there is multiple communication options the device might support
e.g., get messages through TCP/IP or RTU (serial port).
We need to provide a flexible way to attach the transport layer.
- Logic: the main logic of the sensor e.g., register 0x0051 is the register which holds the
information of motion/no motion, so the logic will update this register according to the state
of the motion sensor.
- GPMS Manager: general purpose Modbus slave manager will provide the Modbus slave
logic according to the Modbus standard.
For testing we’ll use TCP/IP as a transport and a basic logic that print to a file or read a keyboard
press button and monitor part of our OS parameters.

# GPMS Manager
This is the main part of our project; in this part we should implement all the Modbus functions
according to the Modbus standard.

# Transport
The transport layer responsible for receiving Modbus commands from the outer world and
forwarding it to the GMPS Manager,in this project we’ll support TCP/IP communication.

# Logic
This code component will represent the actual functionality of the hardware, it will reflect any
relevant changes of the Modbus registry table to the actual hardware and vice-versa.
For example, if register 0x0015 of the holding registers table should represent some button state
(ON/OFF) the logic will add a handler to the GPMS Manager.
