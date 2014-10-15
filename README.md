ece382_lab03
============

SPI - "I/O"

###Mega Prelab
See PDF in repository

###Timing Diagram
![alt text](https://raw.githubusercontent.com/byarbrough/ece382_lab03/master/timingDiagram.PNG "Timing Diagram")

###Writing Modes
![alt text](https://raw.githubusercontent.com/byarbrough/ece382_lab03/master/pixelColor.PNG "Writing Modes")

###Lab
This first table shows the various calls to #writeNokiaByte

Line	| R12	| R13 |	Purpose 
|--------|-------------|--------|---------
66 |	#NOKIA_DATA	| #0xE7	| Write the beam with hole in center
276 |	#NOKIA_CMD	| 0xB[row]	| Which row
288 |	#NOKIA_CMD	| 0x[col][col]	| write a blank col
294 |	#NOKIA_CMD	| 0x0[col]	| increment

The above outputs are sent out in four burst via the MOSI pin. Measurements from the Logic Analyzer are summarized in the following table:

Line | Command/ Data |	8-bit packet
|--------|-------------|--------
66	|Data	11100111
276	|Command	|10110001
288	|Command	|00010000
294	|Command	|00000001

