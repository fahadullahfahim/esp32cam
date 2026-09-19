I have this kock off esp32 cam module , and I couldn't find any helpful markings from its body to match agains official documents. Anyways I will continue studying this cheap module on my hand. 

# esp32 pin mapping
its difficult to read the silk text due to poor print quality, but I will make educated guess here as I proceed. Only 16 GPIO pins are accesible in the module due to camera and the microsd reader taking up a lot of GPIO pins internally.
Legends written on pcb :
1. 5v
2. gnd
3. io 12
4. io 13
5. io 15
6. io 14
7. io 2
8. io 4
9. 3.3v
10. io 16
11. io 0
12. gnd
13. vcc
14. UOR
15. UOT
16. GND/R
Reading from the [datasheet](https://documentation.espressif.com/esp32_datasheet_en.html#pins) I will refine this list as such :

| name                   | no  | type | function                                                                          |
| ---------------------- | --- | ---- | --------------------------------------------------------------------------------- |
| VDDA                   | 1   | P    | Analog power supply (2.3 V ∼ 3.6 V                                                |
| VDD3P3                 | 3   | P    |                                                                                   |
| GND                    | 49  | P    |                                                                                   |
| GPIO2                  | 22  | I/O  | ADC2_CH2, RTC_GPIO12, TOUCH2, HSPIWP, HS2_DATA0, SD_DATA0                         |
| GPIO0                  | 23  | I/O  | GPIO0, ADC2_CH1, RTC_GPIO11, TOUCH1, EMAC_TX_CLK, CLK_OUT1                        |
| GPIO4                  | 24  | I/O  | GPIO4, ADC2_CH0, RTC_GPIO10, TOUCH0, EMAC_TX_ER, HSPIHD, HS2_DATA1, SD_DATA1      |
| GPIO16                 | 25  | I/O  | GPIO16, HS1_DATA4, U2RXD, EMAC_CLK_OUT                                            |
| VDD_SDIO               | 26  | P    | Output power supply: 1.8 V or the same voltage as VDD3P3_RTC                      |
| U0RXD                  | 40  | I/O  | GPIO3, U0RXD, CLK_OUT2                                                            |
| UOTXD                  | 41  | I/O  | GPIO1, U0TXD, CLK_OUT3, EMAC_RXD2                                                 |
| MTMS (slave select)    | 17  | I/O  | **GPIO14**, ADC2_CH6, RTC_GPIO16, TOUCH6, EMAC_TXD2, HSPICLK, HS2_CLK, SD_CLK,    |
| MTDI (master data in)  | 18  | I/O  | **GPIO12**, ADC2_CH5, RTC_GPIO15, TOUCH5, EMAC_TXD3, HSPIQ, HS2_DATA2, SD_DATA2   |
| MTCK (master clock)    | 20  | I/O  | **GPIO13**, ADC2_CH4, RTC_GPIO14, TOUCH4, EMAC_RX_ER, HSPID, HS2_DATA3, SD_DATA3, |
| MTDO (master data out) | 21  | I/O  | **GPIO15**, ADC2_CH3, RTC_GPIO13, TOUCH3, EMAC_RXD3, HSPICS0, HS2_CMD, SD_CMD     |
|                        |     |      |                                                                                   |
The GND/R pins seems like used for Reset operations. 