---
{"dg-publish":true,"permalink":"/20-professional/21-scipp/21-01-iris/iris/m4-board/","noteIcon":"","created":"2024-08-22T23:34:23.994-07:00","updated":"2024-09-03T13:02:43.297-07:00"}
---

Currently, the IRIS board is transitioning from the [Adafruit M0 Adalogger](https://www.adafruit.com/product/2796) to the [M4 Express](https://www.adafruit.com/product/3857) and [Datalogging FeatherWing](https://www.adafruit.com/product/2922). The transition is being made because the SD write latency with the M0 was simply too high. Hopefully, the M4's SAMD51 chip will be more than enough for our purposes.

The current approach is as follows:
```mermaid
graph LR
    Buffer[Buffer] --> CPU
    CPU[CPU] --> SD[SD Card]
    CPU --> DMAC[DMAC]
    DMAC --> CPU
    DMAC --> ADC[ADC]
    DMAC --> Buffer
    ADC --> DMAC
    A0[A0 - A4] --> ADC 


```
In order to allow concurrent data collection and SD writing, we use the M4's SAMD51's [[20 - Professional/21 - SCIPP/21.01 - IRIS/IRIS/DMA Controller\|DMA controller]] to control the 2 onboard [[20 - Professional/21 - SCIPP/21.01 - IRIS/IRIS/ADC\|ADCs]]. The DMAC is configured to collect samples from the ADCs into a buffer. Once the buffer is filled, the CPU begins the process of writing the buffer's contents into the SD card. The DMAC then starts new conversions on the ADCs.

The 2 ADCs each alternate between 2 pins, interleaving the results into the buffer (A0, A1, A2, A3, A1, A2, etc).

> [!warning]
> Looks like Adafruit's SPI library overwrites register level DMAC programming according to [[20 - Professional/21 - SCIPP/21.01 - IRIS/IRIS/Resources#^99fd12\|MartinL]], which may be causing the issues that came up with using the M0's SD card with DMA. 