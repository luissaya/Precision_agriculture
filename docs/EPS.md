# Electrical Power system
Design reference: [Quetzal](https://github.com/Quetzal-1-CubeSat-Team/quetzal1-hardware/tree/master/EPS)  
![energy](../diagrams/energy.png)  
## Energy harvesting
* MPTT charger: for solar panels
* Voltage current monitor: for solar panels
* Ideal diode: supply current to *Energy storage*
  
## Energy storage
* Battery protection: limit current from solar panels
* Battery monitoring: sense current from solar panels
* Voltage protection: limit current that supply *Power distribution*
  
## Power distribution
* Voltage monitor: Sense the voltage that comes from of the battery.
* Voltage regulators:
  - 3.3 Volts: Supply energy for the microcontroller and general signal circuits.
  - 5 Volts: Supply energy for the I2C devices
  - 12 Volts: Supply energy for the RS485 devices