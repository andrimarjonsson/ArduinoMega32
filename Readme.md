#ArduinoMega32
This small project was born out of the fact that I needed to test some Arduino program but all I had on stock was a bunch of ATMega32s. Hopefully this will be useful to someone else faced with the same issue. 

##Installtion instructions

* Append the contents of `boards.txt` to `<arduinopath>/hardware/arduino/avr/boards.txt`
* Copy the `mega32` folder into `<arduinopath>/hardware/arduino/avr/variants`
* Open `<arduinopath>/hardware/arduino/avr/cores/arduino/HardwareSerial.cpp` and replace the following

```cpp
//set the data bits, parity, and stop bits
#if defined(__AVR_ATmega8__)
  config |= 0x80; // select UCSRC register (shared with UBRRH)
#endif
```
with

```cpp
//set the data bits, parity, and stop bits
#if defined(__AVR_ATmega8__) || defined(__AVR_ATmega32__)
  config |= 0x80; // select UCSRC register (shared with UBRRH)
#endif
``` 

##Note
My test setup does not have a bootloader so in order to upload you sketch you have to go to `Sketch -> Upload Using Programmer` after having set your programmer first. To do that go to `Tools -> Programmer: <someprogname>` and select yours from the list in the submenu.