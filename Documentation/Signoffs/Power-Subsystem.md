# Power Subsystem

## Functionality
This subsystem is responsible for powering all necessary devices that are present as part of the total sensing system.

## Constraints
| # | Description | Constraint | Source |
|--------|-------------|------------|--------|
| 1 | Operation time | The system must operate at full functionality for 15 to 60 minutes | Darpa[1] |
| 2 | Form of power | The power source for our system must be portable, and replaceable or rechargeable | The system is being designed to eventually be attached to a drone which will require an independent, portable power supply. Darpa[1] |
| 3 | Weight | The power system must weigh a max of 1.5 lbs  | From Darpa[1] and Conceptual Design |
| 4 | Powering the Jetson Nano | The Jetson Nano must maintain a supply voltage greater than or equal to 4.75 V via a 2.1 mm DC barrel jack. The Jetson Nano has a maximum voltage rating of 5.5 V and a maximum current rating of 5 A. The Nano consumes approximately 1.25 W at 4 A with no peripherals | This constraint originates from the computing subsystem required for data processing and to operate the on-board sensors. The specifications come from the Jetson Nano datasheets and NVIDIA forums [2][3][4] |
| 5 | Power Consumption | The system must effectively supply 1.1250 A at 5 V for a total power of 5.625 W | [9] [10] [11] [12] |

