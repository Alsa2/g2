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

Considering the client's requirements an adequate solution includes a low cost sensing device for humidity and temperature
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
DHT11 sensors. It will take approximately 1 month to complete and will be evaluated according to criterias below

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
| 1       | Write the Problem context | To have a clear and defined goal to achieve and what the client wants | 20min    | Nov 22                 | A         |
| 2       | Create BOM(Bill of Materials) | Compile a list of necessary materials | 10min | Nov 22 |A|
| 3       | Finalize Design Statement | To have a clear outline of final goal of our project and tasks that need to completed | 30min | Nov 22 |A|
| 4       | Collect materials and sign Scope of Work document | To aquire all materials in order to achieve project goal and sign document stating materials taken and intended use. | 20min | Nov 29 |A|
| 5       | Install necessary software for development | Prepare computer and Raspberry Pi for coding | 45min | Nov 29 |A|
| 6       | Test run of equipment | To make sure sensors and raspberry pi are working properly. | 60min | Nov 29 |B|
| 7       | Construction of Weather Station | To have the physical part of the weather station prepared | 30min | Nov 29 |B|
| 8       | Create MVP (Minimum Viable Product) | To test most base level function of the product and validate the concept before moving on to coding for the final product | 60min | Nov 29 |C|
| 9 | Register user to server and obtain access token | To create user with secure username and password in order to have elevated access to the server. Access token allows to post to server | 5min | Dec 01 |C|
| 10 | Create code to obtain temperature and humidity data from DHT11s | To be able to collect data from the sensors at an interval of 5 minutes | 30min | Dec 01 |C|
| 11 | Create code that saves collected data to JSON file and sends to server | To be able to have a local backup of data and then post the results to the server | 30min | Dec 01 |C|
| 12 | Create code to obtain data from the school sensors | To be able to get data from the school sensor for future graphing and comparisons | 15min | Dec 01 |C|
| 13 | Create Bash Program to keep alive program | To have a failsafe when the main program fails to stop the loop | 15min | Dec 01 |C|
| 14 | Replace malfunctioning sensors | To replace broken down sensors with functioning one | 5min | Dec 06 |C|
| 15 | Test run of replaced parts | To make sure that the replaced parts are functioning correctly | 15min | Dec 06 |B|
| 16 | Run program for 48 hours in order to collect needed data in R2-10B | Obtain temperature and humidity data from R2-10B for 48 hours at 5 minute intervals | 48 hours | Dec 06-07 |C|
| 17 | Create flow diagrams for interesting aspects of the code | To clearly display the functions used in the program | 2 hours | Dec 08 |B|
| 18 | Create code for graphing the room data and school data | To be able to visualize the collected data and prepare for linear fit functions | 45min | Dec 11 |C|
| 19 | Include more data into graph | To plot smoothed data with additional stats like min, max, mean and error bars and also polynomial functions for predictions | 1 hour | Dec 11 |C|
| 20 | Video Outline | To organize what needs to be included in the video | 1 hour | Dec 11 |D|
| 21 | Create Scientific Poster | To present the background information, methodologies, materials, results, analysis and conclusion for the client in a clear and easy to understand way | 2 hour | Dec 11 |D|
| 22 | Beautify README file | To make README file more easily-understandable | 3 hour | Dec 11 |B|
| 23 | Create Video Demonstration | To make the video in order to demonstrate the solution and the findings | 4 hour |  |D|

# 	Test Plan

| Description | Type | Inputs | Outputs |
|-------------|------|--------|---------|
|             |      |        |         |
|             |      |        |         |
|             |      |        |         |
|             |      |        |         |

# Criteria C: Development

## Existing Tools

| Software/Development Tools | Coding Structure Tools | Libraries    |
| -------------------------- | ---------------------- | ------------ |
| Python                     | For Loops              | datetime     |
| VS Code                    | API requests           | requests     |
| Terminal                   | Functions              | Sys          |
| SSH                        | JSON file              | Adafruit_DHT |
|                            |                        | Json         |
|                            |                        | Time         |

## List of techniques used

1. Functions
2. While Loops
3. Conditions
4. JSON formating
5. HTTP requests
6. Token Authentication
7. GPIO Interface
8. Graph Plotting

## Computational Thinking

In the initial code and the Minimum Viable Product, we utilized a while loop in order for the code to keep running every five minutes at specific intervals. This solution proved to be inefficient becuase the task of getting readings every 5 minutes for 48 hours straight, which would mean leaving the SSH connection on for the whole time, basically disabling the connected laptop for 2 days which is not feasible. To solve this problem, we first tried using a crontab task that would automatically run the code every 5 minutes. However, due to multiple system issues with our raspberry pi, we attempted multiple times to still no avail. Instead, we resorted to using the while loop and a bash program to make sure the program was running in the background.

#### Bash Program

```bash
source "/home/dev/Program/venv/bin/activate" && python3 "/home/dev/Program/main-loop.py" > /home/dev/Program/logger.log
output=$(ps -aux | grep python3)
while true
do
if [[ $output != *"main-loop.py"* ]]
then
source "/home/dev/Program/venv/bin/activate" && python3 "/home/dev/Program/main-loop.py" > /home/dev/Program/logger.log
fi
sleep 5
done
```

