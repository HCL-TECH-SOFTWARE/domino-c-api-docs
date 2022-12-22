




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




**Initial Release 5.0.2**



**Symbolic Value : Signal Handler**



**PROGRESS\_SIGNAL\_xxx** **-** Definitions
specific to progress signal handler.


**----------------------------------------------------------------------------------------------------------**



**#include <ossignal.h>**


 **Symbolic Values :**      PROGRESS\_SIGNAL\_BEGIN           -  Signal the beginning of
the progress signal.  

  

      PROGRESS\_SIGNAL\_END   -  Signal the end of the progress signal.  

  

      PROGRESS\_SIGNAL\_SETRANGE   -  Specify the range of the progress
indicator.  

  

      PROGRESS\_SIGNAL\_SETTEXT      -  Specify the text to be displayed.  

  

      PROGRESS\_SIGNAL\_SETPOS        -  New progress position.  

  

      PROGRESS\_SIGNAL\_DELTAPOS   -  Change of progress position.  

  

      PROGRESS\_SIGNAL\_SETBYTERANGE      -  Total bytes.  

  

      PROGRESS\_SIGNAL\_SETBYTEPOS           -  Bytes done.  

  




 **See Also :**


**[OSSIGPROGRESSPROC](OSSIGPROGRESSPROC.md)**



----------------------------------------------------------------------------------------------------------


 





