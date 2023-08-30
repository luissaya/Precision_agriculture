# Precision Agriculture
Design of an IoT device for agriculture properties tracking.  
[Sensors](./docs/sensors.md)
## General Structure
The hole system is designed in two parts, the first is one *Gateway* that upload data to the cloud and the second is the *Node*. Various Nodes can feed the gateway with data from sensors.  
![overview](./diagrams/overview.png)
## Gateway
Receive the data from the Node and is preprocessed to be sent to the cloud through LTE, Ethernet or WiFi.
![gateway](./diagrams/gateway.png)
## [Node](./docs/Node.md)
Retrieve the data from sensors and send through Lora to the Gateway.
![node](./diagrams/node.png)  
Note: *for indoor independent functionality the Lora module would be replaced for an WiFi module.*

