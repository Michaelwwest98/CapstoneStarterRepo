# Experimental Analysis Report

## Introduction
The following report details the expriments, results, and interpretation of results. It is important to note all constraints ar ementioned, 
but not all where impleemnts or ended up being proven. Due to time limitations some experiemnts also weren't physically recorded, but an analysis
of the results is till done through other methods. All constraints are separated by the subsystem and then further expanded upon throughout the report.
## Specifications and Constraints

### Constraints Table

| ID | Specification/Constraint | Rescope |
| -- | ------------------------ | --------------------- |
| -- | **RESPIRATORY/HEARTBEAT** |--|
| 1 | Must sense Beats per minute from 30 to 210 bpm (or frequencies from 0.5 Hz to 3.5 Hz) | N/A |
| 2 | Must sense breaths per minute from 1 to 70 bpm (or frequencies from 0.017 Hz to 1.17 Hz) | N/A |
|3 | Must detect and measure heartbeat and breath rate from at least 1 meter away | N/A |
| 4 | Entire system must weigh less than 6 pounds, this subsystem should weight 1.5 lbs or less | N/A |
| 5 | Radar must not emit at a frequency over 10 GHz with a power density of 1000 W/m^2 in order to keep the radar skin and eye safe. | N/A |
| 6 | Operational Amplifier must be able to handle a max 0.8 V peak-to-peak amplitude and a maximum 19.4 KHz frequency. | Ampflier not used for this iteration of system, hopefully it can be implemented in future |
| 7 | Circuit must be able to filter out high frequencies with a corner frequency of around 19kHz while at least also amplifying the signals between 0.017Hz - 3.5Hz by a gain of 6. The corner frequency comes from satisfying nyquist value for a sample frequency of 38.4kHz as specified by the ADC datasheet. | Ampflier not used for this iteration of system, hopefully it can be implemented in future |
| 8 | The gain of 6 comes from a 0.8 Vp-p input voltage of the radar as specified by the datasheet which needs to reach no more then 5 Vp-p output voltage as specified by the ADC datasheet. The frequency minimum of 0.017 Hz comes from the total bandwidth needed by heartbeat and respiratory rate frequencies. | Ampflier not used for this iteration of system, hopefully it can be implemented in future |
| -- | **POWER** | -- |
| 1 | The system must operate at full functionality for 15 to 60 minutes | N/A |
| 2 | The power source for our system must be portable, and replaceable or rechargeable | N/A |
| 3 | The power system can weigh a max of 1.5 lbs | N/A |
| 4 | The Jetson Nano must maintain a supply voltage greater than or equal to 4.75 V via a 2.1 mm DC barrel jack. The input voltage ripple should be below 220 mV peak to peak. The Jetson Nano has a maximum voltage rating of 5.5 V and a maximum current rating of 5 A. The power rating for the Jetson nano is 27.5 W. The Nano consumes approximately 1.25 W at 4 A with no peripherals |  The Raspberry Pi 4 B requires a nominal input voltage of 5 V via USB type C connector. The input voltage ripple should be below 220 mV peak to peak. The Raspberry Pi 4 Model B has a maximum voltage rating of 6 V and a maximum current rating of 3 A. The Raspberry Pi 4 Model B consumes approximately 2.7 W at 240 mA with no peripherals. |
| 5 | The system must effectively supply 1.1250 A at 5 V for a total power of 5.625 W to the Jetson and its peripherals via the 12 V out of the battery adapter plate, and it must supply max 60 mW from 7.4 V out of the adapter plate for a total of 5.685 W | Changed to Raspberry Pi for computing system |
|6 | The op amp circuit requires +/- 5 V. The maximum input voltage is +/- 15 V, and the maximum power consumption is going to be from 8 to 60 mW | Ampflier not used for this iteration of system, hopefully it can be implemented in future |
| -- | **WIRELESS COMMUNCATION** | -- |
| 1 | The maximum distance the sensing system can be away from the command center is 9 kilometers | N/A |
| 2 | The system shall send results from the computing subsystem to user interface subsystem at a maximum time of two seconds | N/A |
| 3 | The entire subsystem shall weigh less than 1.2 pounds | N/A |
| 4 | Unlicensed devices that operate in the 902 - 928 MHz band allow for a maximum power output of up to 30 dBm or 1 Watt | N/A |
| 5 | The device must operate in the United States Unlicensed frequency band that is from 902 - 928 MHz | N/A |
| 6 | The system must be able to transmit a data packet at the size of at least 30 bits of data | N/A |
| 7 | The system must be compatible with Linux based computing systems | N/A |
| -- | **USER INTERFACE** | -- |
| 1 | Must display whether the victim is in the Expectant, Immediate, or Delayed category with appropriate associated color | N/A |
| 2 | The system must provide triage results in less than 1 minute | N/A |
| 3 | Shall display victim’s heartbeat in beats per minute | N/A |
| 4 | Must display heartbeat data at least once per second | N/A |
| 5 | Shall display victim’s breath rate in breaths per minute | N/A |
| 6 | Must display respiratory data at least once per second | N/A |
| -- | **VOICE ACTIVITY DETECTION** | -- |
| 1 | Must detect the presence of a human voice from audio signal
| 2 | Must pick up a minimum sound pressure level of 30 dB SPL from at least 1 meter away | N/A |
| 3 | Must sense frequencies from 100 Hz to 3000 Hz | N/A |
| 4 | Must output sound at a volume heard from at least 1 meter away | N/A |
| 5 | Must play sound clips between 20 Hz- 20000 Hz | N/A |
| 6 | Must function with noise from drone from at least 1 meter away | N/A |
| 7 | The entire subsystem shall weigh less than 1.2 pounds | N/A |
| 8 | Speaker output must not be louder than 120 dB | N/A |
| -- | **COMPUTING** | N/A |
| 1 | Must calculate results of triage algorithm and display wirelessly in under 2 seconds | already mentioned in wireless subsystem |
| 2 | Must not store any audio recordings of victims in distress | N/A |
| 3 | Must weigh below 1.2 lbs | N/A |

