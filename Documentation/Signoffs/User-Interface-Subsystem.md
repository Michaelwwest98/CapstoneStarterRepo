# User Interface Subsytem

## Functionality

The function of this subsystem is to take the data from the wireless communication between the Jetson Nano and a computer, then to display the data in an intuitive manner that is useful for responders. Data that should be displayed should include the following: triage results, heartbeat, and respiratory rate data. Triage results should be prioritized as the main result being displayed with heartbeat data and respiratory data being displayed as secondary data.

## Specs and Constraints Table

| Description | Constraint | Source |
|-------------|------------|--------|
| Display triage results | Must display whether the victim is in the Expectant, Immediate, or Delayed category | From START Method [1] |
| Display heartbeat data | Shall display victim’s heartbeat in beats per minute | From Conceptual Design, from Heartbeat and Respiratory Subsystem section |
| Display respiratory data | Shall display victim’s breath rate in breaths per minute | From Conceptual Design, from Heartbeat and Respiratory Subsystem section |

## Block Diagram
![UI_Schematic_1](https://user-images.githubusercontent.com/123419455/232373698-02f55d76-d05c-44ac-aec9-f2af683e1fef.jpg)

## Analysis
Pictured above is the block diagram for the UI for the program that will show the user the output data from the algorithm. The data will be shown to the user via a Python script that creates an intuitive table of the relevant data [2]. The main result will be the necessary data from the Computing Subsystem sent via the Wireless Communication Subsystem to output the following onto the screen: the sorting status of the victim, whether they are Expectant, Immediate, or Delayed as described in the START Method [1]. Secondarily, the two less prominent outputs for the UI would be the measured heartbeat in beats per minute (bpm) and the measured respiratory rate in breaths per minute (bpm) from the Heartbeat and Respiratory Sensing Subsystem or from the Computing Subsystem. Whichever origin for this data is more convenient for the Python program shall be used. The specific computer used will similarly be incidental, as the input from the Wireless Communication Subsystem is flexible as described in more detail in its respective signoff.

## BOM
| Name of item | Description | Part Number | Manufacturer | Quantity | Price | Total |
|--------------|-------------|-------------|--------------|----------|-------|-------|
| N/A | N/A | N/A | N/A | N/A | $0 | $0 |
|Total |  |  |  |  |  | $0 |

## Sources
[1] “Start adult triage algorithm,” CHEMM. [Online]. Available: https://chemm.hhs.gov/startadult.htm. [Accessed: 14-Feb-2023].

[2] “The python tutorial,” Python documentation, https://docs.python.org/3/tutorial/index.html (accessed Sep. 5, 2023). 
