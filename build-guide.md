# THIS IS A DEPRECATED GUIDE. A NEW GUIDE WITH A DIRECT ENGLISH TRANSLATION AND UPDATED INSTRUCTIONS IS IN THE MAKING, PLEASE WAIT FOR A FUTURE RELEASE.

## How to Use
- **Install**  
Use Arduino's Library Manager to install the library. Search for “hellodrum ”.  
If you use MIDI, also install the [MIDI Library](https://github.com/FortySevenEffects/arduino_midi_library). Or [BLE-MIDI Library](https://github.com/lathoub/Arduino-BLE-MIDI) or [USB-MIDI library](https://github.com/lathoub/Arduino-USBMIDI).

<img src="https://open-e-drums.com/images/ide.png" width="800px">

- **Initialize EEPROM**  
If you want to use EEPROM to store the settings, you will need to initialize the EEPROM.
Please write the sample code, example > EEPROM > InitializeEEPROM > InitializeEEPROM.ino, to your Arduino. Once it's written, the initialization is complete.  

- **Coding**
   ```cpp
    #include <hellodrum.h>
    #include <MIDI.h>
    MIDI_CREATE_DEFAULT_INSTANCE();

    //Please name your piezo.
    //The piezo named snare is connected to the A0 pin
    HelloDrum snare(0);

    //Setting
    byte SNARE[6] = {
      80, //sensitivity 
      10, //threshold
      20, //scantime
      20, //masktime
      38, //note
      1   //curve type
    }; 

    void setup()
    {
        MIDI.begin(10);
        snare.setCurve(SNARE[5]); //Set velocity curve 
    }

    void loop()
    {
        //Sensing
        snare.singlePiezo(SNARE[0], SNARE[1], SNARE[2], SNARE[3]); //(sensitivity, threshold, scantime, masktime)

        //Sending MIDI signals
        if (snare.hit == true) {
            MIDI.sendNoteOn(SNARE[4], snare.velocity, 10);  //(note, velocity, channel)
            MIDI.sendNoteOff(SNARE[4], 0, 10);
        }
    }
    ```

- **Coding (MUX)**:
   ```cpp
    #include <hellodrum.h>
    #include <MIDI.h>
    MIDI_CREATE_DEFAULT_INSTANCE();

    //Define MUX Pins
    HelloDrumMUX_4051 mux(2,3,4,0);//D2, D3, D4, A0
    
    //Please name your piezo.
    //The piezo named snare is connected to MUX 0 pin
    HelloDrum snare(0);

    //Setting
    byte SNARE[6] = {
      80,  //sensitivity
      10,  //threshold
      20,  //scantime
      20,  //masktime
      38,  //note
      1    //curve type
    }; 

    void setup()
    {
        MIDI.begin(10);
        snare.setCurve(SNARE[5]); //Set velocity curve 
    }

    void loop()
    {
        //scanning all pin of mux
        mux.scan();

        //Sensing
        snare.singlePiezoMUX(SNARE[0], SNARE[1], SNARE[2], SNARE[3]); //(sensitivity, threshold, scantime, masktime)

        //Sending MIDI signals
        if (snare.hit == true) {
            MIDI.sendNoteOn(SNARE[4], snare.velocity, 10);  //(note, velocity, channel)
            MIDI.sendNoteOff(SNARE[4], 0, 10);
        }
    }
    ```  

    [Check instruction.md](https://github.com/RyoKosaka/HelloDrum-arduino-Library/blob/master/docs/instruction.md) for more info on coding.

## Using Arduino MIDI Library

[FortySevenEffects Arduino MIDI Library](https://github.com/FortySevenEffects/arduino_midi_library)   
There are three ways to communicate with a PC using MIDI with an arduino.

1. Rewrite arduino's USB chip (UNO,MEGA only)
    - https://www.arduino.cc/en/Hacking/DFUProgramming8U2
    - http://morecatlab.akiba.coocan.jp/lab/index.php/aruino/midi-firmware-for-arduino-uno-moco/?lang=en
2. Using Hairless MIDI (Easiest way)
    - https://projectgus.github.io/hairless-midiserial/
    - https://open-e-drums.tumblr.com/post/171304647319/using-hairless-midi
3. Using a MIDI terminal and a MIDI-USB cable
    - https://www.arduino.cc/en/Tutorial/Midi
    - https://open-e-drums.tumblr.com/post/171168448524/using-midi-socket-with-arduino


```cpp
#include <hellodrum.h>
#include <MIDI.h>
MIDI_CREATE_DEFAULT_INSTANCE();

//...
```

## Using USB-MIDI Library

[lathoub Arduino-USBMIDI](https://github.com/lathoub/Arduino-USBMIDI)   
If you are using atmega32u4 (Arduino Leonardo, Arduino Micro, Arduino Pro Micro...), you can use USB-MIDI library. No additional software is needed, the 32u4 is recognized as a MIDI device.

```cpp
#include <hellodrum.h>
#include <USB-MIDI.h>
USBMIDI_CREATE_DEFAULT_INSTANCE();

//...
```

## Using BLE-MIDI Library with ESP32

[lathoub Arduino-BLE-MIDI](https://github.com/lathoub/Arduino-BLE-MIDI)   
It is very easy to use BLE-MIDI with ESP32.  
You can find a device named "BLE-MIDI".

```cpp
#include <hellodrum.h>
#include <BLEMIDI_Transport.h>
#include <hardware/BLEMIDI_ESP32.h>
BLEMIDI_CREATE_DEFAULT_INSTANCE();

//...
```
Please check the KORG's documentation for instructions on how to connect.  
[KORG Bluetooth MIDI Connection Guide](https://cdn.korg.com/us/support/download/files/7c456d3daad3b027197b3fda1f87dce7.pdf?response-content-disposition=inline%3Bfilename%3DBluetooth_MIDI_SettingG_E1.pdf&response-content-type=application%2Fpdf%3B) 

## Sensing Method and Setting Values
**Be sure to check here first if it is not working properly.**  
[Check sensing.md](https://github.com/RyoKosaka/HelloDrum-arduino-Library/blob/master/docs/sensing.md) for sensing methods.  
[Check setting.md](https://github.com/RyoKosaka/HelloDrum-arduino-Library/blob/master/docs/setting.md) for setting values. 

## Circuit
[Check circuit.md](https://github.com/RyoKosaka/HelloDrum-arduino-Library/blob/master/docs/circuit.md) for how to connect the pad and the board.

## Pads
[The STL data of pads from 6 inches to 12 inches, hi-hat controllers](https://www.thingiverse.com/RyoKosaka/designs)
