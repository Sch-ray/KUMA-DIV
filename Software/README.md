If you just need bin files to download, you can found that in ./output.

And this is download address you need to know:

ESP32-DIV.ino.bootloader.bin -> 0x0

ESP32-DIV.ino.partitions.bin -> 0x8000

ESP32-DIV.ino.bin -> 0x10000

****1. Setting Up the Build Environment****

First, you need to install Arduino IDE. Then install the following dependencies:

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

****2. Replacing Files****

Replace the `platform.txt` file in the following directory with the `platform.txt` provided in the `Libraries` directory:

`C:\Users\user\AppData\Local\Arduino15\packages\esp32\hardware\esp32\2.0.10-cn`

Manually install the `SmartRC-CC1101-Driver-Lib` library from the `Libraries` directory.

Manually install the `TFT_eSPI` library from the `Libraries` directory. You also need to replace its original `User_Setup.h` file with the `User_Setup.h` provided in the `Libraries` directory.

If everything is configured correctly, Arduino should now be able to compile the project successfully.

****3. GPIO Pin Mapping****

The two files you need to pay particular attention to are `config.h` in the project and `User_Setup.h` in the TFT_eSPI installation directory. Make sure that the pin definitions in these files match the following GPIO mapping:

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