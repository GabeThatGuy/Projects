## Gabe's Toolkit
This page gives details about the arduino toolkit. Modified for the EECS 1011 minor project. 

### What is it?
Gabe's toolkit is a toolkit that allows the grove arduino board to measure the value of a moisture sensor, and then enables it to determine if the soil inside a plant pot is wet or dry. Once determined, the board will decide if the soil needs to be watered or not. 

### The Code
Grab the code [here](/Projects/EECS1011/Arduino/gabestoolkit/Gabes_Toolkit_v1.1.ino), or find the inline version below.

```arduino

#include <Arduino.h>
#include <U8x8lib.h>

U8X8_SSD1306_128X64_NONAME_HW_I2C u8x8(U8X8_PIN_NONE);
int pumpPin = 7;
bool cleared = false;
int sensorPin = A3;
int buttonStatus = 0;
String note = "";
void setup() {
 
  
  // put your setup code here, to run once:


  pinMode(pumpPin, OUTPUT);
  pinMode(sensorPin, INPUT);
  u8x8.begin();
  u8x8.setFlipMode(1);

}


void loop() {
  // put your main code here, to run repeatedly:
  double sensorValue;
  sensorValue = analogRead(sensorPin);
  u8x8.setFont(u8x8_font_pxplusibmcgathin_r);
  u8x8.setCursor(0, 0);
  double voltage = sensorValue/212;
  String waterStatus;







  if (voltage > 3.0105) {
      
    waterStatus = "Watering!";
 String voltageconctrue = String(voltage) + " Volts";
 u8x8.setCursor(0,3);
 u8x8.print(voltageconctrue);
 u8x8.setCursor(0,6);
   u8x8.print("                ");
 u8x8.print(waterStatus);
    digitalWrite(pumpPin, HIGH);
  }else{
    waterStatus = "Not Watering!";
  
     String voltageconcfalse = String(voltage) + " Volts";
 u8x8.setCursor(0,3);
 u8x8.print(voltageconcfalse);
  u8x8.setCursor(0,6);

 u8x8.print(waterStatus);
 digitalWrite(pumpPin, LOW);
  }


/*String freqconc = String(frequency) + " Hz";
  String toDisplay = (brightnessPercentage + "%");
  u8x8.print(toDisplay);
 u8x8.setCursor(0,3);
 u8x8.print(freqconc);
 u8x8.setCursor(0,6);
 u8x8.setFont(u8x8_font_pxplusibmcgathin_r);
 u8x8.print("Gabe's Toolkit");
 u8x8.setCursor(0,7);
 u8x8.print("v1.1");

  */
  delay(10);

}
```