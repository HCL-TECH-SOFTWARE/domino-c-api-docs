




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




**Initial Release 9.0**



**Symbolic Value : iCalendar**



**CAL\_NOTEOPEN\_xxx** **-** Flags that
control behavior of the calendar APIs - Used when opening a note handle for
calendar data.


**----------------------------------------------------------------------------------------------------------**



**#include <calapi.h>**


 **Symbolic Values :**      CAL\_NOTEOPEN\_HANDLE\_NOSPLIT          -  Used when getting a
handle via CalOpenNoteHandle (Handy for read-only cases).When a specific
instance of a recurring entry is requested, the underlying note may represent
multiple instances. Default behavior makes appropriate modifications so that
the returned handle represents a single instance (but this might cause notes to
be created or modified as a side effect). Using CAL\_NOTEOPEN\_HANDLE\_NOSPLIT
will bypass any note creations or modifications and return a note handle that may
represent more than a single instance on the calendar.  

  




 




----------------------------------------------------------------------------------------------------------


 





