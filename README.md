# HelloDrum-2
HelloDrum-2 is an unofficial remix and continuation of the original HelloDrum DIY e-drums project by Ryo Kosaka.

![alt text](https://open-e-drums.com/images/oedrum1.jpg)
-# Image by Ryo Kosaka, taken from [here](https://open-e-drums.com/).

HelloDrum is a simple, open source, easy-to-build modular e-drum kit made to be as cheap and easy to build as possible that utilizes the MIDI protocol, making it compatible with virtually every music-making hardware or software out there. You can mix-n-match modules to create your own kit, or pick your favorite ones to expand your current e-kit!

**Current Version: 1A.0.0 - This is a work in progress, expect bugs and other issues.** 

## Available modules:
- 6 to 12 inch single-piezo pads
- 6 to 12 inch dual-piezo pads
- 8 inch kick pad *and* pedal
- Arduino MIDI/synth module

# Compatibility
*Note: Compatibility with listed software is untested. Some things might not work.*
- Works with ESP32, Teensy, Pico and Arduino-like boards like UNO and MEGA
- Runs on [MIDI Library](https://github.com/FortySevenEffects/arduino_midi_library), [BLE-MIDI Library](https://github.com/lathoub/Arduino-BLE-MIDI) and [USB-MIDI library](https://github.com/lathoub/Arduino-USBMIDI)

## Release History (OLD)
*Kept for archival purposes, HelloDrum-2 releases start from 1A.0.0*

* 0.7.7
   - Bug fix for ESP32
   - Add and Update sample codes about BLE-MIDI, USB-MIDI
* 0.7.6
   - Bug fix for LCD and buttons
   - Add and Update sample codes
* 0.7.5
   - Bug fix for ESP32
   - Bug fix for hihatControl()
   - Update sample codes
   - Add pullup mode to deal with floating pins (Beta)
   - Add debug mode
* 0.7.4
   - Add velocity curve function
   - FSR() and TCRT5000() integrated into hihatControl()
   - Update circuits
   - Add circuit images
   - Update sensing algorithm
   - Add sensing figure
   - Update sample code
   - Organize the source code
* 0.7.3
   - Update variables type
   - Add button function for LCD keypad shield
   - Add sample code "lcdShield.ino" for LCD keypad shield
* 0.7.2
   - Update sample code
   - Add Knob function
   - Add sample code for Teensy
* 0.7.1
   - Sensing with 16ch MUX(4067) is available
   - Update sample code
   - Organize folders and files
   - Add library.properties
   - Teensy3.2 has been tested
* 0.7.0
   - Improved sensing
   - Dual Piezo sensing available (Test)
   - ESP32 EEPROM available
   - Setting mode with I2C LCD or I2C OLED available
   - Add sample code
* 0.6.0
   - Sensing with MUX(4051) is available
   - Add BLE MIDI sample code with ESP32
   - Hihat Contorller with FSR is available
* 0.5.0
   - Setting mode available
   - Display function by LCD is available
   - Saving function of setting items by EEPROM is available
   - Improved sensing of TCRT 5000 hi-hat controller
* 0.1.0
   - Work in progress

## Todo
- rimGain
- retriggerCancel
- rotaryEncoder

## Original Author  
[Ryo Kosaka](https://ryokosaka.com)
[@tnctrekit](https://twitter.com/tnctrekit)

## License

HelloDrum and HelloDrum-2 are licensed under the [MIT License.](http://opensource.org/licenses/mit-license.php)
