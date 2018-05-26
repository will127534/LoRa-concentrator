# LoRa-concentrator

A Real opensource LoRa Gateway using SX1301/SX1308 and SX1255/SX1257

**Version 3**
![Alt text](/Version3/RPI/DSC04207.jpg)
Version 3 is designed for Raspberry Pi, same setup like Version 2, but I added LNA/PA and RF switch, and move to 4-layer board design
PA(RFPA0133) and RF switch(RFSW1012) is same as Microchip's LoRa gateway, but I changed LNA to SKY67150-396LF which have a much better Noise Figure(0.28dB).
Also note that I also used a wide bandwidth ceramic balun(800-1000Mhz) instead of discrete balun.

868Mhz and 915Mhz is mostly the same, just need to change four filter, both part number are in PCB files and BOM file. 

For power supply, 1.8V DC-DC step down has changed to TPS62061, but it is pin-to-pin replaceable with ETA3410. For 3.3V RF power, there is two option,
one is TPS7A470, which is a Ti's high-end LDO with 4 µVRMS noise, and 55dB PSRR, the other one is LP5912-3.3, which is cheaper but still gets 12 µVRMS noise and 75dB PSRR.

GPS module is still Max-7Q, which provide PPS to SX1301/8 and Raspberry Pi(GPIO05),
and provide NEMA through Raspberry Pi's UART port. There is a jumper for shuting down GPS module if you want to stack other board.

Lastly, it support PoE header on Raspberry Pi 3B+, so you can stack PoE hat on top of the board.(Just make it clear that the board doesn't have PoE on board, but just the pin header to support other PoE hat).

And RPI Version is currently sold on Tindle!
https://www.tindie.com/products/will123321/sx1308-raspberry-pi-lora-gateway-board/


**Version 2**
Version 2 is designed for Raspberry Pi and another board for Pi Zero

![Alt text](/Version2/RPI/DSC02654.jpg)
for Raspberry Pi, there is two SX125X, but for Pi Zero I strip down Radio_A for better layout.
Both of them have a Max-7Q GPS module, which provide PPS to SX1301 and Raspberry Pi(GPIO05),
and provide NEMA through Raspberry Pi's UART port. There's also a jumper for shuting down GPS module if you want to stack other board.

At the RF frontend, the main difference is that I didn't combine RX/TX using a RF switch,
and there is no on-board PA/LNA, but I did put a SAW filter. The reason not to is that I can use external LNA which is right under the antenna, there is a bias inductor right after RX port, which is connected to Raspberry Pi's 5V power rail.  

The current RPI version is designed for SX1257, but it is easy to migrate to SX1255, just put SX1255 on SX1257 and change RF passive components according to SX1255 datasheet.

I've tested both SX1255 & SX1257, and also two SX1301 connected to Raspberry Pi at the same time (there is a jumper for CE0/CE1).

last but not least, I've launch some High Altitude Balloon and using it as my multi-channel receiver. Which reach about 100Km by BW 125Khz CR 4/5 SF 7 @ 432Mhz with 16dBm power + MAX2640 LNA.

---
**Version 1**
note that I haven't get it working yet, stuck in PLL lock  
but SPI test seems to be OK.  

![Alt text](/Version1/pcb.jpg)


