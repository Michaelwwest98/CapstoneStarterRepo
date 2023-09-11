# Wireless Communication Subsystem

## Functionality- 
The function of the wireless communication subsystem is to wirelessly transport data from the computing system to the user interface subsystem quickly and over a long distance. 

## Constraints- 
| Constraint | Source |
|------------|--------|
| 1. The maximum distance the sensing system can be away from the command center is 9 kilometers | Analyzed from DARPA's constraints |
| 2. The system shall send results from the computing subsystem to user interface subsystem at a maximum time of two seconds | Analyzed from DARPA's constraints |
| 3. The entire system shall weigh less than six pounds| From conceptual design |
| 4. Unlicensed devices that operate in the 915 MHz band allow for a maximum power output of up to 30 dBm or 1 Watt | From Federal Communications Commission (FCC) |
| 5. The bandwidth of the device must be 125 kHz or 500 kHz | From further analysis of the subsystem |
| 6. The system must be able to transmit a data packet at the size of at least 30 bits of data | From further analysis of the subsystem |

Since DARPA does not specifiy a minimum distance that the drone can be away from the command center, a value had to be calculated to determine this distance. This calculation was found by analyzing the drone chosen to hold the entire sensing system from the conceptual design. Assuming the drone holds the max payload of six pounds, the drone has a battery life of approximately thirty minutes. The max speed of the drone while carryign the max payload of six pounds as well as some consideration for wind resistance is approximately ten meters-per-second. In this calculation, it will be assumed that the drone will cover a circular area with the command center of the drone being at the center of the circle. The maximum distance the drone can travel with a maximum payload and a speed of ten meters-per-second while also being able to return to the command center with one charge of the battery is nine kilometers.

The RAK811 transceiver has a very high sensitivity of -148 dBm, enabling it to transmit data over extremely long distances. This high sensitivity allows the transceiver to receive signals that have become very weak after traveling a great distance.

## Schematic- 

![Newer Schematic](https://github.com/Michaelwwest98/DARPA-Drone-Triage-Sensing-System/assets/123600489/93efebfa-8629-47f7-8946-5c98d0226c97)

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

2. The data that will be sent from the computing system to the user interface will be composed of measurements obtained from the sensing subsystem as well as a simple graphic that displays the START status of a person. This data will most likely hold a data size of at least several kilobytes. The RAK811 has an average data rate of 300 kbps. Using this radio frequency module with an average data rate of 300 kbps,  the data from the computing subsystem will be able to reach the user interface subsystem within the two second minimum time frame specified in the constraints.

3. After choosing a specific drone and calculating the allotted weight that the team has, the entire sensing system as a whole must weigh less than six pounds. The weight of the RAK811 LPWAN breakout module the RAKDAP1 debug and flash tool that will be attached to the sensing system weighs approximately 24.4 grams or 0.0538 pounds. This light weight load of this component will have little affect on the overall weight of the system.

4. The RAK811 Breakout Board operates in the 915 Mhz band and the maximum power output that the RAK811 Breakout Board is 100mW or 20 dBm, which falls below the safety standard set by the FCC concerning maximum power output of an unlicensed device operating in the 915 MHz frequency band.

5. The RAK811 Breakout board as previously stated, must operate in the 915 MHz band which is the frequency band for United States. This means the bandwidth that is required for the device is either 125 kHz or 500 kHz. On the RAK811 data sheet, it does not specify a specific bandwidth that the device possesses. All that is stated on the data sheet is that the RAK811 Breakout Board supports US915 or the 915 MHz frequency band that the United States typically uses. This means that the RAK811 Breakout Board will be able to fulfill the required bandwidth of 125 kHz or 500 kHz.

6. The RAK811 Breakout Board will be sending data to and from the computing subsystem to the user interface subsystem. The size of data that will be sent from the computing subsystem to the user interface subsystem and back will approximately be around 30 bits. The maximum payload size that the RAK811 transceiver can send in one data packet is 52 bytes which is signifacntly greater than the needed amount. 

## BOM-

| Name of item | Description | Part Number | Manufacturer | Quantity | Price | Total |
|--------------|-------------|-------------|--------------|----------|-------|-------|
| RAK811 LPWAN Breakout Module  | LoRa Transceiver Module with Antenna | 316000 | RAK | 2 | $15.00 | $30.00 |
| RAKDAP1 | Debug and flash tool | 910009 | RAK | 2 | $10.00 | $20.00 |
| Laptop | Laptop will be provided by team members | | | 1 | $0 | $0 |
| Total |  |  |  |  |  | $50.00 |
