# Voice Activity Detection Subsystem #

## Subsystem Function:

The purpose of this subsystem is to detect an individual's responsiveness or cognition through the use of call and response techniques. The subsystem will activate once an individual heartbeat has been detected. The speaker will play a sound with an instruction to say something. Once the instruction is given, the microphone will begin transmitting audio to a computing system which will then run an algorithm to detect if a human voice responded or not allowing the total system to know if the individual being tested has cognition or not.


## Specs and Constraints			


| Description | Constraint | Source of Constraint |
|-------------|------------|----------------------|
| (1) VAD System | Must detect the presence of a human voice from auddio signal | Functionality of subsytem with respect to triage algorithm |
| (2) Microphone | Must pick up a minimum sound pressure level of 30 dB SPL from at least 1 meter away | Volume level of a human whisper. [2] DARPA distance constraint |
| (3) Microphone | Must sense frequencies from 100 Hz to 3000 Hz | Frequency range of average man is 100-900 Hz while female is 300 - 3000 Hz.[1] |
| (4) Speaker | Must output sound at a volume heard from at least 1 meter away | Individual can hear sound from the speaker |
| (5) Speaker | Must play sound clips between 20 Hz- 20000 Hz | Frequency range an individual’s ear can hear [1] |
| (6) Distance | Must function with noise from drone from at least 1 meter away | From DARPA constraints |
| (7) Weight | he drone specified in conceptual design had a max load of 2.7 kg. Seeing as 4 subsystems will be attached to the drone. The max weight must not exceed 675g. | From DARPA constraints/ Conceptual design |
| (8) Safety | Speaker output must not be louder than 120 dB | Levels at 120 dB can cause immediate harm to an individual's hearing [2] |  


## Wiring Schematics



![image](https://user-images.githubusercontent.com/79685126/235611053-69878c8b-1b4f-4cb6-9a22-76f6e17996e6.png)


Figure1. Wire Diagram for the total subsystem

## Analysis:

(1)

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

(2),(3)

Sound Pressure Level (SPL) is a way to measure sound intensity compared to human hearing. 0 dB SPL is the minimum a person can hear, while 30 dB SPL is the sound level of a human whisper at a 1 meter distance. The BOB-19389 datasheet states a signal to noise ratio (SNR) of 67 dBV/Pa taken from a 94 dB SPL signal. To calculate the minimum sound level that the microphone can pick up the noise floor level, or the point at which the noise distorts the signal coming in that no signal can be ditected, needs to be found. This is done by simply finding the differnce between the signal used to measure the SNR and the SNR itself. In the case of BOB-19389 this is 94 - 67 which equals 27 dB. This means that from the meter distance the microphone will be able to pick up a human whisper of 30 dB without the signal being distored.      
The datasheet of the BOB-19389 also states a 3dB rolloff frequency range of 7 Hz - 19 kHz which includes the threshold set by the constraints to capture human voice frequencies. The BOB-19389 will be able to capture the 100-3000 Hz range set by the constraint.

(4),(5)

To see the sound level output of the speaker, the intensity of the speaker must first be calculated. The equation for intensity is I = P / (4 * pi * r) where P is the power of the system and r is the distance from source. The COM-18343 datasheet states the speaker includes 2 X 2 W speakers and the constarint puts the distance at 1 meter. The intensity can then be calculated to be 0.3183 W/m^2. This value can be converted to dB scle using the equation dB = 10 * log (I / Io), where I is intensity calcuted and Io is the threshold intensity for human hearing which is set to 1*10^-12 W/m^2. The total sound level capable of being outpued by the speaker is 115 dB. With the drone noise being around the value of 96 dB, this means the COM-18343 is able to output sound that is louder than the drone noises this system will be attached to.    
The COM-18343 datasheet also states the speaker is full range and captures all the heard frequencies from 20 Hz - 20kHz set by the constraint above. But more importantly it will be able to produce sound between 2000 Hz through 5000 Hz which is the range most sensitive to the human ear. 

(6)

The COM-18343 speakers will be able to overcome the noises outside this system such as drone noise, but what about the BOB-19389 microphone? The BOB-19389 is an omnidirectional microphne which is useful to capture sounds that are not necessarily under the microphone, but will also capture other noises such as the drone it is attached to. To solve this issue the casing for this subsystem can create a soundproof barrier for the back of the micrphone eliminating half of the direction sound can be picked up from and making the leakage that does come noise that will not have enough inesity to cause issues for the microphone. The BOB-19389 datasheet also states a max of 134 dB SPL meaning that even if the full sounds are picked up, it will not damage the microphone.

(7)

The total subsystem will consist of two parts. The microphone and speaker. The speakers weight is not specified, but simaliar speakers weig around 200 g, and the microphone, whose weight is also not specficed, has around a weight of 25 g. This brings the total subsystem weight to 225 g which is under the 675 g constraint limit set above. This will allow for some extra weight to be included for other subsystems.

(8)  

As mentioned in the previous analysis, the COM-18343 is not capable of outputing the sound level listed in the constarint allowing this system to be safe from damaging the indivudals hearing. The max sound level is 115 dB while the max level to be an immediate damage to an individuals hearing is 120 dB.


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

