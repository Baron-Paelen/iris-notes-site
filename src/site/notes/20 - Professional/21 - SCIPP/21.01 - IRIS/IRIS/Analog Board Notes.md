---
{"dg-publish":true,"dg-path":"IRIS/Analog Board Notes.md","permalink":"/iris/analog-board-notes/","noteIcon":"","created":"2025-01-07T13:14:10.957-08:00","updated":"2025-04-11T14:48:30.148-07:00"}
---

![Pasted image 20250107131911.png](/img/user/00%20-%20System/09%20-%20External%20Attachments/Pasted%20image%2020250107131911.png)
## Diode
- reverse bias?
- input is "dark current"
	- from thermal excitation on the diode
	- constnat input
	- problem occurs if this baseline is too large bc you lose dynamic range on the op amps 0-3.3V range
## Op-Amp
- scintillation preamplifier?
- not a standard config (noninverting, differentiator, integrator)
- 0-3.3V range
## Capacitor
- capacitance controls sensitivity
	- 
- smaller capacitance = less sensitive
- larger capacitance = more sensitive (includes more of the baseline signal)
## Resistor
- resistance controls baseline
	- resistance proportional to  baseline
		- current * resistance
