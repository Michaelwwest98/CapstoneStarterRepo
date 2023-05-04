# Wireless Communication Subsystem

## Functionality- 
The function of the wireless communication subsystem is to wirelessly transport data from the computing system to the user interface subsystem quickly and over a long distance. 

## Constraints- 
| Constraint | Source |
|------------|--------|
| 1. The maximum distance the sensing system can be away from the command center is 9 kilometers | Analyzed from DARPA's constraints |
| 2. The system shall send results from the computing subsystem to user interface subsystem at a maximum time of two seconds | Analyzed from DARPA's constraints |
| 3. The entire system shall weigh less than six pounds| From conceptual design |

Since DARPA does not specifiy a minimum distance that the drone can be away from the command center, a value had to be calculated to determine this distance. This calculation was found by analyzing the drone chosen to hold the entire sensing system from the conceptual design. Assuming the drone holds the max payload of six pounds, the drone has a battery life of approximately thirty minutes. The max speed of the drone while carryign the max payload of six pounds asw well as some consideration for wind resistance is approximately ten meters-per-second. In this calculation, it will be assumed that the drone will cover a circular area with the command center of the drone being at the center of the circle. The maximum distance the drone can travel with a maximum payload and a speed of ten meters-per-second while also being able to return to the command center with one charge of the battery is nine kilometers.

## Schematic- 



| RAK811 LoRa Breakout Board PINOUT |---|
|-----------------------------------|---|
| Pin Number | Description |
| 1 | 3.3 V |
| 2 | UART1_TXD |
| 3 | UART1_RXD |
| 4 | PB12 |
| 5 | RST |
| 6 | PA3 |
| 7 | PB5 |
| 8 | PA15 |
| 9 | BOOT0 |
| 10 | GND |
| 11 | PA0 |
| 12 | PA1 |
| 13 | SWCLK |
| 14 | SWDIO |
| 15 | PB11 |
| 16 | PB15 |
| 17 | PA2 |
| 18 | PA13 |
| 19 | PA12 |
| 20 | PB14 |

## Analysis-
1. The wireless communication method that will be chosen for this project shall be radio frequency. This will be accomplished by a LoRa radio frequency module that is compatible with the jetson nano, which will be the computing system of the project. The computing system will have a RAK811 LPWAN Breakout Module attached to it. The other transceiver will be attached to a USB to UART converter which will then be connected to a laptop to allow for communication between the computing system and the user interface.  With an antenna which is provided, the range of this transceiver is 15 kilometers, which fulfills the constraint of a 9 kilometer distance.

2. The data that will be sent from the computing system to the user interface will be composed of measurements obtained from the sensing subsystem as well as a simple graphic that displays the START status of a person. This data will most likely hold a data size of at least several kilobytes. The radio frequency module chosen for this project has an average data rate of 300 kbps. Using this radio frequency module with an average data rate of 300 kbps,  the data from the computing subsystem will be able to reach the user interface subsystem within the two second minimum time frame specified in the constraints.

3. After choosing a specific drone and calculating the allotted weight that the team has, the entire sensing system as a whole must weigh less than six pounds. The weight of the NRF24L01+PA+LNA radio frequency module including the antenna that will be attached to the sensing system weighs approximately 16 grams or 0.035274 pounds. This light weight load of this component will have little affect on the overall weight of the system.

## BOM-

| Name of item | Description | Part Number | Manufacturer | Quantity | Price | Total |
|--------------|-------------|-------------|--------------|----------|-------|-------|
| LPWAN Breakout Module  | LoRa Transceiver Module with Antenna | RAK811 | RAK | 2 | $15.00 | $30.00 |
| (FTDI) USB to UART Converter | USB to UART Converter | Cytron | UC00A | 1 | $10.25 | $10.25 |
| Laptop | Laptop will be provided by team members | | 1 | $0 | $0 |
| Total |  |  |  |  |  | $40.25 |
