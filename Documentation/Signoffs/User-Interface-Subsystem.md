# User Interface Subsystem

## Functionality

The function of this subsystem is to take the data from the wireless communication between the Jetson Nano and a computer, and then to display the data in an intuitive manner that is useful for responders. Intuitiveness in this regard means that the user interface of the system is to be specifically designed to make it easier for responders to use the system and keep track of relevant data. Data that will be displayed includes the following: triage results, heartbeat, and respiratory rate data. Triage results should be prioritized as the main result being displayed with heartbeat data and respiratory data being displayed as secondary data to help responders understand why the triage algorithm assigned that specific triage result to the victim and so that responders may act with more certainty quickly and effectively to help the victim that needs the quickest response first.

## Specs and Constraints Table

| Description | Constraint | Source |
|-------------|------------|--------|
| Display triage results | Must display whether the victim is in the Expectant, Immediate, or Delayed category | From START Method [1] |
| Display heartbeat data | Shall display victim’s heartbeat in beats per minute | From Conceptual Design, from Heartbeat and Respiratory Subsystem section |
| Display respiratory data | Shall display victim’s breath rate in breaths per minute | From Conceptual Design, from Heartbeat and Respiratory Subsystem section |

## Block Diagram
![UI_Block_Diagram_1](https://github.com/Michaelwwest98/DARPA-Drone-Triage-Sensing-System/blob/cc92902a6190693c7c66fbc01ece6b466e08f3d2/Documentation/Images/UI_Block_Diagram_1.JPG)


## Analysis
Pictured above is the block diagram for the UI for the program that will show the user the output data from the algorithm. The data will be shown to the user via a Python script [2] that creates an intuitive table of the relevant data listed in the Specs and Constraints section. The main result will be the necessary data from the Computing Subsystem sent via the Wireless Communication Subsystem to output the victim's triage result onto the screen: the sorting status of the victim, whether they are Expectant, Immediate, or Delayed as described in the START Method [1]. This data will be taken through the Wireless Communication Subsystem from the Computing Subsystem in the Jetson Nano, as described in the Computing Subsystem and Wireless Communication Subsystem signoffs respectively. This data will be shown so that responders will know which victim needs help the quickest, according to the triage algorithm in the Jetson Nano. Secondarily, the two less prominent outputs for the UI would be the average measured heartbeat in beats per minute (bpm) and the average measured respiratory rate in breaths per minute (bpm) taken from the Computing Subsystem. This data will be taken from the Jetson Nano instead of being taken directly from the radar, as the Jetson Nano will be the device directly connected to the computer running the UI Subsystem Python program. The Python program will take a sample of heartbeat and respiratory rate data, do the necessary calculations to average them out, and then display them to the user. This data will be important so that responders can get a quick look at the data that leads to the triage result that will also be shown on-screen and they can help the victim that needs the quickest attention with more certainty. The specific computer used for the UI Subsystem Python program will be incidental, as the input from the Wireless Communication Subsystem is connected via USB as described in more detail in the Wireless Communication Subsystem signoff. The triage result as well as the secondary data will be static data. The triage result will be shown as a static result because it is a final result. An average respiratory rate and heartbeat will show the user whether each respective rate is normal, too high, or too low. This will allow the user to gain a decent understanding of why the victim is given their specific triage result.

## BOM
| Name of item | Description | Part Number | Manufacturer | Quantity | Price | Total |
|--------------|-------------|-------------|--------------|----------|-------|-------|
| N/A | N/A | N/A | N/A | N/A | $0 | $0 |
|Total |  |  |  |  |  | $0 |

## Sources
[1] “Start adult triage algorithm,” CHEMM. [Online]. Available: https://chemm.hhs.gov/startadult.htm. [Accessed: 14-Feb-2023].

[2] “The python tutorial,” Python documentation, https://docs.python.org/3/tutorial/index.html (accessed Sep. 5, 2023). 
