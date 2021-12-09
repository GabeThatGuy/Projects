---
layout: default
title: Major Project Code
---

### Gabe's Code for the EECS 1011 Major Project  
Please ensure your system is set to Light Mode so that this page displays correctly.


{% highlight matlab %}
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
%and readVoltage is the command including in MATLAB.

%Create an infinite loop.
while 1 > 0

%Display the sensor voltage to the console



toprint = strcat("Threshold Voltage: " + thresholdVoltage(a,'A0')+", Sensor Voltage: " + readSensorVoltage(a,'A2'));
disp(toprint);
pause(0.1);


thres = readSensorVoltage(a,'A0');
sig = readSensorVoltage(a,'A2');

if sig < thres
    writeDigitalPin(a,'D3',1);

else
    writeDigitalPin(a,'D3',0);

end


end
{% endhighlight %}
