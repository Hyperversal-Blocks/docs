# LoRa SX 1278 Module

Lo(Long) Ra(Range) is a new technology that bypasses WiFi to allow sensors to transmit information to devices at longer ranges. It is an alternative to GSM, where one LoRa module is connected to the transmitter and receiver's side. Data can be sent to distances up to 100 KM, however there is a data limit capped at 50 kbps. Hence, it is unsuitable for media files such as videos but is perfect for transmitting data from sensors (infrared, humidity, etc). A benefit of this technology is its low power usage (10-20 mA) but in exchange for this, the bandwidth is limited. Typically, the sensors are connected to microcontrollers with attached batteries. One LoRa module is connected to this apparatus, while another one is connected at a distance (for example, the user's home). Depending on the use case, data is transmitted in intervals (e.g every 5 or 10 seconds, etc). Using simple batteries, this setup can be powered with a single LiPo battery for over a year. 

## Implementation
LoRa uses a modulation technique called CSS (Chirp Spread Spectrum) that transforms data (with a maximum rate of 50 Kbps), compared to LTE which has a data rate of 10 Mbps. Its link budget is capped at 154 dBM compared to LTE's 130 dBM. As it has higher link budget, LoRa provides better range than LTE. The tradeoff for achieving a higher link budget is a lower bandwidth and data rate. 


### Comparison of wireless techniques


|          | Bandwidth | Range|
|----------|----------|----------|
|Bluetooth | Low | Low |
| WiFi | High | Low |
| Mobile Networks | High | High |
| **LoRa** | **Low** | **High** |
 

LoRa allows a tradeoff between range and bandwidth. The LoRa Alliance is a set of companies that support and use LoRa. LoRaWAN is a Wide Area Network that uses LoRa Gateways to connect LoRa with 4G LTE internet. Sensors connect to LoRa Gateway nodes that transmit sensor data to the internet. Commercially, companies use these gateways to communicate with their products on a large scale via the Things network, which is part of the LoRa Alliance.

A LoRa transmitter module may consist of a battery, an SX-1278 LoRa module and an ESP 8266 Gateway (that operates on a bandwidth of 433 Mhz) to send out packets via the internet.


### Difference between LoRa SX-1278 and ESP 8266 Gateway


|   LoRa SX-1278       | ESP 8266 Gateway|
|----------|----------|
| Radio Frequency (RF) transceiver module designed to enable long-range communication using the LoRa modulation technique | Advanced device that bridges LoRaWAN nodes and the Internet |
|Simple node or endpoint in a LoRaWAN network| Wi-Fi module with built-in microcontroller capabilities| 
| Operates on physical layer (Layer 1) of communication (encoding and decoding data for transmission and reception)| Operates primarily at the Data Link Layer (Layer 2) and the Network Layer (Layer 3)  | 
|  Limited processing capabilities and low power consumption | Requires more power and processing resources as it handles the data processing and networking aspects of the communication  |


## Setup 1: Point to point communication between LoRa SX-1278 Modules


### Step 1: Transmitting Node 

A LoRa SX1278 node prepares the data it wants to send.
Parameters such as frequency, spreading factor, bandwidth, and coding rate are configured to decide the range and data rate of the communication.

### Step 2: Modulation and encoding
The node encodes the data using the selected modulation parameters and starts transmitting the LoRa-modulated signal.

### Step 3: Receiving Node
 Another LoRa node, within the range of the transmitting node, listens for LoRa signals on the configured frequency and parameters.
The receiving node's LoRa module continuously scans for LoRa signals, trying to detect incoming transmissions.
If the receiving node's LoRa module detects a LoRa signal with a sufficient signal-to-noise ratio, it starts demodulating the signal.

### Step 4: Demodulation and Decoding

The receiving node's LoRa module demodulates the received LoRa signal, trying to recover the original encoded data.
Depending on the modulation parameters used, the receiver might can its sensitivity to capture weaker signals for longer communication ranges.



### Step 5: Error Handling

LoRa modulation is robust against noise and interference, which makes it suitable for long-range communication. In case there are errors in the received data, error correction mechanisms can be used to recover the original message.

### Advantages
* Simple, no need for advanced network infrastructure
* Low latency due to no intermediaries
* Reduced communication overheads
* Localized 
* Range is predictable

### Disadvantages
* Low range
* Not scalable
* No redundancy 
* Isolated nodes
* No internet communication
* No data aggregation or remote management


## Setup 2: Communication Between LoRa Modules using ESP8266 Gateway



### Step 1: Packet Forwarding

When ESP8266 gateway receives LoRa packets from the nodes, it processes the packets at the Data Link Layer (Layer 2). Data is encapsulated in appropriate formats and prepares it for transmission over the network.
The gateway forwards the packets to the LoRaWAN network server over an internet connection (e.g., Wi-Fi or Ethernet).

### Step 2: LoRaWAN Network Server

The LoRaWAN network server manages the entire LoRaWAN network. It receives data from multiple gateways, extracts and decodes the data from the packets, and performs tasks like deduplication, security checks, and device authentication.
The server then routes the data to the appropriate application server based on device identifiers and other metadata.

### Step 3: Application Server

The application server receives the data from the LoRaWAN network server which hosts the application logic and is responsible for processing the data and performs actions based on the received information.
For example, if the LoRa nodes are humidity sensors, the application server might process the humidity readings and trigger alerts or visualizations based on predefined thresholds.


### Step 4: Reverse Communication

The communication process also works in reverse. The application server can send commands or data to specific LoRa nodes via the LoRaWAN network server and the ESP8266 gateways.
The ESP8266 gateway receives these commands, encapsulates them into LoRa packets, and transmits them over the airwaves to the appropriate LoRa nodes.

### Advantages
* Internet connectivity
* Extended range 
* Scalable
* Remote Management
* Data collection/aggregation
* Service integration

### Disadvantages
* High complexity
* Higher power consumption 
* Cost
* Latency issues
* Dependent on internet 
* Internet associated security concerns

## Setup 3: Communication Between LoRa Modules and Gateways (LoRaWAN)


### Step 1: Transmitting Node

Similar to point-to-point communication, a LoRa node prepares the data it wants to send.
Instead of directly transmitting to another LoRa node, the node sends the data using the LoRaWAN protocol. This is known as "Direct-to-Application" or "OTAA" (Over-the-Air Activation) communication.

### Step 2: LoRaWAN Gateway

A LoRaWAN gateway is equipped with a **LoRa concentrator** that can receive LoRa signals on multiple channels and spreading factors.
The gateway listens for LoRaWAN packets transmitted by LoRa nodes within its coverage area.
When the gateway receives a LoRaWAN packet, it forwards it to the LoRaWAN network server via an internet connection.

### Step 3: LoRaWAN Network Server and Application Server

The LoRaWAN network server processes incoming data from multiple gateways.
It decodes the LoRaWAN packet, performs security checks, and routes the data to the appropriate application server based on device identifiers.
The application server processes the data and performs appropriate actions based on the application's requirements.

### Advantages
* Highest range and coverage 
* Low power usage 
* Most scalable
* Optimized and dedicated infrastructure 
* Security (end-to-end encryption, authenticity)
* Standardized for integration

### Disadvantages
* High cost 
* Complex (networks of gateways, servers, nodes, etc)
* Dependent on gateways
* Unusable in remote areas 
* Bandwidth due to use of gateways/network servers 
