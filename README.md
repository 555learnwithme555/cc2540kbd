cc2540kbd
=========

[![World's smallest keyboard](http://img.youtube.com/vi/zbrPOiaEOTg/0.jpg)](https://www.youtube.com/watch?v=zbrPOiaEOTg)

This keyboard uses modified HIDEmuKbd sample from the CC2540 SDK.

Download precompiled firmware from the repository (HIDEmuKbd.hex), use [CCLoader](https://github.com/RedBearLab/CCLoader) and Arduino Nano to flash it.

Button sends WinKey keycode, you may modify the code to send any key or a key sequence of your choice.

The button is attached to CC2540 pins P0_1 and GND.

Hardware
========

* $2.65 CC2540 module (RF-BM-S02) from Aliexpress (11.2 x 15.1 x 1.74 mm, onboard USB support): https://www.aliexpress.com/item/MK00283-Bluetooth-4-BLE-from-the-module-serial-communication-direct-drive-mode-RF-BM-S02-CC2540/32658399946.html
* $1.83 Arduino Nano (to program the chip) https://www.aliexpress.com/item/Freeshipping-Nano-3-0-controller-compatible-for-arduino-nano-CH340-USB-driver-NO-CABLE/32341832857.html
* $0.92 Panasonic CR1216 lithium 3v battery (12.5 × 1.6 mm), 34 mAh
* $0.00 Cherry MX Blue keychain (20 x 11 mm) from http://www.geekkeys.com/keychain (actually $3.50 but I got it for free)

Software
========

* IAR Embedded Workbench for 8051 8.30.2: http://iar.com
* BLE-stack 1.4.0: http://www.ti.com/tool/BLE-STACK-ARCHIVE
* CCLoader: https://github.com/RedBearLab/CCLoader
* Hex to bin converter: http://hex2bin.sourceforge.net


Pinout
======

CC2540 pinout for CCLoader (Arduino Nano):

| Signal      | CC254x | CCLoader |
|:------------|:------:|:--------:|
| DEBUG_CLOCK | P2_1   | D6       |
| DEBUG_DATA  | P2_2   | D5       |
| RESET       | RES    | D4       |

CC2540 buttons and LEDs for Keyfob and Dongle development kits (defined in hal_board_cfg.h):

|Define      |Keyfob|Dongle|
|:-----------|:----:|:----:|
|HAL_KEY_SW_1| P0_0 | P1_2 |
|HAL_KEY_SW_2| P0_1 | P1_3 |
|HAL_LED_1   | P1_0 | P0_0 |
|HAL_LED_2   | P1_1 | P1_1 |

(P0_0 pin is not available on RF-BM-S02)

Build
=====
Copy provided files to the corresponding SDK folders:

* hidemukbd.c to BLE-CC254x-1.4.0\Projects\ble\HIDEmuKbd
* hidapp.c to BLE-CC254x-1.4.0\Projects\ble\HIDEmuKbdProjects\ble\HIDAdvRemoteDongle

Run IAR, open .eww, hit Make. You may also try precompiled firmware from the repository.


USB mode
========

CC2540 supports hardware USB (CC2541 doesn't), and can be used as USB-HID, USB Serial or USB Mass Storage Device.

**To run USB firmware and to detect USB on this module, U+ needs to be pulled to +3.3v via 1.5k resistor.**

See HIDAdvRemoteDongle sample for the USB peripheral device.

See HostTestApp sample from the CC2540 SDK for the USB Mass Storage device.

Press
=====

* https://hackaday.com/2017/05/20/the-tiniest-mechanical-keyboard-ever/

