# User Interface Subsystem

## Functionality

The function of this subsystem is primarily to display the triage result in an intuitive manner that is useful for responders. Intuitiveness in this regard means that the user interface of the system is to be specifically designed to make it easier for responders to use the system and keep track of relevant data. Secondarily, this subsystem will also serve the purpose of calculating average heartbeat and breath rate data out of the sample obtained and displaying that data to responders as well.

## Specs and Constraints Table

| Description | Constraint | Source |
|-------------|------------|--------|
| Display triage results | Must display whether the victim is in the Expectant, Immediate, or Delayed category | From START Method [1] |
| Display heartbeat data | Shall display victim’s heartbeat in beats per minute | From Conceptual Design, from Heartbeat and Respiratory Subsystem section |
| Display respiratory data | Shall display victim’s breath rate in breaths per minute | From Conceptual Design, from Heartbeat and Respiratory Subsystem section |
| Weight | 	The entire system must weigh less than 6 pounds, this subsystem should weigh 1.5 lbs or less | From DARPA constraints, from Conceptual design |
| Speed | The system must provide triage results in less than 1 minute | From DARPA constraints |

## Block Diagram
![UI_Block_Diagram_1](https://github.com/Michaelwwest98/DARPA-Drone-Triage-Sensing-System/blob/Michaelwwest98-ui-subsystem-signoff/Documentation/Images/UI_Block_Diagram_1.JPG)

## Analysis
Pictured above is the block diagram for the UI for the program that will show the user the output data from the algorithm. The final data will be shown to the user via a Python script [2] that creates an intuitive table of the relevant data listed in the Specs and Constraints section. Data that will be displayed includes the following: triage results, heartbeat, and respiratory rate data. Triage results should be prioritized as the main result being displayed with heartbeat data and respiratory data being displayed as secondary data to help responders understand why the triage algorithm assigned that specific triage result to the victim and so that responders may act with more certainty quickly and effectively to help the victim that needs the quickest response first.

### Triage Result Display
The main result will be the necessary data from the Computing Subsystem sent via the Wireless Communication Subsystem to output the victim's triage result onto the screen: the sorting status of the victim, whether they are Expectant, Immediate, or Delayed as described in the START Method [1]. This data will be taken through the Wireless Communication Subsystem from the Computing Subsystem in the Jetson Nano, as described in the Computing Subsystem and Wireless Communication Subsystem signoffs respectively. This data will be shown so that responders will know which victim needs help the quickest, according to the triage algorithm in the Jetson Nano. 

### Average Heartbeat and Respiratory Rate Display
Secondarily, the two less prominent outputs for the UI would be the average measured heartbeat in beats per minute (bpm) and the average measured respiratory rate in breaths per minute (bpm) taken from the Computing Subsystem. This data will be taken from the Jetson Nano instead of being taken directly from the radar, as the Jetson Nano will be the device directly connected to the computer running the UI Subsystem Python program. The Python program will take a sample of heartbeat and respiratory rate data, do the necessary calculations to average them out, and then display them to the user. This data will be important so that responders can get a quick look at the data that leads to the triage result also shown on-screen such that they can help the victim that needs the quickest attention with more certainty. 

### Location of Python Program
The specific computer used for the UI Subsystem Python program will be incidental, as the input from the Wireless Communication Subsystem is connected via USB as described in more detail in the Wireless Communication Subsystem signoff. The triage result as well as the secondary data will all be static data when shown to the user. The triage result will be shown as a static result because it is a final result. An average respiratory rate and heartbeat will show the user whether each respective rate is normal, too high, or too low. This will allow the user to gain a decent understanding of why the victim is given their specific triage result.

### Weight Addition to System
Since no part of this subsystem will be a physical component connected to the drone, this subsystem will add 0 lbs to the drone's overall load.

### Speed of the System
According to the programmers behind Python, the current version is approximately 64% faster than the previous version of Python, which would run code in about 48.03 seconds [3]. Applying that approximate percentage to the runtime of the previous version to find the runtime of the current version of Python, means that using the current version of Python, version 3.11, any code written for it should run in approximately 17.29 seconds. Future versions of Python are also currently being developed to run faster than that.

## BOM
| Name of item | Description | Part Number | Manufacturer | Quantity | Price | Total |
|--------------|-------------|-------------|--------------|----------|-------|-------|
| N/A | N/A | N/A | N/A | N/A | $0 | $0 |
|Total |  |  |  |  |  | $0 |

## Sources
[1] “Start adult triage algorithm,” CHEMM. [Online]. Available: https://chemm.hhs.gov/startadult.htm. [Accessed: 14-Feb-2023].

[2] “The python tutorial,” Python documentation, https://docs.python.org/3/tutorial/index.html (accessed Sep. 5, 2023). 

[3] A. Fleiss, “How fast does python execute code?,” Rebellion Research, https://www.rebellionresearch.com/how-fast-does-python-execute-code#:~:text=Specifically%20we%20can%20look%20at,or%201.54%20seconds%20in%20C. (accessed Sep. 11, 2023). 
