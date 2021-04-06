# ESP32SmartBoard_PCB
**KiCad project of a Printed Cuircit Board (PCB) for ESP32 with Temperature/Humidity/CO2 Sensors, User LEDs and Buttons.**

In the past I've implemented various Smart Projects with the ESP32 on break-out boards. On the one hand, break-out boards are very useful because they make hardware modifications as easy as software changes. On the other hand, it is very cumbersome to build several copies of the same circuit with break-out boards. Furthermore, they are mechanically fragile and not really particularly visually appealing. Therefore they are not very suitable for permanent use in the visible area of living rooms.

For this reason I designed the **ESP32SmartBoard_PCB**, which combines different projects on a single, professionally producible PCB. This allows now for reproducing multiple copies of a device without great effort and hide them in a small housing if necessary.

## Board Features

The *ESP32SmartBoard_PCB* contains the following components:
- ESP32 Development Kit
- DHT22 (combined temperature and humidity sensor)
- MH-Z19 (CO2 sensor with integrated temperature sensor)
- 9 freely usable user LEDs (LED0..LED8, arranged in one row and usable as a LED Bar)
- 3 freely usable user Buttons (KEY0, KEY1, BLE_CFG)

![\[kicad_3d_model\]](Documentation/ESP32SmartBoard_PCB.3d-model.png)

## Board Description

The *ESP32SmartBoard_PCB* is a two-layer Printed Circuit Board (PCB), assembled on one side and only uses THT components (Through Hole Technology) that are very easy to solder. It can therefore be used very easily also by students and hobbyists.

The values of all components are specified in the [Schematic](Documentation/ESP32SmartBoard_PCB.sch.pdf).

The PCB size and the positions of the mounting holes allow installation in the plastic universal housing of 135 x 95 x 45 mm (article number 523117). This polystyrene housing (EPS) can be easily processed mechanically (e.g. cut out a viewing window for the LED Bar). It is available from various providers on the Internet.

![\[ESP32SmartBoard_OpenFrame_with_Box\]](Documentation/ESP32SmartBoard_OpenFrame_with_Box.jpg)

By searching in the Internet, several PCB manufacturers can be found who are able to directly import the KiCad layout file [ESP32SmartBoard_PCB.kicad_pcb](ESP32SmartBoard_PCB/ESP32SmartBoard_PCB.kicad_pcb). The PCBs with silkscreen (assembly printing) on the top are then sent by post after a few days.

## Power Supply

There are following options for the power supply of the board:
- Via USB connection of the ESP32 Development Kit (in this case Pin15/Vin of the ESP32DevKit acts as an output and supplies the rest of the circuit)
- Supply of 5 ... 6VDC to connector J1 (in this case the rest of the board supplies the ESP32DevKit and Pin15/Vin acts as an input)

## Commissioning

With the Arduino sketch from the [ESP32SmartBoard_IoCheck](https://github.com/ronaldsieber/ESP32SmartBoard_IoCheck) repository, all components of the board can be checked for correct function after assembly. The sketch is also a good starting point for new software projects based on this board.

## Schematic Symbols, Footprints and 3D Models

Not all schematic symbols, footprints and 3D models required for *ESP32SmartBoard_PCB* are contained in the native installed KiCad library. [External_KiCad_Parts.txt](Documentation/External_KiCad_Parts.txt) lists the additional components and their download links.

## Practice Notes

- The user LEDs are arranged in one row and can be used as a LED Bar. The colors of the LEDs should be selected according to the respective application. For example, to show the CO2 level in the form of a scale, the following grouping is suitable:
  * LED0..LED2: green = excellent
  * LED3..LED5: yellow = acceptable
  * LED6..LED8: red = critical

- It seems that there are several versions of the ESP32 Development Kit and the MH-Z19 CO2 sensor with pins of different widths. In my components, the diameter of the connection pins are larger than the diameter of the soldering pads in the footprint. This prevented me from soldering the components directly onto the board. However, I was able to solve the problem by using Pin Headers (see image above). The solder connections of the Pin Headers are small enough for the solder pads and the ESP32 Development Kit and MH-Z19 CO2 sensor can be easily plugged in.

## Software Projects for the ESP32SmartBoard

 - [ESP32SmartBoard_IoCheck](https://github.com/ronaldsieber/ESP32SmartBoard_IoCheck) - Checking of all components during commissioning and starting point for new software projects based on this board.
   
 - [ESP32SmartBoard_HttpSensors](https://github.com/ronaldsieber/ESP32SmartBoard_HttpSensors) - Embedded WebServer based Arduino Sketch for ESP32SmartBoard
   
 - [ESP32SmartBoard_MqttSensors](https://github.com/ronaldsieber/ESP32SmartBoard_MqttSensors) - MQTT Client based Arduino Sketch for ESP32SmartBoard

