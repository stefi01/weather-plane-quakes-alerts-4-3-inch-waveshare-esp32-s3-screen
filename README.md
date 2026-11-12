# weather, night sky, plane tracker

Version 1.1 for the Freenove FNK0115B, the 4.3 inch ESP32-S3 board. The glass is 480 by 272. The sketch still lays the pages out at 800 by 480, and the sketch scales that onto this glass.

It shows the weather for one US city or ZIP, planes overhead, earthquakes, and the night sky. Wi-Fi is 2.4 GHz. Power is USB-C.

The manual is weather-night-sky-plane-tracker-manual.pdf.

## What is here

firmware/weather/weather.ino, the picture headers, and the touch files XPT2046_Touchscreen.h and XPT2046_Touchscreen.cpp.

libraries/GFX_Library_for_Arduino and libraries/TJpg_Decoder are the two libraries the sketch includes from the Arduino libraries folder. libraries/XPT2046_Touchscreen-master is the touch library this compile also used. The copy beside the ino is the one this sketch builds.

ota/version.txt and ota/weather.bin are the update files. weather.bin is the app bin from the compile that ran on 12 Nov 2026. It is 1266672 bytes.

## Updates

CHECK reads

https://raw.githubusercontent.com/stefi01/weather-plane-quakes-alerts-4-3-inch-waveshare-esp32-s3-screen/main/ota/version.txt

INSTALL reads

https://raw.githubusercontent.com/stefi01/weather-plane-quakes-alerts-4-3-inch-waveshare-esp32-s3-screen/main/ota/weather.bin

version.txt is 1.1. The partition 16M Flash (3MB APP/9.9MB FATFS) has the second slot INSTALL uses. The first copy still goes on over USB.

## Board

ESP32S3 Dev Module, OPI PSRAM, Flash Size 16MB, USB CDC On Boot Enabled, Partition Scheme 16M Flash (3MB APP/9.9MB FATFS). The port is the CH340 COM. There is no UART switch. Leave BOOT. The cable stays in the USB socket.

The compile that made this bin used QIO, 80 MHz, CPU 240, upload speed 921600, and partition app3M_fat9M_16MB. PSRAM XIP stays off. The full list is firmware/weather/settings to change.txt.

Copy libraries/GFX_Library_for_Arduino and libraries/TJpg_Decoder into the Arduino libraries folder. Do not compile a second GFX from inside the sketch folder. The touch .h and .cpp next to weather.ino are the ones this sketch builds. If another XPT2046_Touchscreen library is already installed, move that folder aside before compiling, or the touch code is built twice.

## Loading the bin

ota/weather.bin is the app bin. Flash tool 3.9.3, Develop, UART, ChipType ESP32-S3, SPI SPEED 80MHz, SPI MODE DIO, DoNotChgBin ticked, LockSettings unticked, BAUD 115200, address 0x10000, Erase unticked. Use the CH340 COM. Leave BOOT.
