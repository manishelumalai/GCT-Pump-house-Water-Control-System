The GCT Pump House IoT System is a smart water monitoring and pump control solution developed using a Bharat Pi (ESP series microcontroller with 4G connectivity). It is designed to automate the management of water levels in an Overhead Tank (OHT) and an Underground Tank (UGT) using float sensors.

The system continuously monitors the tank levels and publishes their status (FULL/EMPTY) to an MQTT broker, enabling real-time remote monitoring through an IoT MQTT mobile application. In addition to monitoring, the system allows users to remotely control the water pump by sending ON/OFF commands via MQTT, which are executed through a relay interface.

The firmware is built for stable and reliable operation, using non-blocking logic for continuous execution and debounce handling for accurate sensor readings. It also includes automatic reconnection and recovery mechanisms to handle network or communication interruptions, ensuring consistent performance in practical deployment environments.

This project provides an efficient IoT-based approach to automate pump house operations, minimizing manual intervention while improving reliability and ease of monitoring.
