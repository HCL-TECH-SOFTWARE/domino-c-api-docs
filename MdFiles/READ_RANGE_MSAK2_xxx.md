




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:"Tms Rmn";
 panose-1:2 2 6 3 4 5 5 2 3 4;}
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




 


**Symbolic Value : iCalendar**



**READ\_RANGE\_MSAK2\_xxx** **-** Bits that
control what properties about the calendar entries will be returned in addition
to those defined in dwReturnMask.


**----------------------------------------------------------------------------------------------------------**



**#include <calapi.h>**


 **Symbolic Values :**      READ\_RANGE\_MASK2\_HASATTACH          -  X-LOTUS-HASATTACH is
set to 1 if there are any file attachments for this entry.  

  

      READ\_RANGE\_MASK2\_UNID          -  X-LOTUS-UNID will always be set for
notices (as it is used as the identifier for a notice), but setting this flag
will also set X-LOTUS-UNID for calendar entries, where this will be set with
the UNID of the note that currently contains this instance (can be used to
construct a URL to open the instance in Notes, for instance).  

  




 




----------------------------------------------------------------------------------------------------------


 





