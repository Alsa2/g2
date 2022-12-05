![weather.png](HKWeatherStation.jpeg)

# Unit 2: A Distributed Weather Station for ISAK

## Criteria A: Planning

## Problem definition

Dr Ruben wants to cook methamphetamine in his room. This process requires fine and precise control over the temperature
and humidity of the surroundings. He started with a room thermometer but it is hard to manually collect data from the
thermometer, not to mention the temperature error from the room thermometer affects the predictions and adjustments for
the cooking process. He wants to be able to measure the temperature and humidity inside the room accurately so he can
make adjustments accordingly. He also wants the data to be easily comprehensible and accessible. If possible, he would
like to be able to make predictions for the following 12 hours so he can adjust beforehand as he is not present in the
room most of the time. As he is new to this topic, he wants to keep the cost as low as possible.

## Proposed Solution

Considering the client requirements an adequate solution includes a low cost sensing device for humidity and temperature
and a custom data script that process and analysis the samples acquired. For a low cost sensing device an adequate
alternative is the DHT11 sensor[^1] which is offered online for less than 5 USD and provides adequate precision and
range for the client requirements (Temperature Range: 0°C to 50°C, Humidity Range: 20% to 90%). Similar devices such as
the DHT22, AHT20 or the AM2301B [^2] have higher specifications, however the DHT11 uses a simple serial communication (
SPI) rather than more elaborated protocols such as the I2C used by the alternatives. For the range, precision and
accuracy required in this application the DHT11 provides the best compromise. Connecting the DHT11 sensor to a computer
requires a device that provides a Serial Port communication. A cheap and often used alternative for prototyping is the
Arduino UNO microcontroller [^3]. "Arduino is an open-source electronics platform based on easy-to-use hardware and
software"[^4]. In addition to the low cost of the Arduino (< 6USD), this device is programmable and expandable[^1].
Other
alternatives include different versions of the original Arduino but their size and price make them a less adequate
solution.

**Design statement**  We will design and make a poster for the client who is Dr Ruben. The poster will include the
system diagarma nad visual representation and model of humidity in the said room for 48 hours, and a prediction for the
subsequent 12 hours. It will present the ideal temperatures and humidity for cooking methamphetamine and health levels
for humans. This is achieved through with the software Python on a Raspberry Pi SBC(Single Board Computer) with four
DHT11 sensors. It will take approximately 1 month to complete and will be evaluated according to criterias A,B,C,D

[^1]: Industries, Adafruit. “DHT11 Basic Temperature-Humidity Sensor + Extras.” Adafruit Industries Blog
RSS, https://www.adafruit.com/product/386.
[^2]: Nelson, Carter. “Modern Replacements for DHT11 and dht22 Sensors.” Adafruit Learning
System, https://learn.adafruit.com/modern-replacements-for-dht11-dht22-sensors/what-are-better-alternatives.   
[^3]:“How to Connect dht11 Sensor with Arduino Uno.” Arduino Project
Hub, https://create.arduino.cc/projecthub/pibots555/how-to-connect-dht11-sensor-with-arduino-uno-f4d239.  
[^4]:Team, The Arduino. “What Is Arduino?: Arduino Documentation.” Arduino Documentation | Arduino
Documentation, https://docs.arduino.cc/learn/starting-guide/whats-arduino.

## Success Criteria

1. The solution provides a visual representation of the Humidity and Temperature values inside a dormitory (Local) and
   outside the house (Remote) for a period of minimum 48 hours.
1. ```[HL]``` The local variables will be measure using a set of 4 sensors around the dormitory.
2. The solution provides a mathematical modelling for the Humidity and Temperature levels for each Local and Remote
   locations. ```(SL: linear model)```, ```(HL: non-lineal model)```
3. The solution provides a comparative analysis for the Humidity and Temperature levels for each Local and Remote
   locations including mean, standad deviation, minimum, maximum, and median.
4. ```(SL)```The Local samples are stored in a csv file and ```(HL)``` posted to the remote server.
5. Create a prediction the subsequent 12 hours for both temperature and humidity.
6. A poster summarizing the visual representations, model and analysis is created. The poster includes a recommendation
   about healthy levels for Temperature and Humidity.

# Criteria B: Design

## System Diagram **SL**

![](sysdim_sl.png)

**Fig.1** shows the system diagram for the proposed solution (**SL**). The indoor variables will be measured using an
Arduino microprocessor and the sensor DHT11 conencted to the local computer (Laptop) located inside a room. The outdoor
variables will be requested to the remote server using a GET request to the API of the server
at ```192.168.6.147/readings```. The local values are stored in a CSV database locally.

![](sysdim_hl.png)

**Fig.2** shows the system diagram for the proposed solution (**HL**). The indoor variables will be measured using a
Raspberry PI and four DHT11 sensors located inside a room. Four sensors are used to determine more precisely the
physical values and include measurement uncertainty. The outdoor variables will be requested to the remote server using
a GET request to the API of the server at ```192.168.6.147/readings```. The local values are stored in a CSV database
locally and POST to the server using the API and TOKEN authentication. A laptop computer is used for remotely
controlling the local Rasberry Pi using a Dekptop sharing application (VNC Viewer). (Optional) Data from the local
raspberry is downloaded to the laptop for analysis and processing.

## Record of Tasks

| Task No | Planned Action            | Planned Outcome | Time estimate | Target completion date | Criterion |
|---------|---------------------------|-----------------|---------------|------------------------|-----------|
| 1       | Write the Problem context | 20min           | Nov 22        | Nov 22                 | A         |
| 2       | ALEX TELL ME WHAT YOU DID |                 |               |                        ||
| 3       |                           |                 |               |                        ||
| 4       |                           |                 |               |                        ||
| 5       |                           |                 |               |                        ||
| 6       |                           |                 |               |                        ||
| 7       |                           |                 |               |                        ||
| 8       |                           |                 |               |                        ||

## Test Plan

| Description | Type | Inputs | Outputs |
|-------------|------|--------|---------|
|             |      |        |         |
|             |      |        |         |
|             |      |        |         |
|             |      |        |         |

# Criteria C: Development

## Existing Tools

| Software/Development Tools | Coding Structure Tools | Libraries |
|----------------------------|------------------------|-----------|
| Python                     |                        |           |
| VS Code                    |                        |           |
| Terminal                   |                        |           |
| SSH                        |                        |           |

## List of techniques used

1. Functions
2. While Loops
3. Conditions
4. JSON formating
5. HTTP requests
6. Token Authentication
7. GPIO Interface
8. Graph Plotting

## Development

# Criteria D: Functionality

A 7 min video demonstrating the proposed solution with narration
