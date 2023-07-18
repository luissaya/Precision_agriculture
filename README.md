# Precision Agriculture
Design of an IoT device for agriculture properties tracking.

## General Structure
The hole system is designed in two parts, the first is one gateway that upload data to the cloud and the second are the Nodes various devices that feed the gateway with data from sensors.
![overview](./diagrams/overview.png)
### Gateway
Receive the data from the Node and is preprocessed to be sent to the cloud through mobile network or WiFi.
![gateway](./diagrams/gateway.png)
### Node
Retrieve the data from sensors and send through Lora to the Gateway.
![node](./diagrams/node.png)