## Experimental Results

### RESPIRATORY/HEARTBEAT
#### Constraint 1 - Must sense Beats per minute from 30 to 210 bpm
- Experimental Design  
To test if system is capable of sensning the bpm necessary for heartbeat detetion, a live person can be placed under radar while system is running
, once FFT is recieved looking if there is any data between 0.5 Hz and 3.5 Hz that is not present when system is tested without a person shows the system is caable of detecting such frequnecies. 
- Results  
![image](https://github.com/Michaelwwest98/DARPA-Drone-Triage-Sensing-System/assets/79685126/51a7825d-9967-4bb8-bc15-e55e333279c3)
- Interpretation of Results  
  The results showed everytime an indidual was placed under, if system was operating properly with no errors, there would be a change between the
  frequcnies listed above. This doesn't necessarily mean that the correct values are present, but it for sure proves that the system is indeed capable of retieving frequenices that low.
  A 30 second window is also used sampling at over 100 Hz so emeprically the system should also be capale of looking at sch low frequenices. But looking at the plots
  shows that practically this is the case too.

#### Constraint 2 -  Must sense breaths per minute from 1 to 70 bpm
- Experimental Design  
  Refer to constraint 1
- Results  
  Refer to constraint 1
- Interpretation of Results  
  There is an overlap in freuqnices for breath rate and heart rate, meaning if system is capable of measring up to 3.5 Hz as mentioned above,
  it is also capable of measuring 0.017 to 1.17 Hz
#### Constraint 3 - Must detect and measure heartbeat and breath rate from at least 1 meter away
- Experimental Design  
  Building a test stand a meter away and comparing result given by system with physically counting amount breaths and the amount of beats in 30 seconds and calculating
  both bpms that way.
- Results  
![image](https://github.com/Michaelwwest98/DARPA-Drone-Triage-Sensing-System/assets/79685126/b187a445-4f80-49a0-adde-cfbeacdd2a8a)
- Interpretation of Results  
  The reults show how accurate the system is in 10 trials. The percent errors are given bottom right. It is important to note that all measurments are taken at ideal conditions.
  This means that when the idnivudal has a normal resting bpm the system is pretty accurate. More teting needs to be done in harsher condiitons to see accruacy in more real world conditions.
  This will allow furhter testing of peak detection algorithm accruacy. 
#### Constraint 4 - Entire system must weigh less than 6 pounds, this subsystem should weight 1.5 lbs or less
- Experimental Design  
  Weighing the items to get actual weight of entire subsstem
- Results  
  System was not physically weighed
- Interpretation of Results  
  ALthough the hysical weight of system was not found just by size of the radar it is clear that it probably weighs less than 1.5 lbs. But system should stilll be weighed.
#### Constraint 5 - Radar must not emit at a frequency over 10 GHz with a power density of 1000 W/m^2 in order to keep the radar skin and eye safe
- Experimental Design  
  Calculate the power density of beam by creating a phycial araea where the system functions and dividning it by the power emmited by system.
- Results  
  Did not execute this test
- Interpretation of Results  
  Due to lack of time this test was not executed, but the output power of system is in miliwatts so dividing it by any area will
  give you something less than 100 W/m^2. Still the test should be executed to confirm this result

  
### POWER

#### Constraint 1 - The system must operate at full functionality for 15 to 60 minutes
- Experimental Design  
  Test system while running and only power by battery and check if it is able to stay turned on for more than 15-60 minutes.
- Results  
  The battery was able to power the Raspberry Pi for 2 hours without any negative effects to the system, during the demo session at capstone presentation.
- Interpretation of Results  
  The system is most definitely not operating at worst case, but is 100% able to operate for the mandated time period. Fulling uunning the system powered only by battery resulted in it perating within window.
  Furhter testing can be done on different condiitons of operation.
    
#### Constraint 2 - The power source for our system must be portable, and replaceable or rechargeable
- Experimental Design  
  For the power system to be portable and replaceable or recharagable, a rechargable battery pack with an adapter plate designed for small hand-held cameras was chosen.
- Results  
  The battery and battery adapter plate mounts easily to our test stand and the battery charges easily with a supplied wall charger.
- Interpretation of Results  
  The power system is portable and rechargable.
    
#### Constraint 3 - The power system can weigh a max of 1.5 lbs
- Experimental Design  
  Weigh the physical Battery system. 
- Results  
  The power system came out to weigh just under 0.5 lbs.
- Interpretation of Results  
  The weight requirement was met for the power subsystem.
#### Constraint 4 - Refer to Table
- Experimental Design  
  To supply the appropriate voltage and current levels as well as input voltage ripple for the Raspberry Pi and the peripherals, a buck converter/voltage regulator was used along with the battery. The system can be tested by simply meauring the ripple voltage 
- Results  
  No load voltage ripple on the output of the buck converter/regulator was measure to be 30 mV peak to peak. The voltage seen by the Raspberry Pi is 5 V, and the regulator can supply up to 20 W.
- Interpretation of Results  
  The power system is able to effectively power the computing system and all peripherals.
  

### WIRELESS COMMUNICATION
#### Constraint 1 - The maximum distance the sensing system can be away from the command center is 9 kilometers
- Experimental Design  
  Transmit data at different intervals and through different environements up to the 9 kilometer limit
- Results  
  Did not complete this expermeient emperically
- Interpretation of Results  
  Although the experiemnt was not completed, through testing, the command center system was moved furhter away from radar system all thoughout capstone lab
  and functioned perfectly fine. System was also able to function when testing outside of the lab, but emeprical data must be taken to see if and at what conditions
   the system can operate at the 9 km distance. 
#### Constraint 2 - The system shall send results from the computing subsystem to user interface subsystem at a maximum time of two seconds
- Experimental Design  
  Take the time intervals it takes data to ne transimtted and recieved beteen the two systems at different distances from control unit.
- Results  
  Did not complete experiemnt
- Interpretation of Results  
  This constraint needs to be tested as through testing it wasn't even noted the time it took to transmit. System needs to be timed and recorded to
  see accuracy of system.
#### Constraint 3 - The entire subsystem shall weigh less than 1.2 pounds
- Experimental Design  
  Weigh the total wirelss subsystem
- Results  
  Was not physically weighed
- Interpretation of Results  
  Although system not physically weighed, the size of system and holding it when using allowed for a prety good conclusion that it weighed less than
  1.2 pounds. But system for completeess system should still be weighed.
#### Constraint 4 - Unlicensed devices that operate in the 902 - 928 MHz band allow for a maximum power output of up to 30 dBm or 1 Watt
- Experimental Design  
  Measure the power of the system 
- Results  
  No emperical power measurement taken
- Interpretation of Results  
  Unfortunately, the equipment in the lab could not measure the output power of the transmitter accurately, so the team had to rely on inputted settings and the datasheet to meet this constraint. According to the datasheet, the max power output of this transceiver is 20 dBm which falls below the maximum 30 dBm for transceivers that operate in the 902 - 928 MHz frequency band set in the constraints. While setting up the transceiver using python codes with AT commands, the power output was set to 5 dBm or 0.003162277 W which also falls below the 30 dBm or 1 W maximum output power for transceiver that operate in the 902 - 928 MHz frequency band in the constraints.
#### Constraint 5 - The device must operate in the United States Unlicensed frequency band that is from 902 - 928 MHz
- Experimental Design  
  Set device to run at sepcified frequency band.
- Results  
  N/A
- Interpretation of Results  
  The device was set to operate in the 915 MHz frequency band using AT commands found within the code within the computing subsystem. This satisfies the
  constraint of operating within the 902 - 928 MHz frequency band.
#### Constraint 6 - The system must be able to transmit a data packet at the size of at least 30 bits of data
- Experimental Design  
  Calculate the amount of bits sent by the transmitter in the data packet
- Results  
  72 bits per data packet
- Interpretation of Results  
  Systems sends a total of 9 numbers, with each number taken up 8 bits of data, that puts each data packet at ariund 72 bits. his emans System is above the 30
  bits of data per packet limit 
#### Constraint 7 - The system must be compatible with Linux based computing systems
- Experimental Design  
  Run wirless system on linux device
- Results  
  ![image](https://github.com/Michaelwwest98/DARPA-Drone-Triage-Sensing-System/assets/79685126/8e7cd4dc-f949-4b17-b3d6-544c428ca46f)
- Interpretation of Results  
  Using cutecom, a serial port tool for Linux, the system is able to interact with Linux based systems successfully transmitting data, fulfilling this constraint.

  
### USER INTERFACE
#### Constraint 1 - Must display whether the victim is in the Expectant, Immediate, or Delayed category with appropriate associated color
- Experimental Design  
  Test system multiple times and take note of reults if all three traige staes appear and if color matches properly.
- Results  
![image](https://github.com/Michaelwwest98/DARPA-Drone-Triage-Sensing-System/assets/79685126/13188982-e9a5-43c0-ba72-4eee3071fadf)
![image](https://github.com/Michaelwwest98/DARPA-Drone-Triage-Sensing-System/assets/79685126/aa585897-610c-449e-bc5d-e217b951a395)
  Third Delayed not pictured, but fucntional 
- Interpretation of Results  
  All three appear on the UI interface, but color is not present and needs to be added. 
#### Constraint 2 - The system must provide triage results in less than 1 minute
- Experimental Design  
  Record time it takes from starting system till reult is displayed over a course of multiple trials, to see if less than 1 minute.
- Results  
  Did not keep record of how long system ran for 
- Interpretation of Results  
  Although physcial time not kept, since the system takes 31 seconds to collect the heartbeat, respiratory, and voicy activity data, the user interface
  system is able to successfully display the triage results in less than one minute.
 
#### Constraint 3 - Shall display victim’s heartbeat in beats per minute
- Experimental Design  
  Check diplay if beats per minute is displayed
- Results  
  Refer to reults of constarint 1
- Interpretation of Results  
  The user interface system is able to successfully display an individual’s heart rate in bpm.

#### Constraint 4 - Must display heartbeat data at least once per second
- Experimental Design  
  Keep track and record how often there is a change in value on display and compare to 1 second
- Results  
  Not possible 
- Interpretation of Results  
  As previously stated, the system takes 31 seconds to collect the heartbeat, respiratory, and voice activity data, so the user interface system is
  unable to display an individual’s heart rate data at least once per second.

#### Constraint 5 - Shall display victim’s breath rate in breaths per minute
- Experimental Design  
  Check diplay if breaths per minute is displayed
- Results  
  Refer to reults of constarint 1
- Interpretation of Results  
  he user interface system is able to successfully display an individual’s breathing rate in bpm.
  
#### Constraint 6 -  Must display respiratory data at least once per second 
- Experimental Design  
  Keep track and record how often there is a change in value on display and compare to 1 second
- Results  
  Not possible
- Interpretation of Results  
  As previously stated, the system takes 31 seconds to collect the heartbeat, respiratory, and voice activity data, so the user interface system is
  unable to display an individual’s heart rate data at least once per second.

  
### VOICE ACTIVITY DETECTION

#### Constraint 1 - Must detect the presence of a human voice from audio signal
- Experimental Design  
  Run trials of audio signals with and without human voice recording the accuaracy of human voice detection.
- Results  
  Did not physically record results
- Interpretation of Results  
  Although reults were not physucally recorded, during test runs. an audio of random animal sounds were put next to microphone and system did not detect human voice.
  This of course needs to be tested more with physical trials to get better reults on the accruacy of system. 
#### Constraint 2 - Must pick up a minimum sound pressure level of 30 dB SPL from at least 1 meter away
- Experimental Design  
  Run trials of whispering sounds under radar stand and comput how many times system detcets an indivual person's whisper.
- Results  
  Did not complete experiemnt
- Interpretation of Results  
  This test was not completing due to lack of time, but while testing a similar test was conducted with not promising results. This system needs to furhter be
  tested to see if algorithm or microphone is the issue to lack of voice sensitivity observed.
#### Constraint 3 - Must sense frequencies from 100 Hz to 3000 Hz
- Experimental Design  
  Use either a FFT or Power density fucntion to see if values between this randge are able to be detected
- Results  
  ![image](https://github.com/Michaelwwest98/DARPA-Drone-Triage-Sensing-System/assets/79685126/8e8979f6-b017-4604-8668-cb2f013a9381)
- Interpretation of Results  
  As seen in the reults this specific constraint was not met, but the issue is more with the cnstarint than the reults. The constraint frequencies are too large for human voice.
  The system is stil clearly able to detect some og the freuqnecies in the range set by constraint. 
#### Constraint 4 - Must output sound at a volume heard from at least 1 meter away
- Experimental Design  
  Play sound and check if heard from a meter away in different conditions.
- Results  
  No physical reult taken
- Interpretation of Results  
  Although no physical result was recorded. Speaker was operational and could be heard by all team emembers in an ideal environment without any other outside effects.
  More testing needs to be done on if speaker can operate and be heard in other conditions.
#### Constraint 5 - Must play sound clips between 20 Hz- 20000 Hz
- Experimental Design  
  Play sound for 20 to 20000 Hz on the speaker
- Results  
  No physical result
- Interpretation of Results  
  Speaker ended up not being operational so this test was not run, but speaker was connected to bluetooth and it played youtube videos just fine.
#### Constraint 6 - Must function with noise from drone from at least 1 meter away
- Experimental Design  
  Test system with drone noise and record relsults of voice detection accruacy and audio heard accuracy from at least 1 meter away
- Results  
  Test not fully completed
- Interpretation of Results  
  Test was completed with drone noise coming from phone, but futher testing needs to be done with actual drone noise to test accruacy.
  The system did pass the simple observational test of drone noise coming from drone, but results could vary in different environments.
#### Constraint 7 - The entire subsystem shall weigh less than 1.2 pounds
- Experimental Design  
  Weigh total system
- Results  
  Weight not taken
- Interpretation of Results  
  Although weight not taken, microphone is the size of a penny, so system won't come close to the limit set by this constraint. 
#### Constraint 8 - Speaker output must not be louder than 120 dB
- Experimental Design  
  Check how loud speaker output is
- Results  
  N/A
- Interpretation of Results  
  Speaker system did not work so loudness of the speaker could not be tested on the system. But volume s contorlled so it can be many different vlaues.  
### COMPUTING
  
#### Constraint 2 - Must not store any audio recordings of victims in distress
- Experimental Design  
  N/A
- Results  
  N/A
- Interpretation of Results  
  No storage of audio signal encoded in the system
#### Constraint 3 - Must weigh below 1.2 lbs
- Experimental Design  
  Weigh physical computing subsystem
- Results  
  No phycical measurment
- Interpretation of Results  
  Once again no measuremnt was taken, but the switch to the raspberry pi also meant a lowering of the overall subsystem weight. 

