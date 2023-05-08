# Telemetry-for-DAQ
This repo holds telemetry sender and receiver code for Data Aquisition.

TRANSMITTER:

The telemetry sender in the code is implemented using the SoftwareSerial library and a struct named TelemetryData. The struct is defined to hold the telemetry data that will be transmitted. The struct has the following fields:

mctempmotor: a double value representing the motor temperature in degrees Celsius.
mctempcontroller: a double value representing the controller temperature in degrees Celsius.
pack_current: a double value representing the current flowing in the battery pack in amperes.
pack_inst_voltage: a double value representing the instantaneous voltage of the battery pack in volts.
state_of_charge: a double value representing the percentage of charge left in the battery pack.
high_temp: a double value representing the highest temperature recorded in the battery pack in degrees Celsius.
low_temp: a double value representing the lowest temperature recorded in the battery pack in degrees Celsius.
The telemetrySerial is initialized as a SoftwareSerial object with pin 10 as the receive pin and pin 11 as the transmit pin. In the loop(), the telemetry data is read from the CAN bus and assigned to the corresponding fields of the TelemetryData struct. The struct is then transmitted over the telemetrySerial using the following format:

"motor_temp: controller_temp: pack_current: pack_voltage: state_of_charge: high_temp: low_temp"

The values for each field are separated by colons (:) and there are no spaces between the values. The telemetry data is sent once every second using the delay() function.

RECEIVER:

Receiver code defines a struct to hold telemetry data and reads it from a software serial port. The telemetry data contains information about the temperature, current, voltage, state of charge, and other parameters of a motor controller and battery pack.

The setup() function initializes the serial ports for debugging and telemetry data transmission.

The loop() function checks if a full telemetry packet has been received by the software serial port. If a full packet is available, it is read into a byte array and then decapsulated into a TelemetryData object using the memcpy function.

The received telemetry data is then printed to the serial port for debugging purposes, and can be used to do something else in the code as well.

Overall, this code provides a basic example of how to read telemetry data from a software serial port and use it to monitor and control a motor controller and battery pack.






