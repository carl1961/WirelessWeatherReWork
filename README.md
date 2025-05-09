Currently a Work in progress as I learn how to put this wireless weather to working
search for best prices, I do not get any money from links 

3D printed parts at Thingiverse https://www.thingiverse.com/thing:7009551

I Recommend using  Windfahne-Mast-8.3mm-M4x5x5-Inserts-Window.stl
It has a hole to tighten the bearing bolts. this allows you to use the set screws on bearing to lock bearing to  aluminum tubing.

Update 4-17-2025

*Moved reed switch on Mast to under side

*Added M4 inserts to mast part

*Added BME280-KY-001-DS1820-Screw-Sensor-Mount

![WIN_20250417_22_18_38_Pro](https://github.com/user-attachments/assets/ab961027-37ef-4d3c-8c6a-7c3a29b9824d)

 
*Improved Anemometer-Lagerschale-8mm , Now 11mm and with alignment pin holes 

Anemometer-Lagerschale_1-8mm-V2 has 3 pin holes (same size as for pin used in rain gauge) 

![20250417_025332](https://github.com/user-attachments/assets/b66cc247-2fab-4f85-9bf9-8f3755b43710)



Added file for 195mmx125mm solar module  https://www.amazon.com/Bettomshin-Polycrystalline-Module-Charger-195x125mm%EF%BC%8C1Pcs/dp/B09R9WVTVC?th=1       (110x125 solar module still ordered (hard to find)

![WIN_20250417_22_48_20_Pro](https://github.com/user-attachments/assets/0c3e621c-0a65-4289-949e-4bee5c7844d6)

BME280 Module mount     https://www.amazon.com/JESSINIE-Atmospheric-Pressure-GY-BME280-3-3-Temperature/dp/B0D8L1GPBV

![WIN_20250417_22_17_39_Pro](https://github.com/user-attachments/assets/5eeb67db-a757-43ef-bf22-19b1150bba65)


Reed switch mounts for wind direction , Rain and wind speed

I had to use 3mm magnet on Wind direction for reed switches to work correct. 5mm magnet triggered the surrounding reed switches.

![20250413_174429](https://github.com/user-attachments/assets/0db31994-8120-44d5-a954-1e466abe8da0)

![WIN_20250417_22_20_46_Pro](https://github.com/user-attachments/assets/87bea12d-7e6e-495e-9deb-4d56407920d1)

![20250413_174439](https://github.com/user-attachments/assets/d6833709-c1c1-4031-b1f0-e6c3e5f09c96)

![20250416_141832](https://github.com/user-attachments/assets/872646c2-acb0-412b-8e80-e64291deb5c9)

![WIN_20250417_22_21_43_Pro](https://github.com/user-attachments/assets/be9066b3-7d85-4d74-905a-b1ff2304dedf)

![WIN_20250417_22_30_28_Pro](https://github.com/user-attachments/assets/d9c49ad1-3a51-4696-8acf-9e7064db8948)

![WIN_20250417_22_32_07_Pro](https://github.com/user-attachments/assets/fe88e1de-ad2d-4fb0-9c43-f9f45b5f3412)


## NOTE: I had to use solder paste to get solder to stick to reed switch leads.



Fusion files
[https://github.com/carl1961/WirelessWeatherReWork](https://www.thingiverse.com/thing:7009551)

PaddyCube link to fusion view   https://myweb11242.autodesk360.com/g/shares/SH919a0QTf3c32634dcfa4fd707aa5c92a6e

Windfahne-Magnet-Mount-New.stl  Stronger that original  also I did as test with TPU  (flexible filament)
Windfahne-Mast-8.3mm.stl has reed mount built in.

Anemometer-Lagerschale_1-8mm.stl   is 4mm thick arms  both parts glued together become 8mm. Original was 4mm
Raingauge-mount-plate-Reed-Switch-Mount.stl is only needed if you already printed   Raingauge-mount-plate , you have to apply effort to get holes drilled for screws and reed switch leads. I use 2 M3 x 6mm screws



## Description
Build your own Wireless Weather station. This station includes:
- Temperature
- Humidity
- Pressure
- Rain Level
- Wind Speed
- Wind direction
- Battery monitor

There are three versions available: 
- One uses ESP8622 module and some ATTINYs
- one uses ESP32 and only one ATTINY for wind direction 
- one uses an Arduino Mini together with ATTINY24 for wind direction inside weather station and publish messages by 433 Mhz.

Code and schematics for any solution can be found in corresponding subfolders of folder 'code'
https://myweb11242.autodesk360.com/g/shares/SH919a0QTf3c32634dcfa4fd707aa5c92a6e
## Operation mode
### ESP8266
Wind speed and rain gets detected by pin change interrupt of ATTINYs. 
There is a power hungry device called WEMOS D1 mini pro, which deep sleeps most time. 
Every few minutes, it wakes up, collect data from other devices by I2C, send everything to your MQTT broker and sleeps again.

### ESP32
Wind speed and rain gets count by ULP co-processor of ESP32 module. Every few minutes, ESP32 wakes from deep sleep, read count values from ULP, power up I2C devices and sends everything to your MQTT broker. Then it sleeps again.

### Arduino Pro Mini
Because ESP devices are pretty power hungry, I wanted to build something more power saving. Therefore, a Arduino Pro Mini is used inside the weather station. Most time it sleeps and count wind and rain by interrupts. Every x minutes, it wakes up, power up I2C devices (BME280 and ATTINY24 for wind direction), reads values and send them using cheap 433MHz module. You find a working example based on ESP8266 module acting as a bridge between 433 Mhz and MQTT, so it receives data over 433MHz and publish them like before using MQTT. 

## Project site
You find all 3D printed parts at Thingiverse (https://www.thingiverse.com/thing:7009551) 
https://www.thingiverse.com/thing:3718078

A video is here https://youtu.be/xa0Dt5vs0kM

## BOM
This package includes software for the following components
### ESP8266
- 2x ATTINY85 (wind speed, rain and battery level)
- 1x ATTINY24 (wind direction)
- Wemos D1 Mini pro (or other ESP8266 device)
- 1x BME280
- Please find a complete BOM in BOM.txt file

Moreover you need some device to program ATTINYs. This can be done with any Arduino device. There are plenty of tutorials out there.

### ESP32
- 1x ATTINY24 (wind direction, see folder Wireless Weather)
- ESP32 (DOIT DevKit V1 with 30 GPIOs)
- 1x BME280

For further information, please see readme file in ESP32 folder

### Arduino Pro Mini
- 1x Arduino Pro Mini
- 1x ATTINY24 (wind direction)
- 1x BME280
- 1x 433MHz receiver, transmitter pair

You also need some code and device to receive the data and process them further. This can be done with any device, like Arduino, ESP8266, ESP32, Raspberry PI and so on. To get a complete working example, I added some code for ESP8266 (WEMOS D1 mini pro) which
acts as some kind of bridge between 433MHz and MQTT, meaning it receives the data send by Arduino Pro Mini and send them using MQTT protocol.

## Required Software
For ATTINYs, you need this package <br>
https://github.com/SpenceKonde/ATTinyCore <br>
https://github.com/rambo/TinyWire <br>

For ESP8266 and ESP32, I used this one <br>
https://arduino.esp8266.com/stable/package_esp8266com_index.json <br>
https://github.com/knolleary/pubsubclient <br>
https://github.com/adafruit/Adafruit_BME280_Library <br>

When using Arduino Pro mini, you need these packages as well <br>
https://github.com/rocketscream/Low-Power <br>
https://github.com/PaulStoffregen/RadioHead <br>
https://github.com/adafruit/Adafruit_BME280_Library <br>

## License
<br>Copyright (c) 2019 by Patrick Weber  

Private-use only! (you need to ask for a commercial-use)
 

You should have received a copy of the GNU General Public License
along with this program.  If not, see <http://www.gnu.org/licenses/>.

Private-use only! (you need to ask for a commercial-use)

kicad-5.1.2_2
https://downloads.kicad.org/kicad/windows/explore/stable
https://myweb11242.autodesk360.com/g/shares/SH919a0QTf3c32634dcfa4fd707aa5c92a6e
