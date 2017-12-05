# LoRa-concentrator

A Real LoRa Gateway using SX1301 and SX125X

Current version is designed for Raspberry Pi and another board for Pi Zero

![Alt text](/Version2/RPI/DSC02654.jpg)
for Raspberry Pi, there is two SX125X, but for Pi Zero I strip down Radio_A for better layout.
Both of them have a Max-7Q GPS module, which provide PPS to SX1301 and Raspberry Pi(GPIO05),
and provide NEMA through Raspberry Pi's UART port.

At the RF frontend, the main difference is that I didn't combine RX/TX using a RF switch,
and there is no on-board PA/LNA, but I did put a SAW filter. The reason not to is that I can use external LNA which is right under the antenna, there is a bias inductor right after RX port, which is connected to Raspberry Pi's 5V power rail.  

The current RPI version is designed for SX1257, but it is easy to migrate to SX1255, just put SX1255 on SX1257 and change RF passive components according to SX1255 datasheet.

I've tested both SX1255 & SX1257, and also two SX1301 connected to Raspberry Pi at the same time (there is a jumper for CE0/CE1).

last but not least, I've launch some High Altitude Balloon and using it as my multi-channel receiver. Which reach about 100Km by BW 125Khz CR 4/5 SF 7 @ 432Mhz with 16dBm power + MAX2640 LNA.

And RPI Version is currently sold on Tindle!
https://www.tindie.com/products/will123321/sx1308-raspberry-pi-lora-gateway-board/

---

**Update: 2017/09/01**
The version 2 is working now, I've changed the design to build a Raspberry Pi Zero hat  
But because board size limit, I removed Radio_A for layout simplicity, also changed the 1.8V power supply from LDO to step-down, and pull the 3.3V directly from Raspberry Pi, more over, added GPS module for PPS supply.

![Alt text](/Version2/RPI_Zero/Ver1/version2_2.jpg)





---
**Version 1**
note that I haven't get it working yet, stuck in PLL lock  
but SPI test seems to be OK.  

![Alt text](/Version1/pcb.jpg)


