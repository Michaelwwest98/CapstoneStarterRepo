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
   <td>Must sense frequencies from 100 Hz to 3000 Hz
   </td>
   <td>Frequency range of average man is 100-900 Hz while female is 300 - 3000 Hz.[1]
   </td>
  </tr>
  <tr>
   <td>Microphone
   </td>
   <td>Must sense a minimum decibel gain value of 30 dB.
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
     <tr>
   <td>Microphone/Speaker
   </td>
   <td> The B0B-19389 and COM-18343 must function at a minimum distance of 1 meter.
   </td>
   <td>Constraint set by the overall system to be contactless
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

The algorithm will function by sending out a verbal message from the speaker and listening for a response from a human voice. The presence of a human voice adds energy to a signal at specific frequences. To find if a human voice is present the task of the system is to look at the energy levels of the signal and find where the voice is present. This begins by taking a window of raw data from the microphone of around 30 ms. The data should look similar to the figure below.

![image](https://github.com/Michaelwwest98/DARPA-Drone-Triage-Sensing-System/assets/79685126/a53e92db-5e71-46a3-8f1a-8de806992744)

Figure taken from [3]

Once converted through the ADC the signal can be sent through a digital passband filter to take out frequencies outside the the band set by the constraints. The signal energy of the signal can be calculated by taking the magnitude squared of the signal and converting to dB values. The result should look smething like the grap below. 

![image](https://github.com/Michaelwwest98/DARPA-Drone-Triage-Sensing-System/assets/79685126/432ab20f-44d4-48f9-b450-449ad1bc6362)

Figure taken from [3]

With energy of the signal found a threshhold for min level of energy can be used to detect where speech is present. In the case of [3] 17 dB is used. This creates a graph that looks like the one below.

![image](https://github.com/Michaelwwest98/DARPA-Drone-Triage-Sensing-System/assets/79685126/dbd87f31-08b4-4b58-b0f0-6515aa8fff09)

Figure taken from [3]

If value is a 1 speech has been detected and value can be sent for further analysis at other subsystems.


The datasheet of the BOB-19389 states a frequency range at 7 Hz - 36 kHz which includes the threshold set by the constraints to capture human voice frequencies. This microphone will be able to capture the 100-3000 Hz range set by the constraint.

The BOB-19389 datasheet also has a minimum sensitivity of -44 dB which is much more sensitive than the 30 dB needed to capture a human whisper. This meets the constraint set above and will allow the system to capture an individuals cognition even if a faint sound is heard from the human.

The COM-18343 speakers are full range and capture all the hard frequencies from 20 Hz - 20kHz set by the constraint above. But more importantly it will be able to produce sound between 2000 Hz through 5000 Hz which is the range most sensitive to the human ear. 

According to [4] for every doubling of distance tthe sound goes down -6dB. With a 1 meter minimum this would allow the BOB-19389 to function up to around 16 meters. The COM-18343 is a 2W speaker which can output around 93dB at max volume. Using the same method as above with a meter distane as minimum value, the speaker should function at a distyance of about 32 meters.

The total subsystem will consist of two parts. The microphone and speaker. The speakers weight is not specified, but simaliar speakers weig around 200 g, and the microphone, whose weight is also not specficed, has around a weight of 25 g. This brings the total subsystem weight to 225 g which is under the 675 g constraint limit set above. This will allow for some extra weight to be included for other subsystems.

  

## BOM


| Name of item | Description | Part Number | Manufacturer | Quantity | Price | Total |
|--------------|-------------|-------------|--------------|----------|-------|-------|
| Microphone | 	OPA344, SPH8878LR5H-1 MEMS Omnidirectional Microphones Audio Evaluation Board | B0B-19389 | SparkFun Electronics | 1 | $6.95 | $6.95 |
| Speaker | 4 Ohms General Purpose Speaker 4 W Top Rectangular | COM-18343 | SparkFun | 1 | $10.95 | $10.95 |
  
## Sources

[1] Berlinshoegazer, “EQing vocals: What's happening in each frequency range in the human voice,” Flypaper, 09-Jan-2023. [Online]. Available: https://flypaper.soundfly.com/produce/eqing-vocals-whats-happening-in-each-frequency-range-in-the-human-voice/#:~:text=The%20human%20ear%20can%20hear,from%20165%20to%20255%20Hz. [Accessed: 02-May-2023]. 

[2] “What noises cause hearing loss?,” Centers for Disease Control and Prevention, 08-Nov-2022. [Online]. Available: https://www.cdc.gov/nceh/hearing_loss/what_noises_cause_hearing_loss.html#:~:text=A%20whisper%20is%20about%2030,running%20is%20about%2095%20dB. [Accessed: 02-May-2023]. 

[3] T. Backstrom, “Note! these pages are deprecated and retained only for archiving purposes. our new location is https://speechprocessingbook.aalto.fi .Tom,” Aalto University Wiki, https://wiki.aalto.fi/pages/viewpage.action?pageId=151500905#:~:text=Generally%2C%20voice%20activity%20detection%20algorithms,bitrate%20whenever%20speech%20is%20absent. (accessed Sep. 8, 2023). 

[4] dsa2gamba and Abbottds, “Intensity and distance,” Understanding Sound, https://pressbooks.pub/sound/chapter/intensity-and-distance-april-2019-version/ (accessed Sep. 8, 2023). 

