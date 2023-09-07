# User Interface Subsystem

## Functionality

The function of this subsystem is to take the data from the wireless communication between the Jetson Nano and a computer, then to display the data in an intuitive manner that is useful for responders. Data that should be displayed should include the following: triage results, heartbeat, and respiratory rate data. Triage results should be prioritized as the main result being displayed with heartbeat data and respiratory data being displayed as secondary data.

## Specs and Constraints Table

| Description | Constraint | Source |
|-------------|------------|--------|
| Display triage results | Must display whether the victim is in the Expectant, Immediate, or Delayed category | From START Method [1] |
| Display heartbeat data | Shall display victim’s heartbeat in beats per minute | From Conceptual Design, from Heartbeat and Respiratory Subsystem section |
| Display respiratory data | Shall display victim’s breath rate in breaths per minute | From Conceptual Design, from Heartbeat and Respiratory Subsystem section |

## Block Diagram
![UI_Block_Diagram_1](https://github.com/Michaelwwest98/DARPA-Drone-Triage-Sensing-System/blob/cc92902a6190693c7c66fbc01ece6b466e08f3d2/Documentation/Images/UI_Block_Diagram_1.JPG))


## Analysis
Pictured above is the block diagram for the UI for the program that will show the user the output data from the algorithm. The data will be shown to the user via a Python script that creates an intuitive table of the relevant data listed in the Specs and Constraints [2]. The main result will be the necessary data from the Computing Subsystem sent via the Wireless Communication Subsystem to output the victim's triage result onto the screen: the sorting status of the victim, whether they are Expectant, Immediate, or Delayed as described in the START Method [1]. This data will be taken through the Wireless Communication Subsystem from the Computing Subsystem in the Jetson Nano, as described in the Computing Subsystem and Wireless Communication Subsystem signoffs. Secondarily, the two less prominent outputs for the UI would be the measured heartbeat in beats per minute (bpm) and the measured respiratory rate in breaths per minute (bpm) from the Computing Subsystem. This data will be taken from the Jetson Nano instead of being taken directly from the radar, as the Jetson Nano will be the device directly connected to the computer running the UI Subsystem Python program. The specific computer used for the UI Subsystem Python program will be incidental, as the input from the Wireless Communication Subsystem is connected via USB as described in more detail in the Wireless Communication Subsystem signoff. The triage result as well as the secondary data will be static data. The triage result will be shown as a static result because it is a final result. An average respiratory rate and heartbeat will show the user whether each respective rate is normal, too high, or too low. This will allow the user to gain a decent understanding of why the victim is given their specific triage result.

## BOM
| Name of item | Description | Part Number | Manufacturer | Quantity | Price | Total |
|--------------|-------------|-------------|--------------|----------|-------|-------|
| N/A | N/A | N/A | N/A | N/A | $0 | $0 |
|Total |  |  |  |  |  | $0 |

## Sources
[1] “Start adult triage algorithm,” CHEMM. [Online]. Available: https://chemm.hhs.gov/startadult.htm. [Accessed: 14-Feb-2023].

[2] “The python tutorial,” Python documentation, https://docs.python.org/3/tutorial/index.html (accessed Sep. 5, 2023). 
