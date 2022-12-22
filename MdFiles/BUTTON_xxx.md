




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Helv;
 panose-1:2 11 6 4 2 2 2 3 2 4;}
@font-face
 {font-family:"Cambria Math";
 panose-1:2 4 5 3 5 4 6 3 2 4;}
 /\* Style Definitions \*/
 p.MsoNormal, li.MsoNormal, div.MsoNormal
 {margin-top:0cm;
 margin-right:0cm;
 margin-bottom:8.0pt;
 margin-left:0cm;
 line-height:107%;
 font-size:11.0pt;
 font-family:"Calibri",sans-serif;}
.MsoChpDefault
 {font-size:11.0pt;}
.MsoPapDefault
 {margin-bottom:8.0pt;
 line-height:107%;}
 /\* Page Definitions \*/
 @page WordSection1
 {size:612.0pt 792.0pt;
 margin:72.0pt 72.0pt 72.0pt 72.0pt;}
div.WordSection1
 {page:WordSection1;}
-->




**Initial Release 5.0.3**



**Symbolic Value : Constants; Rich
Text**



**BUTTON\_xxx** **-** CDBUTTON -
Flags


**----------------------------------------------------------------------------------------------------------**



**#include <editods.h>**


 **Symbolic Values :**      BUTTON\_UNUSED   -  Button is unused.  

  

      BUTTON\_RUNFLAG\_SCRIPT          -  Script is attached to this button.  

  

      BUTTON\_RUNFLAG\_NOWRAP        -  Works with width flags
BUTTON\_RUNFLAG\_FIXED, BUTTON\_FUNFLAG\_MINIMUM, BUTTON\_RUNFLAG\_CONTENT and
BUTTON\_RUNFLAG\_WIDTHMASK.. If text doesn't "fit" in the specified
width, determines if text should be wrapped (and button made taller) or not.  

  

      BUTTON\_ODS\_MASK          -  Determines which of the flag bits are written
to disk as opposed to just being used while the button "is running"
to record the current state of the button (e.g., if the button has been pressed
and is currently executing script bits). In other words, it's the AND mask for
all the bits that are going to be written to disk.                        

  

      BUTTON\_RUNFLAG\_RTL    -  Button uses right-to-left reading order.  

  

      BUTTON\_RUNFLAG\_FIXED             -  Button has a fixed width of specified
size.  

  

      BUTTON\_RUNFLAG\_MINIMUM       -  Button has a fixed width of specified
size UNLESS text is too wide to fit in which case it's made wider to
accommodate the text.  

  

      BUTTON\_RUNFLAG\_CONTENT      -  Button is as wide as is necessary to
accommodate the text.  

  

      BUTTON\_RUNFLAG\_PROPORTIONAL        -  Button width is a fixed number of
characters.  

  

      BUTTON\_FOCUS\_ON          -  Button has focus.  

  

      BUTTON\_RUNFLAG\_WIDTH\_MASK            -  AND mask to see if
BUTTON\_RUNFLAG\_FIXED, BUTTON\_RUNFLAG\_MINIMUM, BUTTON\_RUNFLAG\_CONTENT,
BUTTON\_RUNFLAG\_NOWRAP and BUTTON\_RUNFLAG\_PROPORTIONAL flags are set. If none of
these flags are set, the button is "MAXIMUM" size.
"Maximum" means the button is as wide as is necessary to accommodate
the text up-to the specified maximum width. If the text doesn't fit at the
maximum width, it's wrapped onto a second (third, fourth, ...) line and the
button is made correspondingly taller. Minimum allowed value is
"2.00".  

  

      BUTTON\_EDGE\_ROUNDED            -  Button edges are rounded.  

  

      BUTTON\_EDGE\_SQUARE   -  Button edges are square.  

  




**Description :**



Possible
values for the Flags member of the CDBUTTON structure.


 **See Also :**


**[CDBUTTON](CDBUTTON.md)**



----------------------------------------------------------------------------------------------------------


 





