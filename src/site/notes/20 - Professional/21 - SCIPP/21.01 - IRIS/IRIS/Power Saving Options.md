---
{"dg-publish":true,"permalink":"/20-professional/21-scipp/21-01-iris/iris/power-saving-options/","tags":["Stub"]}
---

Currently, we do not have any considerations for battery longevity as the board is plugged in directly via USB. However, we can use a combination of the following in the future:
- SAMD51's sleep mode(s)
- ADC's window monitor to trigger an event/interrupt/wake-up when readings go above a specified threshold
- SAMD51's internal comparators
	- may be faster than window monitor
> [!note] 
> Testing must be done to ensure that the SAMD51's wakeup time is < 100us to ensure we can begin collecting data as soon as possible
>