## Buildable Schematic
![Power Subsystem Buildable Schematic](https://github.com/Michaelwwest98/DARPA-Drone-Triage-Sensing-System/assets/123699820/a4a049ab-8726-47c9-a8cd-c67424ba8cbb)

## Analysis
1. The system must operate at full functionality for 15 to 60 minutes. The NP-F550 7.4 V, 2600 mAh is estimated to power the Jetson Nano with a 4 A draw for approximatley 40 minutes. The radar module, transmission module, microphone, and speaker will be powered directly from the Jetson Nano. 
2. The form of power shall be a battery. The battery chosen to power the sensing system is a 2 cell lithium-ion battery pack that is rechargable, relativley small in size, and low in weight in order to eventually be mounted to a drone.  
3.  The power system must be under 1.5 lbs. The power system is weighing in at just under 1 lb. This design complies with the weight constraint [5][6][8].
4.  The Jetson Nano requires a specific power supply. The buck converter/regulator is going to step down the voltage from 7.4 V to 5.0 V and limits the current to a maximum of 5 A. The buck converter uses op amps as feedback circuit to regulate output voltage. The battery adapter plate is going to allow easy connection to the battery pack and the regulator. The system will require two 2.1 mm DC barrel jacks with loose leads to connect the battery to the input of the regulator and the second one to connect the output of the regulator to the power supply input of the Jetson Nano. The connectors that will be used are 18 AWG which will be capable of handling 5V/5A. This design makes for an easy setup and meets all specifications for the Jetson Nano [5][6][7].

5. 
| # | Peripheral | Power Considerations | Source |
|---|------------|----------------------|--------|
| 1 | Radar Module | The minimum supply voltage is 4.75 V. The maximum supply voltage and current is 5.25 V at 65 mA. The typical supply voltage and current is 5.0 V at 55 mA. This gives a typical power consumption of 275 mW and a maximum power consumption of 341.25 mW. | IPS-937 24GHZ RADAR MODULE datasheet [9] |
| 2 | RAK811 LPWAN Breakout Module | The maximum supply voltage is 3.45 V. The typical supply voltage is 3.3 V. The minimum current consumption is 30 mA when transmitting a signal. | RAK811 LPWAN Breakout Module datasheet [10] |
| 3 | Microphone | The total power consumption is 4 W. | B0B-19389 datasheet [11] |
| 4 | Speaker | The maximum supply voltage is 3.6 V. At 3.6 V the device is tested to draw typically 0.265 mA. | COM-18343 datasheet [12] |

The peripherals run off of the Jetson's 5 V pin, 3.3 V pin, and the USB 2.0 ports. The 5 V pins are connected via a power rail. The 3.3 V pin is connected from the 5 V V_in through an MP2152 2A, step-down converter. The overall circuit is essentially the following diagram.

![Power System Circuit Analysis](https://github.com/Michaelwwest98/DARPA-Drone-Triage-Sensing-System/assets/123699820/9ed6de54-e216-444b-8dcf-685680a0d42a)

The total current seen by the 5 V source is 1.1250 A which, using Ohm's Law, results in a total power of 5.625 W. The battery and regulator circuit is capable of supplying up to 75 W. The Jetson can take up to 5 A. This system theoretically should work.

## BOM
| Product | Quantity | Price |
|---------|----------|-------|
| DC-DC 5A Buck Converter 4-38V to 1.25-36V Step-Down Voltage Regulator High Power Module with LED Display | 1 | $4.89 |
| 2 in 1 20W 3.6-30V to +-3-30V Adjustable Positive And Amp Negative Dual Output Power Supply Module | 1 | $6.89 |
| SmallRig NP-F Battery Adapter Plate Lite for Sony NP-F Battery, w/ 12V/7.4V Output Port, LED Low Battery Indicator - 3018 | 1 | $26.90 |
| CENTROPOWER 20 Pcs DC Power Cable 5A 12v DC Power Plug Cord Male Connectors 2.1mm x 5.5mm | 1 | $9.59 |
| Artman NP-F550 Battery 2-Pack and Wall Charger | 1 | $25.79 |
| Total | | $74.06 |

## Sources
[1] DARPA Triage Challenge. Available: https://triagechallenge.darpa.mil/.

[2] *Jetson Nano System-On Module Data Sheet*, NVIDIA, 2023. [Online]. Available: https://developer.download.nvidia.com/assets/embedded/secure/jetson/Nano/docs/JetsonNano_DataSheet_DS09366001v1.1.pdf?8eLmRr66qsksQXJ_jT0pYHP2nzXMwKkh8h9m4JFe71uQOMU6SlIKShEZEleOVIjLwHWbyeVYiWHL-CmATBrjWUmjz5shYbX3cMNRDZ5k1hQnDP41gFKH2lev54vQkSGbEfGR_aS_mAZMddBUAf4YUo4TDJTGolayv0I9WcmbHspkpz870pOBqNT19hApnA==&t=eyJscyI6IndlYnNpdGUiLCJsc2QiOiJkZXZlbG9wZXIubnZpZGlhLmNvbS9yZXN0cmljdGVkP2ZpbGVuYW1lPTQwMy5odG1sIn0=
[3] *Jetson Nano Develover Kit*, NVIDIA, 2020. [Online]. Available: https://developer.download.nvidia.com/assets/embedded/secure/jetson/Nano/docs/NV_Jetson_Nano_Developer_Kit_User_Guide.pdf?EJsH8ZYNz5pFvY3xfek_t8S719_1OlL2HyyEdrbWH7Cs4dW7W_T72B_ntKtwV55xuzUiQb5NFF1rIVcbmF7HqZH-PTEjKzl4Exc_hivvbH0cS7lEQrrqC8DaXltt33Db7GIt-2NOzTPLX7rsDxql2Vio-GiaGfss_qKMzmh3_SCBDiF2DB-_BsDl9ecCGWxQUxI=&t=eyJscyI6ImdzZW8iLCJsc2QiOiJodHRwczovL3d3dy5nb29nbGUuY29tLyJ9

[4] *Power supply considerations for Jetson Nano Developer Kit*, NNIDIA, 2019. [Online]. Available: 
https://forums.developer.nvidia.com/t/power-supply-considerations-for-jetson-nano-developer-kit/71637

[5] *DC-DC 5A Buck Converter 4-38V to 1.25-36V Step-Down Voltage Regulator High Power Module with LED Display*, icstation. Available: https://www.icstation.com/step-down-buck-converter-power-supply-module-125v-adjustable-voltmeter-p-3017.html

[6] *2 in 1 20W 3.6-30V to +-3-30V Adjustable Positive And Amp Negative Dual Output Power Supply Module*, AliExpress. Available: https://www.aliexpress.us/item/3256804028860260.html?src=google&aff_fcid=4f4e2b29191e40388e6ac755398bc5ec-1694653440148-04081-UneMJZVf&aff_fsk=UneMJZVf&aff_platform=aaf&sk=UneMJZVf&aff_trace_key=4f4e2b29191e40388e6ac755398bc5ec-1694653440148-04081-UneMJZVf&terminal_id=d06cb1cdc06c4998b4935111d106946f&afSmartRedirect=y&gatewayAdapt=glo2usa

[6] *SmallRig NP-F Battery Adapter Plate Lite for Sony NP-F Battery, w/ 12V/7.4V Output Port, LED Low Battery Indicator - 3018*, Amazon. Available: https://www.amazon.com/dp/B091TRMFYT?ascsubtag=amzn1.ideas.2WYYMHDV0VVNZ&linkCode=sl1&tag=jetsonhacks-20&linkId=3a4257f3f9f547ba799ddbcec22977d9&language=en_US&ref_=as_li_ss_tl

[7] *CENTROPOWER 20 Pcs DC Power Cable 5A 12v DC Power Plug Cord Male Connectors 2.1mm x 5.5mm, DC Pigtail Adapter Plug Socket Wire?for CCTV Security Camer*, Amazon. Available: https://www.amazon.com/dp/B0BTHSDF4S/ref=sspa_dk_detail_3?psc=1&pd_rd_i=B0BTHSDF4S&pd_rd_w=1OS6v&content-id=amzn1.sym.08ba9b95-1385-44b0-b652-c46acdff309c&pf_rd_p=08ba9b95-1385-44b0-b652-c46acdff309c&pf_rd_r=B74W16YJ43CMEFKHPWKW&pd_rd_wg=M4xV8&pd_rd_r=78ab97fe-0ffb-402f-b35f-0bdd04872f7e&s=industrial&sp_csd=d2lkZ2V0TmFtZT1zcF9kZXRhaWxfdGhlbWF0aWM#customerReviews

[8] *Artman NP-F550 Battery 2-Pack and Wall Charger for Sony NP F550, F530, F970, F960, F770, F750, F330, CCD-SC55, TR516, TR716, TR818, TR910, TR917 Camera, CN-160, CN-216 LED Video Light (2600mAh)*, Amazon. Available: https://www.amazon.com/dp/B078NRLSKL/ref=sspa_dk_detail_0?psc=1&pd_rd_i=B078NRLSKL&pd_rd_w=rglsi&content-id=amzn1.sym.08ba9b95-1385-44b0-b652-c46acdff309c&pf_rd_p=08ba9b95-1385-44b0-b652-c46acdff309c&pf_rd_r=WKYPTFJDH5F1FP8918S5&pd_rd_wg=r98KB&pd_rd_r=a3acff40-bd0e-4712-b060-39a785e03d4e&s=electronics&sp_csd=d2lkZ2V0TmFtZT1zcF9kZXRhaWxfdGhlbWF0aWM&spLa=ZW5jcnlwdGVkUXVhbGlmaWVyPUEyUUxSNzZQMjBLUlpWJmVuY3J5cHRlZElkPUEwNjM4OTE0MlczWFNPVlNaSEc3MyZlbmNyeXB0ZWRBZElkPUEwNjkyNzg5RzJJWVJMWlJIRTZDJndpZGdldE5hbWU9c3BfZGV0YWlsX3RoZW1hdGljJmFjdGlvbj1jbGlja1JlZGlyZWN0JmRvTm90TG9nQ2xpY2s9dHJ1ZQ==

[9] *IPS-937 24GHZ RADAR MODULE Datasheet*, Digikey. Available: https://www.digikey.com/en/products/detail/innosent-gmbh/80.00000358/10416543?utm_adgroup=General&utm_source=google&utm_medium=cpc&utm_campaign=PMax%20Shopping_Product_Zombie%20SKUs&utm_term=&utm_content=General&gclid=Cj0KCQjwl8anBhCFARIsAKbbpySVa5hng0yX4ISLjmgNrZj6kV_B27nqxPhVCxs_16I0LGLt4auF3hoaApTdEALw_wcB

[10] *RAK811 Breakout Board Datasheet*, RAK. Available: https://docs.rakwireless.com/Product-Categories/WisDuo/RAK811-Breakout-Board/Datasheet/?_gl=1%2a13xpun6%2a_ga%2aMTkxMjU2MzU1NC4xNjkzOTcxNjQ3%2a_ga_9MEJ39NSTZ%2aMTY5Mzk3NDM1MS4yLjEuMTY5Mzk3NDM1My41OC4wLjA.

[11] *SPH8878LR5H-1 Datasheet*, Sparkfun. Available: https://www.sparkfun.com/products/19389

[12] *COM-18343 Datasheet*, Sparkfun. Available: https://www.sparkfun.com/products/18343
