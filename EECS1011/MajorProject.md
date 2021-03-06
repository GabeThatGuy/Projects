## The EECS 1011 Major Project
By Gabriel Gonsalves --- 219 006 014  
Written in Markdown  
### Introduction
This device is indented to replace conventional faucets by allowing the faucet to detect when it is needed and when it is not.  

### Context  

Every year, hundreds of billions of liters of water are wasted across the country, and one contributor to this problem is that people often leave their faucets on for convenience, for example while doing dishes or while washing their hands.  

### Technical Requirements  
The system should be able to detect when the user’s hands are near, and then turn on the water pump. When the user’s hands are removed, the pump should turn off immediately.  

### Procedure  
To begin, I first disassembled my minor project, which consisted of the grove board, a humidity sensor and a water pump. I then adapted the code to receive input from the integrated light sensor on the grove board. Once the light sensor was providing values, I then added input from the potentiometer, to tune a threshold for different lighting conditions.  
### Test  
To test that the system worked, I first took the grove board with sensor and laptop to the bathroom and directed the rubber tube into the sink. I then turned on the lights in the bathroom and adjusted the potentiometer to set the background light level. Then, I proceeded to cover the board with my hand which then turned on the pump. Then after removing my hand, the pump turned off, meaning the project was a success. Or so I thought. I then moved it to another sink that I had in my house and found that the pump would always turn on, regardless of whether my hands were under the faucet or not. To mitigate this, I implemented some ``` disp() ``` statements into my code to display the voltage value coming from the sensor. I found that an adjustable threshold was required. To do this, I added the ability to read voltage from the integrated potentiometer. I then modified my infinite loop to compare the sensor voltage to the threshold voltage, and if the sensor voltage drops below the threshold, then the pump should turn on. This allowed me to adjust the circuit to accommodate for darker environments.  
### Contingency  
Initially, I wanted to create a synthesizer, which would accept a MIDI input via USB and then use the buzzer to create an appropriate tone. Unfortunately, the grove board does not have a USB input, nor did the beginner kit come with one, so I was not able to connect my MIDI keyboard into the grove board. Next time, I would attempt to find a suitable USB input device and purchase it in order to produce a synthesizer.  
### Additional Material  
As I mentioned in the introduction, thousands of liters of water are wasted each year and running sinks contribute extensively to this problem. If such a product as mine were to be industrialized and mass produced, and installed in peoples homes, it would significantly reduce water waste.  
### Conclusion  
With all of the aspects considered, such as environmental factors and feasibility of the project, I was content with my result and how it functions.  

### <span style="color:lime">The Code</span>
```matlab

if exist('a','var') == 1
%If arduino has been defined, do not define again, continue program as normal.
     a = a
else
%This will only run if the program is being run for the first time

%Notify the operator that MATLAB is programming the arduino for use.
    disp("Programming Arduino Board for Operation with MATLAB");

%Execute the command to program the arduino.
    a = arduino('/dev/cu.usbserial-0001','uno');
end

%This code contains two functions: readSensorVoltage and thresholdVoltage.
%They are contained in .m files. Note: readSensorVoltage is the function
%and readVoltage is the command included in MATLAB.

%Create an infinite loop.
while 1 > 0

    %Display the sensor voltage to the console

    toprint = strcat("Threshold Voltage: " + thresholdVoltage(a,'A0')+", Sensor Voltage: " + readSensorVoltage(a,'A2'));
    disp(toprint);
%Wait for 100ms before continuing.
    pause(0.1);

%Measure the threshold value from the potentiometer.
    thres = readSensorVoltage(a,'A0');
    
%Measure the light level from the sensor.     
    sig = readSensorVoltage(a,'A2');
    
%Compare the signal to the threshold. If the signal is lower, then turn the pump on. Otherwise, pump must be off. 
    if sig < thres
        writeDigitalPin(a,'D3',1);

    else
        writeDigitalPin(a,'D3',0);

    end


end
```



[Back to Top](/Projects/EECS1011/MajorProject#Introduction)  

[Back to List of Projects](/Projects)  
