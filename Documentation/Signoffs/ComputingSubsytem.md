# Computing Subsystem 
## Subsystem Functionality
This subsystem is responsible for the housing and computing of the voice detection algorithm and the overall triage algorithm as well as wirelessly transmitting the results to the user interface. The voice detection algorithm will take in raw data from the microphone, process it, and take out the data found between a vocal frequency range and send the results to the triage algorithm. The triage algorithm will take in data sent from the Heartbeat/Respiratory Subsystem and the voice detection algorithm and compute whether a heartbeat is present, what the breathing rate is, and if the individual is responsive, these results will then be compared to the START triage method model to output the triage level necessary for the individual being tested. The result of this algorithm will then be wirelessly transmitted to the user interface. For this signoff, the Jetson Nano by NVIDIA is being considered to satisfy all the constraints and functionality of this subsystem.
## Constraints and specifications
| Description | Constraint | Source |
|-------------|------------|--------|
| Speed | Calculate results of triage algorithm and vitals in close to real time | DARPA[1] |
| Wireless communication | Communicate wirelessly with the user interface subsystem at a minimum of 30 meters | DARPA[1] |
| Sound | Must generate human voice frequencies between 20Hz to 20kHz | Derived constraint to ensure sound can be heard by human ears[2] |
| Voice detection | Must listen for audio frequencies between 80Hz to 255Hz | Derived constraint to ensure all human voice can be heard[3] |
| Power | Must be powered by a portable 5V power supply capable of supplying 2A current | DARPA[1], Jetson Nano datasheet[4] |
| Compliance with laws | 	Must not store any audio recordings of victims in distress | Two party consent laws |
| Weight | When combined with other subsystems as well as reference drone, must weigh below 20 lbs in total | DARPA[1] |
## Jetson Nano flowchart
![Jetson flow chart](https://user-images.githubusercontent.com/60167425/232330518-f4a37d9c-8a62-42da-84e8-18ca2963f8d6.png)
## Analysis
+ The DARPA challenge specifications does not give a quantative time for how fast the calculation of the triage level must take. 
The Jetson Nano is a powerful embedded computing platform that operates at 640MHz, So the Jetson Nano will not be a bottleneck for calculating the triage results[1][4].
+ The DARPA challenge requires a minimum wireless communication distance of 30m. The Jetson Nano has a wireless Wifi module connector on the board, this can be used
along with a LAN to communicate the results wirelessly. 30 meters should be achieved by using standard 2.4GHz wireless comunication.
+ To generate the sounds for the speaker system, the jetson will need to generate signals in the human voice spectrum which is within the operating frequency on the Jetson Nano. (Note: this may require external circuitry to achive this functionality)
+ To detect human vocals, the jetson will have to listen for signals in the human vocal region of frequencies. The jetson will have no issue with these frequencies since
they are small relative to the frequency the jetson operates at. (Note: this may require external circuitry to achive this functionality)
+ The datasheet provided with the Jetson Nano specifies for a supply of 5V with a maximum of 2A draw. There is multiple battery solutions at this range of power due to it being
a popular voltage level and current draw. Refer to the Power subsystem signoff for information regarding the specifics of the battery.
+ To be in compliance with all 50 states two party consent laws, the Jetson Nano will not store any recordings of injured victims.
+ The DARPA challenge specifications call for a total weight less than 20lbs in total including the drone, so this subsystem will have to work with all other subsystems to
remain in specification with this constraint.

## BOM
| Product | Quantity | Price |
|-------------|------------|--------|
| Jetson Nano V4 | 1 | $280.00 |

## Sources

+ [1] DARPA Triage Challenge. Available: https://triagechallenge.darpa.mil/.
+ [2] Mann, James, et al. “What Is a Good DB &amp; SPL for Speakers? – Becomesingers.com.” BecomeSingers.Com, https://www.becomesingers.com/studio-setups/db-spl-for-speakers#:~:text=The%20higher%20the%20rating%20of%20sensitivity%2C%20the%20louder,or%20more%20sensitivity%20rating%20can%20be%20considered%20excellent. 
+ [3] The Audible Spectrum - Neuroscience - NCBI Bookshelf. https://www.ncbi.nlm.nih.gov/books/NBK10924/. 
+ [4] “Jetson Download Center.” NVIDIA Developer, 13 Apr. 2023, https://developer.nvidia.com/embedded/downloads. 

