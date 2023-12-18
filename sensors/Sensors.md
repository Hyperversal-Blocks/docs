## Introduction
Micro controllers: integrated computers to run simple software/programs at low power.
Arduino are circuit boards consisting of processors or micro controllers chips on them along with other stuff.
Arduino also consists of their own software which allows us to configure their products directly with its own programming language.

## Arduino Hardware
### Micro Controllers
1. Consist of micro controllers connected with resonator which controls how fast a micro controller runs.
2.Another micro controller chip in the center which allows for connecting the board with a computer and lets us send messages back and forth. Its also responsible for uploading the software created to the main micro controller. 
3. Has a built in voltage regulator which is set to 5volt. There is also a reset button which reboots the Arduino program. 

### Pin Connectors: 
1. Power pins for circuitry which allows for wire connection to the circuitry (allow connections up to few milli-amps).
2. TX RX pins are for sending and receiving serial data from bluetooth or wifi modules and etc.
3. Pin 2 to Pin 13 are for digital inputs and outputs in the form of 0s and 1s which are known as first and second states. However these micro controller pins can also be used for third state in which instead of sending the digital input/output, we send the voltage as the digital input for example: 5 volts for 1, 0volts for 0 or voltage that is expected on the pin is interpreted as 0 or 1 (Tristate Logic).
4. 6 Analog pins next to the reset button. They can be used to measure continuous voltages from 0-5volts. 
5. Some pins containing tilda infront of them can be used to output pulse width modulated square waves.

Know How: Pulse Width Modulated Square waves
https://www.youtube.com/watch?v=pFl-swR8BRo for pwm
When pulses being sent to the circuit, Pulse width is the pulse generated by the voltage being applied to the circuit. Important components to these pulse widths are switching frequency and duty cycle.
  
Switching Frequency and Duty Cycle
Switching Frequency: Should be optimum as the output (say LED light turning on) varies on how fast the switching frequency of the circuit is. This can vary from 100hz to kilo hz. 
Duty Cycle: The ratio of ON time to the total time. Or the pulse duration during which its set to ON state. Controlling the width of the pulse allows us to control the duration of the current.

## Arduino Software and Coding
Arduino software is its own ide, which is downloaded on computer. The codes are written there and then loaded into the board. For coding, C++ is the native language for Arduino. 

### How it works
It is a programmable circuit board consisting of micrcontrollers. Once the board is connected to computer, we feed it instructions/codes using the ide to carry out. These codes are written in a simplified version of c++ language. Programs developed through Arduino Programming Language are known as sketch and saved with file extension of .ino. 


### Why is it used/ Advantages
1. Easy to use and program.
2. Can be used to create low cost scientific equipment motion activated lights, rc light switches, portable humidifier etc.

## Raspberry Pi
A mini computer or a microprocessor which uses python language.

### Hardware
1. Center: Has the cpu and ram 
2. Corner: Wifi module
3. Connector pins, usb ports, ethernet ports, camera lens, and sd card port which serves as its main memory.

### Software
Involves downloading raspberry pi os on computer which can be programmed and controlled using python script. The programs are written and run directly within the operating system, which is due to the similarities it has with an actual computer. Operating system is usually linux.

## Arduino vs Raspberry

Both have cpu to execute instructions, timer, memory as well as i/o pins
Key difference lies on io pins as well as what they are designed for: 

1. Micro Controller io pins are stronger than microprocessor io pins which require transistors meaning it allows for more current to flow across the board.
2. Micro controllers are slightly slower in terms of processing as compared to microprocessors who are specifically designed to carry out processes. 

In terms of general specifications, the raspberry pi is stronger than arduino due to better ram, register size and clocking speed even though it comes at the cost of more power consumption as well as limiting max i/o current that can flow through its circuit (arduino having 40mA whereas raspberry pi having only 5mA).

However, the decision on which device is better entirely depends upon what project is to be carried out.
Arduino is designed to carry out applications which involves controlling small devices such as lcds, motors and sensors.
Raspberry pi is designed to carry out tasks which require higher level of data processing such as carrying out complex math queries, creating or running user interface etc.

## Why We Are using Arduino
As our project relies on the use of various sensors, we will be using arduino. It makes creating interface for the sensors easier as it already provides us with a software ide for programming meaning the only hardware required are breadboard and connecting wires to interface sensors with the Arduino.






## 1. NodeMcu Lua Wifi (based on ESP8266 CP2102)

NodeMCU is a software/hardware development environment built around a chip known as esp8266 (system on a chip). The chip consists of computer elements such as cpu, ram, wifi/networking, an operating system etc. It can be used for IoT projects and is similar to Arduino.

### Disadvantage: 
1. Harder to access and use. Wires with appropriate voltage must be connected to pins for even simplest of tasks i.e. powering on, sending keystroke to computer on chip.
2. It must be programmed on a low level machine instruction which is interpreted by the chips hardware. 