This program checks if the main program is running, and automatically restarts the program if it's not.

## Development

Below are the key parts of code development for the project

####  Libraries

To reduce the lines of repetitve, we included frequently used functions into a library to improve code readbility and simplicity.

```py
import requests

def get_readings(id:int, url:str="http://192.168.6.142/readings") -> list:
    req = requests.get(url)
    data = req.json()
    readings = data["readings"][0]
    temp = []
    for sample in readings:
        if sample["sensor_id"] == id:
            temp.append(sample["value"])
    return temp

def smoothing(data:list, size_window:int=12) -> list:
    x = []
    y = []
    for i in range(0, len(data), size_window):
        #print(data[i:i+size_window])
        segment_mean = sum(data[i:i+size_window])/size_window
        y.append(segment_mean)
        x.append(i)
    return x, y
```

#### MVP - Minimum Viable Product

In order to validate our concept of creation, we created a MVP as a prototype to make sure our concept is reliable and achievable. The MVP code gets data from each sensor and displays the output in the terminal. Please refer to the code below:



Link to MVP video: 

```py
#!/usr/bin/python3
import sys
import Adafruit_DHT
autocheck = ""
autocheck = str(autocheck)

while True:
    if autocheck != "":
        Adafruit_DHT.read_retry(11, autocheck)
    else:
        tocheck = input("Enter sensor number to check: ")
        if Adafruit_DHT.read_retry(11, tocheck) is not None:
            print("Sensor pin "+tocheck+" is connected")
            h, t = Adafruit_DHT.read_retry(11, tocheck)
            print("Temperature: "+str(t)+"C")
            print("Humidity: "+str(h)+"%")
        else:
            print("Sensor pin "+tocheck+" not working")
```

#### Registration of sensors on server

Authenticating and creating 8 sensors. Code is as follows:

```py
import requests

user = {"username": "xxx", 'password':'xxxxxxxx'}
#for security reasons, the username and passwords are masked!

req = requests.post('http://192.168.6.142/login', json=user)
access_token = req.json()["access_token"]
print(access_token)
access_token = req.json()["access_token"]
auth = {"Authorization": f"Bearer {access_token}"}

for i in range(8):
    if i < 5:
        new_sensor ={ "type": "Temperature","location": "R2-10B", "name": ("sensor_alex_bern"+str(i)),"unit":"C" }
    else:
        new_sensor ={ "type": "Humidity","location": "R2-10B", "name": ("sensor_alex_bern"+str(i)),"unit":"%" }
    r = requests.post('http://192.168.6.142/sensor/new', json=new_sensor, headers=auth)
    print(r.json())
```



#### Complex Graphs - 4+1 Data representation

After much consideration, we decided to present the data in a way where the average of the four sensors can be viewed. The code plots the graphs of smoothed data from all 4 sensors and a larger graph of the average temperature datas. Refer to the code and graphs below:



Temperature:

```py
from matplotlib import pyplot as plt
from matplotlib.gridspec import GridSpec
import library as u2l
sensors = [28,29,30,31]
values = []
for s in sensors:
    x,smoothed = u2l.smoothing(u2l.get_readings(s)[:])
    values.append(smoothed)

mean_per_hour = []
for i in range(len(values[0])):
    data = [values[n][i] for n in range(4)]
    mean_per_hour.append(sum(data)/len(sensors))
print("Ready to plot")

fig=plt.figure(figsize=(12,12))
gs = GridSpec(4, 4, figure=fig)
ax = fig.add_subplot(gs[:,0:3])
plt.title("Average of sensors")
plt.plot(x, mean_per_hour)
plt.ylim([20,28])
plt.xlabel("Samples per hour")
plt.ylabel("Celsius")

for row, my_color in [(0,"#e63946"),(1,"#a8dadc"),(2,"#457b9d"),(3,"#1d3557")]:
    ax = fig.add_subplot(gs[row,3])
    plt.plot(x, values[row], color=my_color)
    plt.title("Sensor "+str(sensors[row]))

plt.show()
```

![](Assets/temp4in1.png)

Humidity:

```py
IM WAITING ALEX * 2
```

*Graph

#### Polynomial fit w/ predictions

This piece code aims to plot the smoothed average data from the sensors and plot a polynomial fit for said data. This also predicts dta for 12 hours after the collected data ends. Refer to the code and graphs below:

Temperature:

```py
IM WAITING ALEX * 3
```

*Graph

Humidity:

```py
IM WAITING ALEX * 4
```

*Graph

#### Errors bars and other statistical data

This part of the code calculates the maximum, minimum and mean values of the plotted data, and indicates the vales with a line which is parallel to the x-axis. This code also includes plots error bars to indicate the standard deviation of the data. Refer to code and graphs below

Temperature:

```py
IM WAITING ALEX * 5
```

*Graph

Humidity:

```py
IM WAITING ALEX * 6
```

*Graph

# Criteria D: Functionality

## Scientific Poster

*Insert Poster

## Demonstration Video

A 7 min video demonstrating the proposed solution with narration
