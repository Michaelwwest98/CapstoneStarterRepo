# Voice Activity Detection Subsystem #

## Subsystem Function:

The purpose of this subsystem is to detect an individual's responsiveness or cognition through the use of call and response techniques. The subsystem will activate once an individual heartbeat has been detected. The speaker will play a sound with an instruction to say something. Once the instruction is given, the microphone will begin transmitting audio to a computing system which will then run an algorithm to detect if a human voice responded or not allowing the total system to know if the individual being tested has cognition or not.

## Specs and Constraints:			


<table>
  <tr>
   <td>Description
   </td>
   <td>Constraint
   </td>
   <td>Source of Constraint
   </td>
  </tr>
  <tr>
   <td>Microphone
   </td>
   <td>Must sense frequencies from 80 Hz to 300 Hz
   </td>
   <td>Frequency range of average man is 80-180 Hz while female is 165 - 300 Hz.[1]
   </td>
  </tr>
  <tr>
   <td>Microphone
   </td>
   <td>Must sense a minimum decibel gain value between 30 dB.
   </td>
   <td>Volume level of a human whisper. Helps to detect those who can barely speak.[2]
   </td>
  </tr>
  <tr>
   <td>Speaker
   </td>
   <td>Must play sound clips between 20 Hz- 20000 Hz 
   </td>
   <td>Frequency range an individual’s ear can hear [1]
   </td>
  </tr>
  <tr>
   <td>Weight
   </td>
   <td>The drone specified in conceptual design had a max load of 2.7 kg. Seeing as 4 subsystems will be attached to the drone. The max weight must not exceed 675g.
   </td>
   <td>From DARPA constraints/ Conceptual design
   </td>
  </tr>
  <tr>
   <td>Safety
   </td>
   <td>Speaker output must not be louder than 120 dB
   </td>
   <td>Levels at 120 dB can cause immediate harm to an individual's hearing [2]
   </td>
  </tr>
</table>


## Wiring Schematics



![image](https://user-images.githubusercontent.com/79685126/235611053-69878c8b-1b4f-4cb6-9a22-76f6e17996e6.png)


Figure1. Wire Diagram for the total subsystem

## Analysis:

The datasheet of the BOB-19389 states a frequency range at 7 Hz - 36 kHz which includes the threshold set by the constraints to capture human voice frequencies. This microphone will be able to capture the 80-300 Hz range set by the constraint.

The BOB-19389 datasheet also has a minimum sensitivity of -44 dB which is much more sensitive than the 30 dB needed to capture a human whisper. This meets the constraint set above and will allow the system to capture an individuals cognition even if a faint sound is heard from the human.

The COM-18343 speakers are full range and capture all the hard frequencies from 20 Hz - 20kHz set by the constraint above. But more importantly it will be able to produce sound between 2000 Hz through 5000 Hz which is the range most sensitive to the human ear. 

The total subsystem will consist of two parts. The microphone and speaker. The speakers weight is not specified, but simaliar speakers weig around 200 g, and the microphone, whose weight is also not specficed, has around a weight of 25 g. This brings the total subsystem weight to 225 g which is under the 675 g constraint limit set above. This will allow for some extra weight to be included for other subsystems.

  

## BOM


| Name of item | Description | Part Number | Manufacturer | Quantity | Price | Total |
|--------------|-------------|-------------|--------------|----------|-------|-------|
| Microphone | 	OPA344, SPH8878LR5H-1 MEMS Omnidirectional Microphones Audio Evaluation Board | B0B-19389 | SparkFun Electronics | 1 | $6.95 | $6.95 |
| Speaker | 4 Ohms General Purpose Speaker 4 W Top Rectangular | COM-18343 | SparkFun | 1 | $10.95 | $10.95 |
  
## Sources

[1] Berlinshoegazer, “EQing vocals: What's happening in each frequency range in the human voice,” Flypaper, 09-Jan-2023. [Online]. Available: https://flypaper.soundfly.com/produce/eqing-vocals-whats-happening-in-each-frequency-range-in-the-human-voice/#:~:text=The%20human%20ear%20can%20hear,from%20165%20to%20255%20Hz. [Accessed: 02-May-2023]. 
[2] “What noises cause hearing loss?,” Centers for Disease Control and Prevention, 08-Nov-2022. [Online]. Available: https://www.cdc.gov/nceh/hearing_loss/what_noises_cause_hearing_loss.html#:~:text=A%20whisper%20is%20about%2030,running%20is%20about%2095%20dB. [Accessed: 02-May-2023]. 



