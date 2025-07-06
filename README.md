# Model M2 Type C
This project is a new board for the IBM model M2 that supports USB C

![Board Render](images/render.png)

## Features
- USB C
- Has QMK and its features (allows key remapping)
- Less power draw (probably)
- Open source

## Usage
1. Print the board either using a cheap foreign service such as [JLCPBC](https://jlcpcb.com/ "JLCPBC") for around $2-6 + shipping, or a domestic service such as [OSH Park](https://oshpark.com/ "OSH Park") for around $22.
2. Acquire the components

|Reference|Type     |Value         |Qty|Link                           |
|---------|---------|--------------|---|-------------------------------|
|C1,C2    |Capacitor|22pF          |2  |                               |
|C3       |Capacitor|1uF           |1  |                               |
|C4,C5,C6 |Capacitor|0.1uF         |3  |                               |
|C7       |Capacitor|10uF          |1  |                               |
|D1,D2,D3 |LED      |Green, 3.3v   |3  |                               |
|F1       |Fuse     |500mA         |1  |https://mou.sr/447NG73         |
|R1,R2    |Resistor |5.1k          |2  |                               |
|R3,R4    |Resistor |22            |2  |                               |
|R5,R6    |Resistor |10k           |2  |                               |
|R7,R8,R9 |Resistor |270           |3  |                               |
|SW1      |Button   |6xH7.3mm      |1  |                               |
|U1       |ESD Diode|PRTR5V0U2X    |1  |https://mou.sr/3vXlnaQ         |
|U2       |Chip     |AT90USB1286-AU|1  |https://mou.sr/4kNduMC         |
|Y1       |Crystal  |16MHz         |1  |https://mou.sr/4ebH8ZG         |
|USB1     |Port     |TYPE-C-31-M-12|1  |[keeb.io link](https://keeb.io/products/usb-c-port-12-pin-hro-type-c-31-m-12 "USB-C Port - 12-pin - HRO")|
|         |Screw    |M3            |1  |Harvest from the old board ([or buy an alternative](https://www.mcmaster.com/91223A411/ "McMASTER-CARR part 91223A411"))|
3. Put it together. It's possible to solder the SMD components manually with a soldering iron, but if you are able to find a hot air gun or a reflow oven, it'll be easier. Reference the visual BOM to see what goes where (it is located in [bom/ibom.html](https://htmlpreview.github.io/?https://github.com/lithium-hypercube/Model-M2-Type-C/blob/master/bom/ibom.html "Interactive bill of materials link")).
	- You should have balls of solder instead of point on the underside of the PCB to not damage the membrane. To do this:
		1. Solder the components to the board normally
		2. Use side cutters to cut away the solder/remaining component legs on the underside (except the screw). Try to cut close to the PCB but don't damage the traces.
		3. Add more solder/flux to the pad. Try to get a smooth blob of solder. Don't add too much though
5. Install firmware and test the board by shorting some pads (carefully)
6. Cut the keyboard's case to make the USB C connector hole larger (I used a fretsaw to do this)

The traces on the membrane may have corroded over time. You can use a multimeter to check for connectivity. Note that trace resistance might be high, so the multimeter might not make a sound even if there is a connection. Try not to scratch the traces. I used conductive copper tape (one where the sticky side is also conductive) to repair damaged traces on mine.

The exposed traces on the membrane that touch the board did not provide a stable connection in my case. Try using a conductive pen (like a circuitscribe) to repaint them (I tried using copper tape but the connection was unreliable). Pushing down on the board might sometimes temporarily resolve the problem.

## Firmware
This board is fully compatible with QMK.

To install the firmware to your keyboard:
- Clone the qmk_firmware repo
	```
	git clone https://github.com/lithium-hypercube/qmk_firmware
	```
- [Setup the build environment](https://docs.qmk.fm/#/getting_started_build_tools)
- [Enter the keyboard into bootloader mode](https://github.com/lithium-hypercube/qmk_firmware/tree/master/keyboards/ibm/model_m2/m2_usbc#bootloader "Link to QMK firmware readme")
- Make and flash the firmware
	```
	make ibm/model_m2/m2_usbc:default:flash
	```
[More details](https://github.com/lithium-hypercube/qmk_firmware/tree/master/keyboards/ibm/model_m2/m2_usbc "Link to QMK firmware")

Note that the firmware only supports the ANSI layout, but you can probably fix that pretty easily if you have access to the ISO one (I don't). Most keys should work even if you use the wrong one.

## Other
If you have any problems/comments, or find anything that could be improved, please submit issue or a pull request!
