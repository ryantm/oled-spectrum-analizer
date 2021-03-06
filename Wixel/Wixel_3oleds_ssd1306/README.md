# Wixel_3oleds_ssd1306

Spectrum analyzer on Pololu Wixel (CC2511F32) with SPI and/or I2C OLED's SSD1306. The spectral width is 2403.47–2476.50 MHz with spacing in 286.4 kHz on two SPI displays. Displays available channels on I2C display. This scheme takes less then 10mA (on 5V).

## Equipment

1. Pololu Wixel ([fritzing part](../../fritzing-parts/OLED%200.96%20128x64%20I2C%20SSD1306.fzpz))
2. OLED 0.96" 128×64 I2C SSD1306 ([fritzing part](../../fritzing-parts/OLED%200.96%20128x64%20I2C%20SSD1306.fzpz))
3. Two OLED`s 0.96" 128×64 SPI SSD1306 ([fritzing part](../../fritzing-parts/OLED%200.96%20128x64%20SPI%20SSD1306.fzpz))

![Wixel_3oleds_ssd1306_photo](./pics/Wixel_3oleds_ssd1306_2.png)

## Wixel

Put the firmware on Wixel with parameters __show_grid__ (for grids) and __I2C_on__ (for additional I2C display). For example, to compile and download the firmware with [wixel-sdk](http://pololu.github.io/wixel-sdk/) on OS Windows:

```
C:\wixel-sdk>make load_Wixel_3oleds_ssd1306 S="show_grid=1 I2C_on=1"
```

More information about Wixel apps you can see on [official site](https://www.pololu.com/docs/0J46/10.b). This scanner based on [Spectrum Analyzer](https://github.com/pololu/wixel-sdk/tree/dev/david/analyzer/apps/spectrum_analyzer) written by David E. Grayson.

## Displays

Connect OLED's to Wixel as shown on the picture.

![Wixel_3oleds_ssd1306_scheme](./fritzing-scheme/Wixel_3oleds_ssd1306_bb.png)

## Connection Map

| Wixel    | SPI0 OLED     |
| -------- | ------------- |
| P0_1     | RES           |
| P0_2     | D/C           |
| P0_3     | DIN (SDA)     |
| P0_4     | CS            |
| P0_5     | CLK           |
| 3V3      | VCC           |
| GND      | GND           |

| Wixel    | SPI1 OLED     |
| -------- | ------------- |
| P1_3     | RES           |
| P1_4     | CS            |
| P1_5     | CLK           |
| P1_6     | DIN (SDA)     |
| P1_7     | D/C           |
| 3V3      | VCC           |
| GND      | GND           |

| Wixel    | I2C OLED      |
| -------- | ------------- |
| P1_0     | SCK           |
| P1_1     | SDA           |
| 3V3      | VCC           |
| GND      | GND           |

| Wixel    | switch        |
| -------- | ------------- |
| P0_0     | normally open |
| GND      | normally open |

| Wixel    | power supply  |
| -------- | ------------- |
| VIN      | 2.7–6.5V      |
| GND      | GND           |

## Implementation

Prototype is assembled in a clear acrylic case for Raspberry Pi, but can be built more compactly. Button with a red cap — switch on, and the second one — pause.

![Wixel_3oleds_ssd1306_photo](./pics/Wixel_3oleds_ssd1306_4.png)

The left screen displays ZigBee and Wi-Fi channels (not all channels fall within the available range). The higher the channel in the histogram, the more free.

![Wixel_3oleds_photo](./pics/Wixel_3oleds_ssd1306_3.png)
