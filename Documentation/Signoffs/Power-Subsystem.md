# Power Subsystem

## Functionality
This subsystem is responsible for powering all necessary devices that are present as part of the total sensing system.

## Constraints
| Description | Constraint | Source |
|-------------|------------|--------|
| Operation time | The system shall operate at full functionality for 15 to 60 minutes | Darpa[1] |
| Form of power | The power source for our system must be portable, and replaceable or rechargeable | The system is being designed to eventually be attached to a drone which will require an independent, portable power supply. Darpa[1] |
| Weight | The team has allocated 1.5 lbs for the power system | From Darpa[1] and Conceptual Design |
| Powering the Jetson Nano | The Jetson Nano requires a power supply capable of delivering 5V/2A and must maintain a supply voltage greater than or equal to 4.75 V via a 2.1 mm DC barrel jack. The Jetson Nano has a maximum voltage rating of 5.5 V and a maximum current rating of 5 A | This constraint originates from the computing subsystem required for data processing and to operate the on-board sensors. The specifications come from the Jetson Nano datasheets and NVIDIA forums [2][3][4] |

## Buildable Schematic
![Power system schematic](https://github.com/Michaelwwest98/DARPA-Drone-Triage-Sensing-System/assets/123699820/c391588f-195b-403e-a3a3-9f4f8c9ef64f)


## Analysis
- The system must operate at full functionality for 15 to 60 minutes. The NP-F750 7.4 V 5600 mAh is estimated to power the Jetson Nano with a 4 A draw for approximatley one and a half hour which overshoots our constraint in a good way because the 15 to 60 minute run-time comes from Darpa and their testing simulations for the challenge, so it is better that our system operate for a longer duration. The sensors will use the power connections on the Jetson. The power consumption will have to be tested as the load is increased on the Jetson. Also, the team expects efficiency losses with the coupling of the battery and the buck converter/regulator.
- The form of power shall be a battery. The battery chosen to power the sensing system is a 2 cell lithium-ion battery pack that is rechargable, relativley small in size, and low in weight in order to eventually be mounted to a drone.  
-  The power system must be under 1.5 lbs. The power system is weighing in at just under 1 lb. This design complies with the weight constraint [5][6][8].
-  The Jetson Nano requires a specific power supply. The buck converter/regulator is going to step down the voltage from 7.4 V to 5.0 V and limits the current to a maximum of 5 A. The buck converter uses op amps as feedback circuit to regulate output voltage. The battery adapter plate is going to allow easy connection to the battery pack and the regulator. The system will require two 2.1 mm DC barrel jacks with loose leads to connect the battery to the input of the regulator and the second one to connect the output of the regulator to the power supply input of the Jetson Nano. The connectors that will be used are 18 AWG which will be capable of handling 5V/5A. This design makes for an easy setup and meets all specifications for the Jetson Nano [5][6][7]. 

## BOM
| Product | Quantity | Price |
|---------|----------|-------|
| [2 Pack] DC-DC 5A Buck Converter 4-38V to 1.25-36V Step-Down Voltage Regulator High Power Module with LED Display | 1 | $13.99 |
| SmallRig NP-F Battery Adapter Plate Lite for Sony NP-F Battery, w/ 12V/7.4V Output Port, LED Low Battery Indicator - 3018 | 1 | $26.90 |
| CENTROPOWER 20 Pcs DC Power Cable 5A 12v DC Power Plug Cord Male Connectors 2.1mm x 5.5mm | 1 | $9.59 |
| Neewer NP-F750 2-Pack 5600mAh Li-ion Replacement Battery with USB Charger, Compatible with Sony NP-F550 570 750 770 930 950 FM55H FM500H QM71 QM91 QM71D LED Light, Monitor, Motorized Slider | 1 | $50.01 |
| Total | | $100.49 |

## Sources
[1] DARPA Triage Challenge. Available: https://triagechallenge.darpa.mil/.

[2] *Jetson Nano System-On Module Data Sheet*, NVIDIA, 2023. [Online]. Available: https://developer.download.nvidia.com/assets/embedded/secure/jetson/Nano/docs/JetsonNano_DataSheet_DS09366001v1.1.pdf?8eLmRr66qsksQXJ_jT0pYHP2nzXMwKkh8h9m4JFe71uQOMU6SlIKShEZEleOVIjLwHWbyeVYiWHL-CmATBrjWUmjz5shYbX3cMNRDZ5k1hQnDP41gFKH2lev54vQkSGbEfGR_aS_mAZMddBUAf4YUo4TDJTGolayv0I9WcmbHspkpz870pOBqNT19hApnA==&t=eyJscyI6IndlYnNpdGUiLCJsc2QiOiJkZXZlbG9wZXIubnZpZGlhLmNvbS9yZXN0cmljdGVkP2ZpbGVuYW1lPTQwMy5odG1sIn0=
[3] *Jetson Nano Develover Kit*, NVIDIA, 2020. [Online]. Available: https://developer.download.nvidia.com/assets/embedded/secure/jetson/Nano/docs/NV_Jetson_Nano_Developer_Kit_User_Guide.pdf?EJsH8ZYNz5pFvY3xfek_t8S719_1OlL2HyyEdrbWH7Cs4dW7W_T72B_ntKtwV55xuzUiQb5NFF1rIVcbmF7HqZH-PTEjKzl4Exc_hivvbH0cS7lEQrrqC8DaXltt33Db7GIt-2NOzTPLX7rsDxql2Vio-GiaGfss_qKMzmh3_SCBDiF2DB-_BsDl9ecCGWxQUxI=&t=eyJscyI6ImdzZW8iLCJsc2QiOiJodHRwczovL3d3dy5nb29nbGUuY29tLyJ9

[4] *Power supply considerations for Jetson Nano Developer Kit*, NNIDIA, 2019. [Online]. Available: 
https://forums.developer.nvidia.com/t/power-supply-considerations-for-jetson-nano-developer-kit/71637

[5] *[2 Pack] DC-DC 5A Buck Converter 4-38V to 1.25-36V Step-Down Voltage Regulator High Power Module with LED Display*, Amazon. Available: https://www.amazon.com/dp/B085T73CSD?ascsubtag=amzn1.ideas.2WYYMHDV0VVNZ&linkCode=sl1&tag=jetsonhacks-20&linkId=18cbbd2d9accf7610e8f6b65517ac8b5&language=en_US&ref_=as_li_ss_tl

[6] *SmallRig NP-F Battery Adapter Plate Lite for Sony NP-F Battery, w/ 12V/7.4V Output Port, LED Low Battery Indicator - 3018*, Amazon. Available: https://www.amazon.com/dp/B091TRMFYT?ascsubtag=amzn1.ideas.2WYYMHDV0VVNZ&linkCode=sl1&tag=jetsonhacks-20&linkId=3a4257f3f9f547ba799ddbcec22977d9&language=en_US&ref_=as_li_ss_tl

[7] *CENTROPOWER 20 Pcs DC Power Cable 5A 12v DC Power Plug Cord Male Connectors 2.1mm x 5.5mm, DC Pigtail Adapter Plug Socket Wire?for CCTV Security Camer*, Amazon. Available: https://www.amazon.com/dp/B0BTHSDF4S/ref=sspa_dk_detail_3?psc=1&pd_rd_i=B0BTHSDF4S&pd_rd_w=1OS6v&content-id=amzn1.sym.08ba9b95-1385-44b0-b652-c46acdff309c&pf_rd_p=08ba9b95-1385-44b0-b652-c46acdff309c&pf_rd_r=B74W16YJ43CMEFKHPWKW&pd_rd_wg=M4xV8&pd_rd_r=78ab97fe-0ffb-402f-b35f-0bdd04872f7e&s=industrial&sp_csd=d2lkZ2V0TmFtZT1zcF9kZXRhaWxfdGhlbWF0aWM#customerReviews

[8] *Neewer NP-F750 2-Pack 5600mAh Li-ion Replacement Battery with USB Charger, Compatible with Sony NP-F550 570 750 770 930 950 FM55H FM500H QM71 QM91 QM71D LED Light, Monitor, Motorized Slider*, Amazon. Available: https://www.amazon.com/dp/B08LDL4QSD?ascsubtag=amzn1.ideas.2WYYMHDV0VVNZ&linkCode=sl1&tag=jetsonhacks-20&linkId=f1adce182e2bbb87e54502f4667b7a19&language=en_US&ref_=as_li_ss_tl