### Advantages over Arduino:
Some arduino boards do not have wifi capabilities and may have serial data port instead of a usb port.

## 2. HC05 Bluetooth wireless serial module

It is a bluetooth module, designed for wireless communication. It allows all devices to communicate with each other using bluetooth.
Consists of 6 pins: 

1. Key/EN: It brings the bluetooth module to AT command mode(Attention command mode: changes default settings of bluetooth). By default it is set to data mode. Command mode is when the module performs certain actions such as scanning for devices, data rates and other operations such as changing device names or pin code. The Data mode refers to when the bluetooth module acts as a gateway allowing for data to be sent or received between the devices. The switching of these modes depends on the baud rate (measure of number of changes to the signal that propogates through the circuit/transmission medium). The default baud rate for command mode is 38400bps and 9600 for data mode. 
2. VCC: Connect 5v or 3.3v to this pin.
3. GND: Ground pin
4. TXD: Transmit Serial Data i.e. data is received wirelessly through bluetooth module and will be transmitted out serially.
5. RXD: Receive serial data i.e. data received will be transmitted wirelessly by bluetooth module. 
6. State: Tells whether the module is connected or not.

The module also has a Red LED light attached which indicates connection status. Initially the led blinks continuously. Once connected, the blinking slows down to two seconds.

## 3. Arduino Color Recognition Sensor GY-31 TCS230 TCS3200

https://randomnerdtutorials.com/arduino-color-sensor-tcs230-tcs3200/


The TCS3200 is a color sensor which can detect colors based on their wavelengths. It consists of 4 white LED lights which light up the object in front of it. In the center is a sensor chip which detects the color of the object that is placed in front of it. 

### Working: 
The sensor consists of 64 photo diodes (semiconductors that convert light to current) with 4 different filters, with each filter having 16 photo diodes.
1.  Red Filter – sensitive to red wavelengths.
2.  Green Filter – sensitive to green wavelengths.
3.  Blue Filter – sensitive to blue wavelengths.
4. No Filter – does not have a specific color preference.

Depending on the photo diodes filter readings, we can detect the intensity of the color on an object. The photo diode reading is stored, and the sensor uses a current to frequency converter to convert it into a square wave with a frequency proportional to light intensity of chosen color. This frequency is then read by the Arduino (using the tilda circuit pin connectors).

## 4. DHT22 Digital Temp and Humidity Sensor AM2302 Module

https://www.electronicwings.com/sensors-modules/dht11

The DHT22 is a digital temperature and humidity sensor. It uses a humidity sensor and a thermistor to measure surrounding air and outputs a serial digital signal on data pin. The sensor can measure temperature ranging from -40 degrees to 80 degrees and humidity from 0% to 100% with an accuracy of +-1% for degrees and +-1% for humidity. 
Disadvantage: The sensor can only get new data once every 2 seconds, meaning every new reading will be up to 2 seconds old. 
Consists of 4 pins:
1. VCC: Power supply 3.3v to 5v
2. Data: output pin 
3. NC: not in use
4. GND: ground pin

### Working
The communication process is divided into 3 steps.

Step 1: The micro controller sends the start pulse. This is to signal the sensor to start operating.

Step 2: The sensor after receiving the start pulse sends a response signal to confirm that the start signal has been received. 

Step 3: The sensor calculates humidity, temperature as well as parity bit/checksum. All of these are calculated in bytes, which totals up to 5 byte segments(each segment is 8 bit long). The first two segments contain humidity value in decimal integer form. First 8 bits are integer values and next 8 bits are fractional parts. The next two segments are temperature values in decimal form. The last segment is checksum for first four segments. It is the direct addition of humidity and temperature value. We can confirm the temperature and humidity value using this checksum. After data is received, the sensor pin goes on cool down for 2 seconds before next start pulse is initiated.


## 5. NRF24L01 Wireless Transceiver Module
https://lastminuteengineers.com/nrf24l01-arduino-wireless-communication/

It is a wireless transceiver module used for communicating between the devices. It operates on 2.4GHz Ism band, making it suitable for short range wireless communication with limited data throughput.
It is utilized in applications which require short range, reliable and low cost wireless data transmission between devices and is used in devices such as sensors, remote controls and riot applications.
The module consists of a low level hardware protocol known as enhanced shock-burst which facilitates communication between devices, and an spi (serial peripheral interface) which allows for data exchange with the micro controller that is connected ot it. 

