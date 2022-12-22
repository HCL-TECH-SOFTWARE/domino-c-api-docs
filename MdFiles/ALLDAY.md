




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




 


**Symbolic Value : Time**



**ALLDAY** **-** Wildcard
value for the Time portion of a TIMEDATE data structure.


**----------------------------------------------------------------------------------------------------------**



**#include <misc.h>**



**Description :**



Wildcard
value for the Time portion of a TIMEDATE data structure. Functions that test or
compare a TIMEDATE in which the Time portion is set to ALLDAY will succeed for
the Time portion of a TIMEDATE. For example:   

Suppose you have two TIMEDATES (td1 and td2) that are identical, except
td1.Time = ALLDAY and td2.Time = 2000.  If you compare them as follows:  

      td\_compare\_result = TimeDateCompare(&td1, &td2);  

 The integer returned in td\_compare\_result will be 0, indicating that the two
TIMEDATEs are equal.


 **See Also :**


**[ANYDAY](ANYDAY.md)**


**[TIMEDATE](TIMEDATE.md)**



----------------------------------------------------------------------------------------------------------


 





