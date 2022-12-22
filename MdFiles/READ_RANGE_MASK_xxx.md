




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



**READ\_RANGE\_MASK\_xxx** **-** Bits that
control what properties about the calendar entries will be returned for
CalReadRange.


**----------------------------------------------------------------------------------------------------------**



**#include <calapi.h>**


 **Symbolic Values :**      READ\_RANGE\_MASK\_DTSTART    -    

  

      READ\_RANGE\_MASK\_DTEND         -    

  

      READ\_RANGE\_MASK\_DTSTAMP    -    

  

      READ\_RANGE\_MASK\_SUMMARY   -    

  

      READ\_RANGE\_MASK\_CLASS         -    

  

      READ\_RANGE\_MASK\_PRIORITY    -    

  

      READ\_RANGE\_MASK\_RECURRENCE\_ID    -    

  

      READ\_RANGE\_MASK\_SEQUENCE              -    

  

      READ\_RANGE\_MASK\_LOCATION   -    

  

      READ\_RANGE\_MASK\_TRANSP       -    

  

      READ\_RANGE\_MASK\_CATEGORY             -    

  

      READ\_RANGE\_MASK\_APPTTYPE   -    

  

      READ\_RANGE\_MASK\_NOTICETYPE           -    

  

      READ\_RANGE\_MASK\_STATUS       -    

  

      READ\_RANGE\_MASK\_ONLINE\_URL           -  Includes online meeting URL as
well as any online meeting password or conf ID  

  

      READ\_RANGE\_MASK\_NOTESORGANIZER             -  For performance reasons,
the organizer may not be stored in ORGANIZER but rather in X-LOTUS-ORGANIZER to
avoid lookups necessary to get the internet address.  

  

      READ\_RANGE\_MASK\_NOTESROOM          -  For performance reasons, the
organizer may not be stored in PARTICIPANT but rather in X-LOTUS-ROOM to avoid
lookups necessary to get the internet address.  

  

      READ\_RANGE\_MASK\_ALARM         -  Output alarm information for this entry  

  




 




----------------------------------------------------------------------------------------------------------


 





