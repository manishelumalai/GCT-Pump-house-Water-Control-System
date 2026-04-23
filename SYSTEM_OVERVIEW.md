System Configuration
The system communicates using the MQTT protocol over a 4G network connection provided by the SIM7600 modem. It connects to a cloud-based MQTT broker and exchanges data through predefined topics.
The OHT and UGT status are published to their respective MQTT topics whenever there is a change in water level. The pump is controlled by subscribing to a dedicated MQTT topic, where commands such as ON and OFF are received and executed.
The system also publishes its connection status using a dedicated topic to indicate whether the device is online or offline.

Operational Logic
The float sensors are configured using internal pull-up resistors. The logic is defined such that when the sensor reads LOW, the tank is considered FULL, and when it reads HIGH, the tank is considered EMPTY.
To avoid false triggering due to noise or fluctuations, a debounce mechanism with a delay of 1000 milliseconds is implemented. This ensures that only stable changes in sensor readings are considered.
The pump is controlled through a relay interface. When a command is received via MQTT, the system switches the relay accordingly. Since the relay is active LOW, setting the control pin to LOW turns the pump ON, and setting it to HIGH turns it OFF.

Connectivity and Reliability
The firmware is designed using a non-blocking approach to ensure continuous monitoring and operation. It uses time-based scheduling to perform different tasks such as sensor reading, network maintenance, and MQTT communication.
The system continuously monitors the network and MQTT connection. If a disconnection occurs, it automatically attempts to reconnect. The reconnection attempts use a gradual backoff mechanism to avoid excessive retries.
Periodic maintenance routines are included to keep the modem and communication stable over long durations. The system also performs regular checks on network connectivity and restores the connection if needed.

Timing Parameters
The debounce delay for sensor readings is set to 1000 milliseconds to ensure stable detection.
The MQTT keepalive interval is configured to 30 seconds to maintain an active connection with the broker.
The modem maintenance routine runs at regular intervals of 15 seconds to prevent network drop.
MQTT reconnection attempts start with a short delay and gradually increase up to a maximum limit to ensure efficient recovery.
A periodic connection refresh is performed approximately every one hour to maintain communication stability.
A modem reset routine is triggered at longer intervals, typically around six hours, to ensure long-term reliability.
The network connectivity is checked at regular intervals of 30 seconds to detect and recover from connection issues.

Power and Interface Notes
The system requires a stable power supply to ensure proper functioning of both the Bharat Pi board with the modem.
A valid SIM card with an active data plan is required for 4G connectivity.
The relay module should be properly interfaced to safely control the pump, and necessary isolation precautions should be taken.
Float sensors should be installed securely in the tanks to ensure accurate and reliable water level detection.
