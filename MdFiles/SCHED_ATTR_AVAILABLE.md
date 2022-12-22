




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Courier;
 panose-1:2 7 4 9 2 2 5 2 4 4;}
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




**Initial Release 4.5**



**Function : Calendaring and
Scheduling**



**SCHED\_ATTR\_AVAILABLE** **- Check if
time is available.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdata.h>**



BOOL **SCHED\_ATTR\_AVAILABLE(**  

      BYTE  attr**);**



**Description :**



Implemented
as a macro:


 


#define SCHED\_ATTR\_AVAILABLE(attr)
(!((attr) & SCHED\_ATTR\_BUSY\_BASE))


 


**Parameters :**



Input :  

attr  -  The attributes for this schedule entry.  

  




Output :  

(routine)  -  Returns TRUE if it is an available time, FALSE if it is a busy
time.  

  

  




 **See Also :**


**[SCHED\_ENTRY](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/5EDBDAD427D0F3328525636100504E3B)**



----------------------------------------------------------------------------------------------------------


 





