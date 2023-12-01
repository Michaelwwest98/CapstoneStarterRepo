# Wireless Communication Subsystem

## Functionality- 
The function of the wireless communication subsystem is to wirelessly transport data from the computing system to the user interface subsystem quickly and over a long distance. 

## Constraints- 
| Constraint | Source |
|------------|--------|
| 1. The maximum distance the sensing system can be away from the command center is 9 kilometers | Analyzed from DARPA's constraints |
| 2. The system shall send results from the computing subsystem to user interface subsystem at a maximum time of two seconds | Analyzed from DARPA's constraints |
| 3. The entire subsystem shall weigh less than 1.2 pounds| From conceptual design |
| 4. Unlicensed devices that operate in the 902 - 928 MHz band allow for a maximum power output of up to 30 dBm or 1 Watt | From FCC Part 15 Subpart C |
| 5. The device must operate in the United States Unlicensed frequency band that is from 902 - 928 MHz | From FCC Part 15 Subpart D |
| 6. The system must be able to transmit a data packet at the size of at least 30 bits of data | From further analysis of the subsystem |
| 7. The system must be compatible with Linux based computing systems | From further analysis of the subsystem |

Since DARPA does not specifiy a minimum distance that the drone can be away from the command center, a value had to be calculated to determine this distance. This calculation was found by analyzing the drone chosen to hold the entire sensing system from the conceptual design. Assuming the drone holds the max payload of six pounds, the drone has a battery life of approximately thirty minutes. The max speed of the drone while carryign the max payload of six pounds as well as some consideration for wind resistance is approximately ten meters-per-second. In this calculation, it will be assumed that the drone will cover a circular area with the command center of the drone being at the center of the circle. The maximum distance the drone can travel with a maximum payload and a speed of ten meters-per-second while also being able to return to the command center with one charge of the battery is nine kilometers.

The RAK811 transceiver has a very high sensitivity of -148 dBm, enabling it to transmit data over extremely long distances. This high sensitivity allows the transceiver to receive signals that have become very weak after traveling a great distance.

## Schematic- 

![Most_Newest_Scematic](https://github.com/TnTech-ECE/CapstoneStarterRepo/assets/123600489/838026af-3567-4727-9e24-eea32cde70de)

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
1.  The RAK811 transceiver has a range of 15 kilometers, which fulfills the constraint of a 9 kilometer distance.

2. The data that will be sent from the computing system to the user interface will be approximately 30 bits in size according to the designer of the computing subsystem. The RAK811 has an average data rate of 300 kbps.

The amount of time that it will take for 2 data packages to be sent to the computing system to the user interface and back, or sending 30 bits of data back and forth will take 0.0002 seconds with the data rate of 300 kbps that the transceiver possesses.
  
This means that the data from the computing subsystem will be able to reach the user interface subsystem within the two second minimum time frame specified in the constraints.

5.  The weight of the RAK811 LPWAN breakout module the RAKDAP1 debug and flash tool that will be attached to the sensing system weighs approximately 24.4 grams or 0.0538 pounds which is a signaficantly less than the maximum 1.2 pounds the entire subsystem must weigh.

6. The RAK811 Breakout Board operates in the 915 MHz band and the maximum power output that the RAK811 Breakout Board is 100mW or 20 dBm, which falls below the safety standard of 30 dBm or 1 watt set by the FCC Part 15 Subpart C.

7. Since the team does not have a license to operate in certain frequency bands used by the United States, the transceiver must operate in the unlicensed frequency band in the United States which is between 902 MHz and 928 MHz stated by FCC Part 15 Subpart D. According to the RAK811 transceiver datasheet, the transciever operates in the 915 MHz frequency band fulfilling the constraint.

8. The size of data that will be sent from the computing subsystem to the user interface subsystem and back will approximately be around 30 bits. The maximum payload size that the RAK811 transceiver can send in one data packet is 52 bytes which is significantly greater than the needed amount. 

9. Within the RAK811 Quick Start Guide documentation, there is a list specifying the required hardware components needed for the transceiver to function properly. One of these components specified in the list is a Linux computer which means that the RAK811 transceiver is compatible with Linux based systems.
  
From there, you must use a serial port tool to interact with the transceiver. The manufacturer does not seem to provide a serial port tool for Linux, but on a forum on the manufactuer's website, and employee of the manufacturer said on the forum to use a serial port tool called Cutecom. Cutecom is a serial port tool that is able to run on the Raspberry Pi 4 Model B which will be the chosen computing system for the project. This allows the computing system to interact with the RAK811 transceiver.

## BOM-

| Name of item | Description | Part Number | Manufacturer | Quantity | Price | Total |
|--------------|-------------|-------------|--------------|----------|-------|-------|
| RAK811 LPWAN Breakout Module  | LoRa Transceiver Module with Antenna | 316000 | RAK | 2 | $15.00 | $30.00 |
| RAKDAP1 | Debug and flash tool | 910009 | RAK | 2 | $10.00 | $20.00 |
| Laptop | Laptop will be provided by team members | | | 1 | $0 | $0 |
| Total |  |  |  |  |  | $50.00 |
