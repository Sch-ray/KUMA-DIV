如果你只想要最终的固件，你可以在output目录下找到，它们的烧录地址是：

ESP32-DIV.ino.bootloader.bin -> 0x0

ESP32-DIV.ino.partitions.bin -> 0x8000

ESP32-DIV.ino.bin -> 0x10000

**1、安装编译环境**

首先你需要安装arduino。并安装以下依赖库：

ESP32 2.0.10

PCF8574_library-2.3.7

XPT2046_Touchscreen

rc-switch

RF24

arduinoFFT

ArduinoJson

IRremoteESP8266

Adafruit_PN532

Adafruit_BusIO

**2、文件替换**

使用Libraries目录下的platform.txt替换此目录下的同名称文件C:\Users\user\AppData\Local\Arduino15\packages\esp32\hardware\esp32\2.0.10-cn

手动安装Libraries目录下SmartRC-CC1101-Driver-Lib库

手动安装Libraries目录下TFT_eSPI库，并且需要使用Libraries目录下的User_Setup.h替换原有的同名称文件

如果顺利的话arduino现在可以成功编译这个项目

**3、引脚关系**

在项目中，首先需要关注的是config.h和TFT_eSPI安装目录下的User_Setup.h文件，他们需要和引脚保持对应：
| GPIO | Screen | Touch | TFCard | NRF24_1 | NRF24_2 | NRF24_3 | CC1101 | PN532 | BUZZER/WS2812 | GNSS | IR | IP5306 |
|------|--------|-------|--------|---------|---------|---------|--------|-------|---------------|------|----|--------|
| IO1  |        |       |        |         |         |         |        |       |               | RX   |    |        |
| IO2  |        |       |        |         |         |         | CS     |       |               |      |    |        |
| IO3  |        |       |        | CE      |         |         |        |       |               |      |    |        |
| IO4  |        |       |        |         |         |         |        | CS    |               |      |    |        |
| IO5  |        |       |        |         |         |         |        |       |               |      |    | SCL    |
| IO6  |        | IRQ   |        |         |         |         |        |       |               |      |    |        |
| IO7  |        | CS    |        |         |         |         |        |       |               |      |    |        |
| IO8  | D/C    |       |        |         |         |         |        |       |               |      |    |        |
| IO9  |        |       |        |         |         | CSN     |        |       |               |      |    |        |
| IO10 |        |       |        |         |         | CE      |        |       |               |      |    |        |
| IO11 |        |       |        |         | CSN     |         |        |       |               |      |    |        |
| IO12 |        |       |        |         | CE      |         |        |       |               |      |    |        |
| IO13 |        |       | MISO   | MISO    | MISO    | MISO    | MISO   | MISO  |               |      |    |        |
| IO14 |        |       | MOSI   | MOSI    | MOSI    | MOSI    | MOSI   | MOSI  |               |      |    |        |
| IO15 |        |       | CS     |         |         |         |        |       |               |      |    |        |
| IO16 | MISO   | MISO  |        |         |         |         |        |       |               |      |    |        |
| IO17 | MOSI   | MOSI  |        |         |         |         |        |       |               |      |    |        |
| IO18 | CS     |       |        |         |         |         |        |       |               |      |    |        |
| IO19 | SCK    | SCK   |        |         |         |         |        |       |               |      |    |        |
| IO20 |        |       |        | CSN     |         |         |        |       |               |      |    |        |
| IO21 |        |       | SCK    | SCK     | SCK     | SCK     | SCK    | SCK   |               |      |    |        |
| IO38 |        |       |        |         |         |         |        |       |               |      | TX |        |
| IO39 |        |       |        |         |         |         |        |       |               |      | RX |        |
| IO40 |        |       |        |         |         |         |        |       |               |      |    | SDA    |
| IO41 |        |       |        |         |         |         | IO0    |       |               |      |    |        |
| IO42 |        |       |        |         |         |         | IO2    |       |               |      |    |        |
| IO45 |        |       |        |         |         |         |        |       | EN/DATA       |      |    |        |
| IO46 | BackLight |    |        |         |         |         |        |       |               |      |    |        |