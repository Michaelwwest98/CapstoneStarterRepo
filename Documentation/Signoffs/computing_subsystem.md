# Computing Subsystem 
## Subsystem Functionality
The computing subsystem, powered by the Jetson Nano, is the core subsystem that interconnects all other subsystems. This subsystem serves as the housing for the triage algorithm designed to operate by the guidelines set forth by the START model, 
which is a framework for assigning triage levels to injured individuals in a mass casualty situation. The Jetson Nano is a cutting-edge embedded system platform that has artificial intelligence and machine learning capabilities, 
this Jetson Nano-driven subsystem will conduct swift and precise assessments of injured victims based on data collected from the other subsystems, a task that in hopes will save countless lives in emergency scenarios. 
Eventually, to be integrated with a drone, this computing subsystem showcases advanced technology in artificial intelligence and machine learning which will be more than capable for any advanced tasks in the future.
## Constraints and specifications
| Description | Constraint | Source |
|-------------|------------|--------|
| Speed | Calculate results of triage algorithm and display wirelessly in under 2 seconds | Derived, DARPA[1] |
| Compliance with laws | 	Must not store any audio recordings of victims in distress | Two party consent laws |
| Weight | must weigh below 2.8 lbs | DARPA[1] |
## Jetson Nano Wiring Diagram
![wiring 2 0](https://github.com/Michaelwwest98/DARPA-Drone-Triage-Sensing-System/assets/60167425/a338061a-f107-4e52-926d-a2150ad1e136)
## Triage Program Flowchart
![flow diagram](https://github.com/Michaelwwest98/DARPA-Drone-Triage-Sensing-System/assets/60167425/25671318-2959-4bcb-9cc9-0d8db281cdc6)
## Analysis
+ The DARPA challenge specifications do not explicitly define a quantitative timeframe for the required speed of the triage level calculation. However, the goal is to achieve a processing speed that closely resembles real-time performance.
  Within this context, our team has derived a strict 2-second time constraint as our target. To determine whether the Jetson Nano can meet this constraint, we will use the Big O time complexity analysis.
  This type of analysis focuses on observing how the program's runtime behavior changes in response to linear growth, remaining constant, or quadratic growth of the input vector.
  It's noteworthy that, we will be using a fast Fourier transform to extract the heartrate  and respiratory frequencies. The Fourier transform integral is over a time period T, which in this case, will require the storage of a signal over a time period.
  Knowing this, the program's execution time has to be a function of how long the desired time period of the fast Fourier transform is. The concept of Big O notation represents this quality, typically representing 'n' as the variable with the fastest growth         concerning time. In this application, the execution time will grow linearly, therefore, big O notation yields O(n). This implies that not only does the program's execution time hinge on the program's length and complexity but also on the time period used for 
  the Fourier transform.
  The conceptualized program architecture can be summarized in three primary steps: firstly, performing a Fourier analysis on the signals received from the radar subsystem; secondly, running the vital signs through the triage algorithm flow chart,
  as illustrated above; and finally, transmitting the triage level, heart rate, and breathing rate through the wireless transmission subsystem.
  Given this program structure and the utilization of Python for its implementation, estimating the precise execution time presents challenges.
  Python's nature, being a high-level scripting language, creates a significant gap between the programmer and the Python compiler, making precise predictions difficult without actual hardware simulations.
  Nevertheless, for estimation purposes, the UMN performance equation suggests that a simple instruction takes around 4 cycles to complete[3], a conservative approximation of 10 cycles per instruction is considered.
  Considering the Jetson Nano's 640MHz clock speed[2], it can theoretically execute 64 million instructions per second. The project's demands should comfortably stay well below this threshold,
  ensuring quick computations of the triage algorithm.
+ In strict accordance with the two-party consent laws in all 50 states, the Jetson Nano will abstain from any memory storage mechanisms to retain recordings of injured victims.
+ In accordance with the weight constraints outlined in the DARPA challenge specification sheet[1], a collective weight not exceeding 20 lbs is required, including both the drone and its components. Furthermore, a 6lb reference drone will be used in this project, making the target weight for all 5 subsystems 14 lbs. Given this, the allocated weight will be distributed evenly amongst the 5 subsystems giving each subsystem a max weight of 2.8lbs. The datasheet for the Jetson Nano approximates the full developer kit to weigh 0.55lbs[2], this meets the derived constraint while also allowing other subsystems more room.

## BOM
| Product | Quantity | Price |
|-------------|------------|--------|
| Jetson Nano J1020 V4 | 1 | $259.00 |

## Sources

+ [1] DARPA Triage Challenge. Available: https://triagechallenge.darpa.mil/.
+ [2] “Jetson Download Center.” NVIDIA Developer, 13 Apr. 2023, https://developer.nvidia.com/embedded/downloads.
+ [3] "Performance Equation", https://www.d.umn.edu/~gshute/arch/performance-equation.xhtml
