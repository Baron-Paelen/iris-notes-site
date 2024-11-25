---
{"dg-publish":true,"dg-path":"IRIS/Quick Start.md","permalink":"/iris/quick-start/","noteIcon":"","created":"2024-11-06T15:07:28.124-08:00","updated":"2024-11-25T13:52:10.773-08:00"}
---

## Setting Up Your Computer and M0/M4!
This guide should apply to everyone on a modern operating system (Windows, MacOS, most modern Linux distros). 
### Requirements
- [Arduino IDE 2.3+](https://www.arduino.cc/en/software)
	- Legacy IDE (1.8.X) should work, but the GUI is different and you will have to find the analogous menus.
- [Python 3.10+](https://www.python.org/downloads/)
	- Ideally 3.12+
### Arduino IDE 
The bare IDE will not recognize our microcontrollers (MCUs) without some set up. 
1. Open *Arduino IDE*.
2. Go to *File*->*Preferences*
3. At the bottom, there will be an empty text box titled "Additional boards manager URLS". Paste in the following:
```
https://adafruit.github.io/arduino-board-index/package_adafruit_index.json
```
4. and click OK.
5. Next, in the left sidebar, open the *Boards Manager*.
6. Search for and install *Adafruit SAMD *