### Working
1. Data Packets: Consists of payload i.e. actual data and a header i.e. address and control information.
2. Channels: Module can operate on approx 126 cahnnels within the 2.4GHz range. All devices must be on the same channel to allow communication and data exchange.
3. Addressing: Each module has unique 5 byte address. This address can be used to distinguish between the modules and allow targeted communication. 
4. Modes: Has TX mode (transmits data) and RX mode (receives data).
5. Acknowledgment: When the packet is received, the receiver automatically sends an acknowledgment to the sender/transmitter ensuring the data integrity.
6. Power level and Range: Higher power level allow for a larger frequency range but consumes more energy. Range is still fairly limited and is affected by the surrounding.
7. Data Transmission Rate: Transmission rate varies from 250 kbps upto 1 or 2mbps.

## 6. GY-291 ADXL345 Sensor
It is a sensor board based on ADXL345 Accelerometer integrated circuit. It can be used for measuring acceleration in 3 axis, (x,y,z) and is used in mobile application for detecting motion sense. The sensor can detect any movement made and calculate it through its sensor chip. 
Uses
Motion Detection: Mobile applications and controllers often require actions which involve movement, therefore this sensor is used to detect the user movements and based on those movements, it sets orientation of the screen and allows for screen rotations, interactions with the environment as well as collision with elements.
Activity Monitoring: Actions such as running, walking, cycling etc can be monitored using these sensors. 
Gesture Recognition: The sensors can recognize gestures being made through detecting the change sin acceleration made by user and or application. 
Impact Detection: It can detect any impacts being made once the object comes into collision. 
Robots: Integrated into robots to allow the controlling of their movement as well as maintaining the stability of the movement being made. 



## 7. HC-SR602 Mini Motion Sensor Module SR602
It is a motion detection sensor that detects infrared radiation changes emitted by objects. The sensor triggers various actions when motion is detected and is primarily used in security systems. It connects to Arduino using pins, where the output pin provides a high or low signal to indicate motion detection
Working
It consists of a PIR sensor having 2 halves which, when exposed to infrared radiation, generate voltage. When motion is detected, the voltage is switched between the halves and it triggers the sensors.

## 8. BMP180 Barometric/Pressure Sensor
It is a sensor used to measure atmospheric pressure and temperature. Its sensor detects changes in the pressure and forwards the data obtained to the micro controller

It can communicate to the Arduino board using its I2C interface (allows for communication between 2 or more integrated circuits).

 ## 9. LoRa SX1278 RF Wireless Sensor
It is a wireless sensor module which allows for long range communication between modules. It is used in IoT applications as well as remote monitoring from a long distance.
It can be connected to Arduino using SPI pins(pulse width modulation through tilda pins) for data exchange.

## 10. DHT11 Humidity and Temp Sensor
It is a basic version of the DHT 22 Sensor which has same working as its peer but provides a lower range of accuracy and current flow. 

## 11. AHT20 High Precision Humidity and Temp Sensor
It is a higher precision and accuracy sensor which works similarly to DHT22 sensor, but also offers extra options regarding communication, accuracy, and higher current flow but also comes with higher power consumption. 
It can communicate with Arduino circuit using I2C or UART(asynchronous hence transmission rate is not fixed) protocols by connecting to the required Arduino pins.

## 12. MQ-5 Methane Gas Sensor
Its a sensor used for detecting the presence of methane gas in the air. It consists of detecting chemical resistance change when exposed to target gas.
Both analog and digital connections must be mad eto Arduino for this sensor to work properly.

## 13. MQ-2 Gas Sensor
Its a sensor used to detect presence of various gases present in the air such as hydrogen, propane etc. Similar to MQ-5 sensor, it detects the chemical resistance change when exposed to target gas to measure which gas Is present in the air. Similar to MQ-5 sensor, requires both analog and digital connection to arduino. 

## 14. HC-SR04 Ultrasonic Sensor
It is an ultrasonic sensor used for distance measuring. It emits ultrasonic pulses which extend to a wide area and bounce around on collision with objects and then return to the sensor. The sensor detects the time taken for the echo to return to calculate the distance the sensor is away from a certain object.
The sensor connects to Arduino through connection of two digital pins, with one being used as trigger which works as output to begin emitting the ultrasonic pulses and other being used for echo which acts as an input once it returns to the starting point.

## 15. LM393 IR Flame Sensor
It is a sensor used to detect presence of flame. The sensor has a detection range of 60 degrees and can also respond to flame/light with wavelength at the range of 760nm to 1100nm. The sensitivity with which it detects the light/flame can be adjusted using a precision potentio-meter connected to it. It has an operating voltage of 3.3v to 5v. 

## 16. 3Pin Voice Sound Detection Module
It is a small sensor module designed to detect sound or voice related signals. The module consists of a built in microphone, when sound is detected it converts the soundwaves to electrical signals. These signals are then processed by internal circuits and if a threshold is exceeded, the module will generate a digital output signal. Arduinos digital input pins can be connected to the sensor to read the output signals from the sensors and based on the output signals we can trigger various actions as response.