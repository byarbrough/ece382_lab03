ece382_lab03
============

SPI - "I/O"

###Mega Prelab
I turned in the prelab as a hard copy. [See the PDF](https://github.com/byarbrough/ece382_lab03/blob/master/megaPrelab.pdf?raw=true)

####Timing Diagram
This diagram was part of the prelab not in the PDF. It shows what I anticipated for the clock, CS, and MOSI signals.
![alt text](https://raw.githubusercontent.com/byarbrough/ece382_lab03/master/timingDiagram.PNG "Timing Diagram")

###Writing Modes
This task is somewhat unrelated.... it demonstrates my ability to XOR.
![alt text](https://raw.githubusercontent.com/byarbrough/ece382_lab03/master/pixelColor.PNG "Writing Modes")

###Lab
The lab had two tables which it wanted completed.

This first table shows the various calls to #writeNokiaByte

Line	| R12	| R13 |	Purpose 
|--------|-------------|--------|---------
66 |	#NOKIA_DATA	| #0xE7	| Write the beam with hole in center
276 |	#NOKIA_CMD	| 0xB[row]	| Which row
288 |	#NOKIA_CMD	| 0x[col][col]	| write a blank col
294 |	#NOKIA_CMD	| 0x0[col]	| increment

The above outputs are sent out in four burst via the MOSI pin. When the S3 button was pressed on the LCD shield, this waveform was generated.
![alt text](https://raw.githubusercontent.com/byarbrough/ece382_lab03/master/4blurps.png "4 MOSI signals")
As you can see, four calls to #writeNokiaByte are made - each one preceded with a Data/Command bit and then 8 bits of information.

Here is a zoomed in look at the second write.
![alt text](https://raw.githubusercontent.com/byarbrough/ece382_lab03/master/2ndBlurp.png "Second write")

Each of these writes is summarized below.

Line | Command/ Data |	8-bit packet
|--------|-------------|--------
66	|Data	    |11100111
276	|Command	|10110001
288	|Command	|00010000
294	|Command	|00000001

This was the first button push, which fits because both the row and column values are at one.

Finally, below is the screenshot of the reset.
![alt text](https://raw.githubusercontent.com/byarbrough/ece382_lab03/master/rstDelay.png "Reset Delay")

This shows that there is a 1.156 microsecond delay between pressing reset and MOSI changing.

###A Functionality
I thought I would include a video just for fun, but unfortunately, GitHub doesn't support files that large. You can still [download it](https://github.com/byarbrough/ece382_lab03/blob/master/demo.mp4?raw=true); I think it is worth watching.


###Documentation
C2C Jaasper Arnenberg told me to look at the setAdress table for the first table in the lab.
C2C Ian Goodbody helped a little with understanding the logic analyzer.

