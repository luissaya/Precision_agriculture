# Electrical Power system
Design reference: [Quetzal](https://github.com/Quetzal-1-CubeSat-Team/quetzal1-hardware/tree/master/EPS)  
![energy](../diagrams/energy.png)  
## Energy harvesting
* MPTT charger: for solar panels
* Voltage current monitor: for solar panels
* Ideal diode: supply current to *Energy storage*
  - Device: TC4352IMS#TRPBF - Low Voltage Ideal Diode Controller with Monitoring
  
## Energy storage
* Battery protection: limit current from solar panels
  - Device: TPS2551QDBVRQ1 - ADJUSTABLE CURRENT LIMITED POWER DISTRIBUTION SWITCH
* Battery monitoring: sense current from solar panels
  - Device: BQ27441DRZR-G1A - System-Side Impedance Track™ Fuel Gauge
  - operates with supplies from 2.9V to 18V
* Voltage protection: limit current that supply *Power distribution* 
  - Device: TPS2551QDBVRQ1 - ADJUSTABLE CURRENT LIMITED POWER DISTRIBUTION SWITCH
  - Adjustable Current-Limit: 100 mA to 1100 mA
  - Reverse Input-Output Voltage Protection
  - Operating Range: 2.5 V to 6.5 V
  - 15-kV ESD Protection (With External capacitance)
## Power distribution
* Voltage monitor: Sense the voltage that comes from of the battery.
* Voltage regulators:
  - 3.3 Volts: Supply energy for the microcontroller and general signal circuits.
  - 5 Volts: Supply energy for the I2C devices
  - 12 Volts: Supply energy for the RS485 devices
## Energy calculation
Maximum energy consumption:
- RS485 sensors: 0.5W(12V, 41.7mA / 5V, 100mA)
- I2C sensors: 0.1W(3.3V, 30.3mA), 0.6W(120mA, 5V)
- STM32F7 with all peripherals: 200mA, 3.3V
- Lora1278-C1 140mA, 3.3V
- ESP32-C3 350mA, 3.3V

Power energy of voltage regulator:
- 3.3V : 750mA <> 350 + 200 + 140 + 2x30.3
-   5V : 450mA <> 2x100 + 2x120 
-  12V : 130mA <> 3*41.7

Characteristics:
- Up to 3 RS485 sensors(up to 3 x 12V and 2 x 5V ): 1.5W
- Up to 2 I2C ( 3.3V or 5V): 0.2W/1.2W
- WiFi or Lora wireless communication: 1.15W/0.46W

Battery dimensioning:

WiFi|Configurations  | RS485 |  I2C  | Total Power(W)|
----|----------------|-------|-------|---------------|
----|  Max demand    |   3   | 2(5V) |    3.85       |
----|  All RS485     |   3   |   0   |    2.65       |
----|  All I2C       |   0   | 2(5V) |    2.35       |
----|Min demand RS485|   1   |   0   |    1.55       |
----| Min demand I2C |   0   |1(3.3V)|    1.35       |

Lora|Configurations  | RS485 |  I2C  | Total Power(W)|
----|----------------|-------|-------|---------------|
----|  Max demand    |   3   | 2(5V) |    3.16       |
----|  All RS485     |   3   |   0   |    1.96       |
----|  All I2C       |   0   | 2(5V) |    1.66       |
----|Min demand RS485|   1   |   0   |    0.86       |
----| Min demand I2C |   0   |1(3.3V)|    0.66       |

  
- power: 3.85W(5 sensors and wifi), 1W(1 sensor RS485 and Lora) 
- battery: 10AH(4.2V)= 42WH
- duration:  10.9hour / 42hour
- solar panel: 