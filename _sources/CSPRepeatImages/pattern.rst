..  Copyright (C)  Mark Guzdial, Barbara Ericson, Briana Morrison
    Permission is granted to copy, distribute and/or modify this document
    under the terms of the GNU Free Documentation License, Version 1.3 or
    any later version published by the Free Software Foundation; with
    Invariant Sections being Forward, Prefaces, and Contributor List,
    no Front-Cover Texts, and no Back-Cover Texts.  A copy of the license
    is included in the section entitled "GNU Free Documentation License".

.. |bigteachernote| image:: Figures/apple.jpg
    :width: 50px
    :align: top
    :alt: teacher note
    
.. |audiobutton| image:: Figures/start-audio-tour.png
    :height: 20px
    :align: top
    :alt: audio tour button

.. 	qnum::
	:start: 1
	:prefix: csp-11-3-

A Pattern for Image Processing
================================

As we have seen with turtles and words, there are some general patterns in the programs that we write.  With turtles, there was a polygon pattern (based on the Total Turtle Trip Theorem).  When working with words and numbers, we used the accumulator pattern.

The image processing pattern is shown in the program below.  This program changes the red to the original green, the green to the original blue, and the red to the original green.  But, mostly we are trying to describe a pattern that you can use to create many image effects.

.. raw:: html

   <img src="../_static/beach.jpg" id="beach.jpg">

.. activecode:: Image_Pattern
    :tour_1: "Important Lines Tour"; 2: timg4-line2; 5: timg4-line5; 8-9: timg4-line8-9; 12-14: timg4-line12-14; 17-19: timg4-line17-19; 22: timg4-line22; 25-26: timg4-line25-26;
    :nocodelens:

    # STEP 1: USE THE IMAGE LIBRARY 
    from image import *
    
    # STEP 2: PICK THE IMAGE
    img = Image("beach.jpg")

    # STEP 3: LOOP THROUGH THE PIXELS
    pixels = img.getPixels()
    for p in pixels:
        
    	# STEP 4: GET THE DATA
        r = p.getRed() 
        g = p.getGreen()
        b = p.getBlue()
            
        # STEP 5: MODIFY THE COLOR
        p.setRed(g)
        p.setGreen(b)
        p.setBlue(r)
            
        # STEP 6: UPDATE THE IMAGE
        img.updatePixel(p)
            
    # STEP 7: SHOW THE RESULT
    win = ImageWin(img.getWidth(),img.getHeight())
    img.draw(win)


Here are our six steps:

1. STEP 1: USE THE IMAGE LIBRARY.  We need to import the image library.
2. STEP 2: PICK THE IMAGE. We pick a particular image from our library by specifying it inside of the parentheses and double quotes.
3. STEP 3: LOOP THROUGH THE PIXELS This example gets *every* pixel in the image and loops through them all one at a time.
4. STEP 4: GET THE DATA.  You could *always* use the STEP 4 lines just as they are above, but you might be able to make it shorter if you wanted.  If you only needed red and were going to set the green and blue to zero, you don't have to get the green and blue.
5. STEP 5: MODIFY THE COLOR. This is the part that you will most often change.  Here's where you change the red, green, and/or blue.  You don't have to change all of them. 
6. STEP 6: UPDATE THE IMAGE.  This will update the image at the original pixel location to the new color.  
7. STEP 7: SHOW THE RESULT.  This will draw the changed image in a window.

**Mixed Up Code Problems**

.. note ::

   The problem below has a *Help Me* button, but it starts out disabled.  You must make at least 3 attempts to solve this problem before the button becomes enabled.  You can click on the *Help Me* button when it is enabled to make the problem easier.  

.. parsonsprob:: Image_Set_Red_Half_Blue
   :adaptive:

   The program below should set all the red values to half the blue values.  Drag the needed code blocks below from the left to the right in the correct order with the correct indention. There may be extra blocks that are not needed in a correct solution.  Click on the *Check Me* button to check your solution.
   -----
   from image import *
   =====
   import * #paired
   =====
   img = Image("beach.jpg")
   =====
   img = image("beach.jpg) #paired
   =====
   pixels = img.getPixels()
   for p in pixels:
   =====
   pixels = Image.getPixels()
   for p in pixels: #paired
   =====
       p.setRed(p.getBlue() * 0.5)
   =====
       img.updatePixel(p)
   =====
   win = ImageWin(img.getWidth(),img.getHeight())
   img.draw(win)
   
.. parsonsprob:: Image_Set_Green_Half_Red

   The program below should set all the green values to half the red values.  Drag the needed code blocks below from the left to the right in the correct order with the correct indention. There may be extra blocks that are not needed in a correct solution.  Click on the *Check Me* button to check your solution.
   -----
   from image import *
   =====
   img = Image("beach.jpg")
   =====
   pixels = img.getPixels()
   for p in pixels:
   =====
       p.setGreen(p.getRed() * 0.5)
   =====
       p.setGreen(p.getRed() - 0.5) #paired
   =====
       img.updatePixel(p)
   =====
       Image.updatePixel(p) #paired
   =====
   win = ImageWin(img.getWidth(),img.getHeight())
   img.draw(win)
   =====
   win = ImageWin(Img.getWidth(),img.getHeight())
   img.draw(win) #paired


