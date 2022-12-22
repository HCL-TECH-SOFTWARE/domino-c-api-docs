




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



**CAL\_ACTION\_xxx** **-** CAL\_ACTION
\_xxx values are used to provide additional processing control to some actions
taken by CalNoticeAction and CalEntryAction


**----------------------------------------------------------------------------------------------------------**



**#include <calapi.h>**


 **Symbolic Values :**      CAL\_ACTION\_DO\_OVERWRITE\_CHECK     -  Indicates that a check
should be performed when processing the action to determine if an overwrite of
invitee changes to the entry will occur.  

  

      CAL\_ACTION\_UPDATE\_ALL\_PARTICIPANTS          -  Used to indicate that
current entry participants should be notified of changes to the participant
list in addition to those being added or removed.  

  




 




----------------------------------------------------------------------------------------------------------


 





