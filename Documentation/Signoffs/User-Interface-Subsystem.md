# User Interface Subsytem

## Functionality

The function of this subsystem is to take the data from the wireless communication between the Jetson Nano and a laptop, then to display the data in a way that is useful for responders. Data that should be displayed should include the following: triage results, heartbeat, and respiratory rate data. Triage results should be prioritized as the main result being displayed with heartbeat data and respiratory data being displayed as secondary data.

## Specs and Constraints Table

| Description | Constraint | Source |
|-------------|------------|--------|
| Display triage results | Must display whether victim is in Expectant, Immediate, or Delayed category | From START Method [1] |
| Display heartbeat data | Should display victim’s heartbeat in beats per minute | From Conceptual Design, from Heartbeat/Respiratory System section |
| Display respiratory data | Should display victim’s breath rate in breaths per minute | From Conceptual Design, from Heartbeat/Respiratory System section |

## Buildable Schematic
![UI_Schematic_1](https://user-images.githubusercontent.com/123419455/232373698-02f55d76-d05c-44ac-aec9-f2af683e1fef.jpg)

## Analysis
Pictured above is the buildable schematic for the UI for the website or other program that will show the user the output data from the algorithm. The main input will be the necessary data from the Computing Subsystem sent via the Wireless Communication Subsystem to output the following onto the screen: the sorting status of the victim, whether they are Expectant, Immediate, or Delayed as described in the START Method [1]. Two less prominent outputs for the UI would be the measured heartbeat in beats per minute (bpm) and the measured respiratory rate in breaths per minute (bpm). Also shown in the buildable schematic is the wireless connection to the algorithm. Further detail on this wireless connection is featured on the Wireless Communication Subsystem signoff file. The website can be built with HTML.

## BOM
| Name of item | Description | Part Number | Manufacturer | Quantity | Price | Total |
|--------------|-------------|-------------|--------------|----------|-------|-------|
|Total |  |  |  |  |  | $0 |

## Sources
[1] “Start adult triage algorithm,” CHEMM. [Online]. Available: https://chemm.hhs.gov/startadult.htm. [Accessed: 14-Feb-2023].
