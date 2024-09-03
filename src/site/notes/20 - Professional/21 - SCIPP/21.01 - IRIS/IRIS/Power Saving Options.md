---
{"dg-publish":true,"dg-path":"IRIS/Power Saving Options.md","permalink":"/iris/power-saving-options/","tags":["Stub"],"noteIcon":"","created":"2024-08-24T11:29:11.277-07:00","updated":"2024-09-03T13:02:48.805-07:00"}
---

Currently, we do not have any considerations for battery longevity as the board is plugged in directly via USB. However, we can use a combination of the following in the future:
- SAMD51's sleep mode(s)
- ADC's window monitor to trigger an event/interrupt/wake-up when readings go above a specified threshold
- SAMD51's internal comparators
	- may be faster than window monitor
> [!note] 
> Testing must be done to ensure that the SAMD51's wakeup time is < 100us to ensure we can begin collecting data as soon as possible
>