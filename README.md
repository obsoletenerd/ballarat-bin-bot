# Ballarat Bin Bot

An ESP32 project that displays Ballarat bin collection times for your specific address.

Pulls rubbish collection data from the Ballarat.vic.gov.au API to tell you when to put which bins out!

Uses an ESP32 with SSD1306 display connected via I2C (I use Wemos Lolin32 OLED, but any should work)

Requires the following libraries (all available via Arduino IDE Library Manager):

- Adafruit_GFX (https://learn.adafruit.com/adafruit-gfx-graphics-library/overview)
- Adafruit_SSD1306 (https://github.com/adafruit/Adafruit_SSD1306)
- WiFiManager (https://github.com/tzapu/WiFiManager)
- ArduinoJson (https://arduinojson.org/)

## Installation

- Open the sketch in the Arduino IDE.
- Select the correct ESP32 board that you're using (WEMOS LOLIN32 if you're using the same as mine).
- Edit line 15 to put your address where the placeholder address currently is. You need to replace any spaces with %20, same as the example in the code. It's best to put your full address with suburb such as "123 High Street Sebastapol" as even though the council website will match partial addresses, this program only works if it gets a single exact match to your address.
- Edit the OLED specs on lines 19 and 20 if you're not using the same one as me.
- Compile and copy the sketch onto your ESP32.
- When the ESP32 restarts, WiFiManager will automatically create an access point called "BinBotAP". You can connect to this from your phone or computer using the passphrase "BinBotBestBot!".
- A captive portal will pop up asking you for your WiFi details. Enter them, and the ESP32 will reboot again and this time connect to your WiFi.
- ... that's it, give it a few seconds and you'll start seeing your bin dates.

If you get an "Address Error!" it means it couldn't find an exact match for your address. Go back and edit Line 15 again and re-compile/copy/etc. You won't need to do the WiFiManager stuff again.

## Notes

This is a very early version with the ultimate goal of having a 3D printed enclosure with LEDs showing which bins are next due out, as well as a second version of this project that uses an e-paper display and battery so it doesn't need constant USB power.
