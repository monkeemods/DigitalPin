# Digital Pin
This is a simple library to handle digital pin. Built for ArduinoPico and supports ESP32.

## Feature
- Input debounce
- Auto adjust HIGH or LOW based in INPUT_PULLUP or INPUT_PULLDOWN

Example
```
DigitalPin pinA;
DigitalPin pinB;
void setup(){
    //setup pin 10 as INPUT_PULLUP
    pinA.setup(10, INPUT_PULLUP);
    
    //setup pin 11 as OUTPUT and set it to HIGH
    pinB.setupAndWrite(11, OUTPUT, 1);
    
    //enable debounce for pin 10, the pin have to be same state for at least 50ms
    //note this will requires continue read() or isInputChanged() call to work 
    pinA.enableInputDebounce(50);
}

void loop(){
    //normal reading, this will save the lastState to the current state
    bool isPin1High = pin1.read();
    
    //check if input pin changed, this will also update the lastState
    bool isChanged = pin1.isInputChanged();
 
}
```

