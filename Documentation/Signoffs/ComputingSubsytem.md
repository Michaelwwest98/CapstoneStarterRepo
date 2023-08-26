# Computing Subsystem 
## Subsystem Functionality
The computing subsystem, powered by the Jetson Nano, serves as the core subsystem that interconnects all other subsystems. This subsystem serves as the housing for the triage algorithm designed to operate by the guidelines set forth by the START model, which is a framework for assigning triage levels to injured individuals in a mass casualty situation. The Jetson Nano is a cutting-edge embedded system platform that has artificial intelligence and machine learning capabilities, this Jetson Nano-driven subsystem will conduct swift and precise assessments of injured victims based on data collected from the other subsystems, a task that in hopes will save countless lives in emergency scenarios. Eventually, to be integrated with a drone, this computing subsystem showcases advanced technology in artificial intelligence and machine learning which will be more than capable for any advanced tasks in the future.
## Constraints and specifications
| Description | Constraint | Source |
|-------------|------------|--------|
| Speed | Calculate results of triage algorithm and vitals in close to real-time | DARPA[1] |
| Compliance with laws | 	Must not store any audio recordings of victims in distress | Two party consent laws |
| Weight | When combined with other subsystems as well as reference drone, must weigh below 20 lbs in total | DARPA[1] |
## Jetson Nano flowchart
![flow diagram](https://github.com/Michaelwwest98/DARPA-Drone-Triage-Sensing-System/assets/60167425/25671318-2959-4bcb-9cc9-0d8db281cdc6)
## Analysis
+ The DARPA challenge specifications do not give a quantitative time for how fast the calculation of the triage level must take, the ideal speed is close to real-time. 
The Jetson Nano is a powerful embedded computing platform that operates at 640MHz, So the Jetson Nano will not be a bottleneck for calculating the triage results[1][2].
+ To be in compliance with all 50 states' two-party consent laws, the Jetson Nano will not use any memory storage methods to keep any recordings of injured victims.
+ The DARPA challenge specifications call for a total weight of less than 20 lbs, including the drone, so this subsystem will have to work with all other subsystems to
remain in specification with this constraint. The Jetson Nano weighs approximately 0.55lb, leaving plenty of room for the other subsystems

## BOM
| Product | Quantity | Price |
|-------------|------------|--------|
| Jetson Nano J1020 V4 | 1 | $259.00 |

## Sources

+ [1] DARPA Triage Challenge. Available: https://triagechallenge.darpa.mil/.
+ [2] “Jetson Download Center.” NVIDIA Developer, 13 Apr. 2023, https://developer.nvidia.com/embedded/downloads. 

