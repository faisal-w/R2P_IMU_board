IMU MODULE
---------------------

This is an IMU module featuring a MEMS gyro, a MEMS accelerometer and an optional magnetometer sensor.
The IMU module is supposed to work together with other smart modules, publishing data on CAN bus using a publish/subscriber QoS enabled middleware (in development).
The overall system should provide the devices and functionalities commonly used in robot prototyping, speeding up the development process and reducing the engeenering time, leaving more time to research activities. The system is supposed also to enable students and amateurs to easily build robots without advanced hardware knowledge.

### Hardware

The IMU module is run by a STM32 ARM Cortex-M3 microcontroller, that takes care of reading sensors data, filtering them to extract accurate pose and attitude measurements, and then publishing the needed data on a CAN bus network and, optionally, on a TTL UART interface.

Inertial data in gathered from three sensors:
- a ST LIS3DH 16-bit digital accelerometer
- a ST L3G4200D 16-bit digital gyroscope
- an optional LSM303DLHC 16 bit accelerometer and magnetometer

The magnetometer sensor is in "preview" status at the time of writing, thus we decided to include its footprint on the board to exploit it when it will available.

The accelerometer and the gyroscope communicates with the microcontroller by SPI, while the accelerometer and magnetometer sensor relies on I2C bus.

Modules are connected together by a single cable, that transports CAN signals as while as 5V power. Each module as two ports, enabling chain connections.

A double connector footprint (RJ45 + pin header) is provided, so the user can choose which cabling fits better his needs:
- RJ45 has been chosen as it provides shielded twisted wires for 1Mbit CAN networking in harsh environments and cables are easy to find.
- pin header has been chosen to give also an space saving and simple connection when modules are closed placed and RJ45 jack/plug pairing space is a problem. This header also enables using the IMU module outside our framework, interfacing with it through a simple TTL UART interface.

The four status LEDs are placed under RJ45 plug light pipes entrance, so it is only needed to solder the preferred connector without other layout changes.

The left connector has the option to connect to the CAN bus or to expose the TTL UART interface by a solder jumper placed on the bottom of the board.

# Firmware

...under development