IMU MODULE
---------------------

This is an IMU module featuring a MEMS gyro, a MEMS accelerometer and an optional magnetometer sensor.
The IMU module is supposed to work together with other smart modules, publishing data on CAN bus using a publish/subscriber QoS enabled middleware (under development).
The overall system should provide the devices and functionalities commonly used in robot prototyping, speeding up the development process and reducing the engeenering time, leaving more time to research activities. The system is also supposed to enable students and amateurs to easily build robots without advanced hardware knowledge.

### Hardware

![Alt text](https://github.com/openrobots-dev/IMU/raw/master/IMU%20rev1.0.png)

The IMU module is run by a STM32 ARM Cortex-M3 microcontroller, that takes care of reading sensors data, filtering them in order to to extract accurate pose and attitude measurements, and then publishing the needed data on a CAN bus network and, optionally, on a TTL UART interface.

Inertial data in gathered from three sensors:

- a ST LIS3DH 16-bit digital accelerometer
- a ST L3G4200D 16-bit digital gyroscope
- an optional LSM303DLHC 16 bit accelerometer and magnetometer

As the magnetometer sensor is in "preview" status at the time of writing,  we decided to include its footprint on the board in order to exploit it when available.

The accelerometer and the gyroscope communicates with the microcontroller by SPI, while the accelerometer and magnetometer sensor relies on I2C bus.

Modules are connected together by a single cable, that transports CAN signals and 5V power. Each module has two ports, enabling chain connections.

A double connector footprint (RJ45 + pin header) is provided, so the user can choose which cabling fits better his needs:

- RJ45 has been chosen as it provides shielded twisted wires for 1Mbit CAN networking in harsh environments and cables are easy to find.
- pin header has been chosen to also give a space saving and simple connection when modules are close and RJ45 jack/plug pairing space is a problem. This header also enables using the IMU module outside our framework, accessing it through a simple TTL UART interface.

The four status LEDs are placed under RJ45 plug light pipes entrance, so it is only needed to solder the preferred connector without any other layout changes.

The left connector has the option to expose the TTL UART interface, instead of the CAN bus interface, by a solder jumper placed on the bottom of the board.

### Firmware

...under development