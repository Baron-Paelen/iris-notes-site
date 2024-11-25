---
{"dg-publish":true,"dg-path":"IRIS/Quick Start.md","permalink":"/iris/quick-start/","noteIcon":"","created":"2024-11-06T15:07:28.124-08:00","updated":"2024-11-25T14:40:16.714-08:00"}
---

## Setting Up Your Computer and M0/M4!

> [!info] Please Read!
> This guide should apply to everyone on a modern operating system (Windows, MacOS, most modern Linux distros).
> 
> Also, if I refer to a **script**, I am most likely referring to a *Python program* that will run on your computer/laptop. If I refer to a **sketch**, I am most likely referring to an Arduino program that will run on your MCU.

> [!tip] 
> Since I primarily use Linux, I will refer to *Terminal*, *cmd*, *PowerShell*, and whatever other analogous app as "terminal". For Windows users, if you see a command run as `sudo` in the guide below, you will have to run that same command (without including `sudo`) in an elevated/administrator *cmd* or *PowerShell* window. 

> [!faq]- Python is Unrecognized?
> Sometimes, trying to run the `python` command in terminal will throw an error saying it's an unrecognized command. Alternatives that usually work are:
> - `python`
> - `python3`
> - `py`
> - `py3`
> 
> If none of these work, chances are you do not have Python installed properly. 

> [!faq]- *Arduino IDE* says my device is unrecognized!
> Sometimes, our sketches "lock" the board in a way that's not always recoverable from our computer. A simple fix is to rapidly double click the little black *reset* button on your MCU. This will switch the MCU into *bootloader mode*, which conveniently halts the currently running sketch until a new one is uploaded. You can now try uploading your sketch again. 

### Requirements
- [Arduino IDE 2.3+](https://www.arduino.cc/en/software)
	- Legacy IDE (1.8.X) should work, but the GUI is different and you will have to find the analogous menus.
- [Python 3.10+](https://www.python.org/downloads/)
	- Ideally 3.12+
	- **Please double check your Python version by running `python --version` in terminal!**
- [A Local Copy of our Code](https://github.com/IRIS-Digital-Dosimeter/IRIS-Project/tree/serial_log_binary)
	- [Here is a link to the zip.](https://github.com/IRIS-Digital-Dosimeter/IRIS-Project/archive/refs/heads/serial_log_binary.zip) 
		- If you use this link, **make sure you extract the contents somewhere memorable before moving on.**
### Arduino IDE 
The bare IDE will not recognize our microcontrollers (MCUs) without some set up. 
1. Open *Arduino IDE*.
2. Go to *File*->*Preferences*
3. At the bottom, there will be an empty text box titled "Additional boards manager URLS". Paste in the following:
```
https://adafruit.github.io/arduino-board-index/package_adafruit_index.json
```
4. ...and click OK.
5. Next, in the left sidebar, open the *Boards Manager*.
6. Search for and install *Adafruit SAMD Boards*.
	- This will install the proper dependencies for our MCUs.

### Validating Your Setup!
Now we'll run a test program on your MCU to make sure the basics are set up properly. Make sure your MCU is plugged into your computer before proceeding.
1. In *Arduino IDE*, go to *File->Examples->Basics->Blink*. This should look something like this:
	- ![Pasted image 20241125142949.png|350](/img/user/00%20-%20System/09%20-%20External%20Attachments/Pasted%20image%2020241125142949.png)
	- This will open a new window with the *Blink* example sketch.
2. In *Arduino IDE*, you should see a dropdown menu in the top left that looks something like this:
	- ![Pasted image 20241125142646.png|300](/img/user/00%20-%20System/09%20-%20External%20Attachments/Pasted%20image%2020241125142646.png)
3. If your setup is correct, you should see an entry in there for every connected MCU. Select the one you'd like to test.


## Using the All-In-One Serial Importer Script!

### Dependencies

> [!info] Acknowledging VENVs
> I know this isn't quite the cleanest way of handling our dependencies. Once I've cleaned up the current GitHub repository more, I will work on updating all relevant scripts to work with Python's virtual environments.

#### Python
- **matplotlib**
	- In 