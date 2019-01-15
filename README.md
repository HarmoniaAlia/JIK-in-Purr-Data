# JIK-in-Purr-Data
This is an early prototype of Just Intonation Keyboard, developed in Purr Data. 

To run this, please follow these steps: 
 1. Install Purr Data on your machine
 	https://github.com/agraef/purr-data/releases
 2. Unzip the files included in this prototype
 3. Run the patch jik.pd
 4. Click on "View" toggle to show/hide the patch, that contains the keyboard. Click on ON/OFF toggle to turn/off the sound. 

For illustration, the prototype includes two simple keyboards. The first compares the standard black-and-white keyboard in 12-tone temperament against the tones of the simple just intonation.  The orange ellipses show the tones of the C major in just intonation and the blue ones add the minor third, sixth and seventh of C minor.  The tones D, F and G in JI are very close (practically indistinguishable) to their equal-tempered counterparts. However, the major and minor thirds (E, Eb), sixths (A, Ab) and sevenths (B, Bb) are clearly distinct. The second keyboard keyboard shows the tones of the acoustic scale (8th through 16th partials). The orange ellipses are the tones of the 5-limit system and the brown ones add the natural augmented fourth (11/8), natural thirteenth (13/8) and natural seventh (7/4).  In both examples, I have chosen the pitch width so that the horizontal offset roughly corresponds to the "mistuning" against the 12-tone temperament. 

This prototype heavily relies on the Purr Data object [draw]. Our current most significant issue is that the [draw] object does not support Touchstart and Touchend events. It supports Mousedown and Mouseup (and some other mouse related) events. However, it seems that touching a touch display usually fires Mouseup events but not Mousedown events (in Windows).  For the time being we applied a workaround: our keyboard is operated by these Mouseup event - i.e. the sound is initiated when you raise you finger from the display (and not when you put it down). And the sound is played for a fixed time (1500ms).  From usability point of view, this is a critical issue and we are working hard to find a solution for this issue. (For this very same reason, multitouch is not working correctly.)

As regards the sound generator - we included just a simple 2-operator FM synthesizer in the prototype.  We will experiment with other options later.  

This prototype is quite flexible. You can easily expand and/or add new keyboard layouts. For that, open the patch "jik-keyboard-design".  There you can add/remove harmonies and define graphical representations of given harmonies. Harmonies are set of tones defined through their prime number factorizations represented as sequences consisting of primes and their exponents. For instance the tone 9/8 is represented as: "2 -3 1 3 2 1".  This corresponds to the prime number factorization:
    9/8 = 2^(-3/1) * 3^(2/1)
