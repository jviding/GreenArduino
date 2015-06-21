# GreenArduino
Arduino Uno source code for Exactum Greenhouse project.
System for supervising environment: digital light, loudness, air humidity and temperature.

# Required Libraries
Wire <br>
TSL2561 <br>
dht

# Arduino's outputs
letter + value(s)

Example: s250
s is the identifier for loudness level. Arduino prints this every 0.5 seconds and it is the average of 4 separate loudness levels measured every 0.125 seconds.

Example: l125 260 75
l is the identifier for digital light values. The output consists of 3 separate values of which the first one stands for infrared light, second one for visible light and the third one for lux value.
Arduino prints this every 1 second and it is the average of 2 separate digital light levels measured every 0.5 seconds.

Example: t24.3
t is the identifier for air temperature. Arduino prints current temperature every 5 seconds.

Example: h23
h is the identifier for air humidity. Arduino prints current air humidity every 5 minutes.

# How it works
There is always a short delay after any single output to avoid data losses. While loudness is printed every 0.5 seconds, the other values are cycled so that they are each printed 0.25 seconds after a single loudness output. And between two loudness level outputs there can only be one other output.

So when the program starts running loudness is printed every 0.5 seconds starting from time 0.5 seconds after zero. Then digital light is printed every 1 second but starting from time 0.25 seconds after zero. Temperature is printed every 5 seconds starting from time 2.75 seconds after zero and eventually humidity every 5 minutes starting from time 4 minutes and 59.75 seconds after zero.

Notice that receiving the Digital Light value from the sensor can take almost up to 0.5 seconds!
