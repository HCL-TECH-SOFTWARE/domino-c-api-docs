




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




**Initial Release 6**



**Data Type : Calendaring and
Scheduling**



**SCHED\_ENTRY\_EXT** **-** Scheduling
busy time entry extended


**----------------------------------------------------------------------------------------------------------**



**#include
<nsfdata.h>**



**Definition :**




typedef
struct {


   
UNID            Unid;       /\* UNID of the entry \*/


   
TIMEDATE\_PAIR   Interval;   /\* Interval of the entry \*/


   
BYTE            Attr;       /\* SCHED\_ATTR\_xxx attributes defined by Notes \*/


   
BYTE            UserAttr;   /\* Application specific attributes \*/


   
BYTE            spare[2];


    


    /\* Everything
above this point is the same as SCHED\_ENTRY for preR6 clients!


    \*\*
Everything from here on down is R6 (or later) only!


    \*/


 


   
UNID            ApptUnid;   /\* ApptUNID of the entry \*/


   
DWORD           dwEntrySize;/\* Size of this entry (for future ease of
expansion) \*/


   
GEO\_INFO        GEOInfo;    /\* Geographical coordinates of the entry \*/


}
SCHED\_ENTRY\_EXT;


 


**Description :**



This is the
extended data structure that describes an individual schedule entry.


 **See Also :**


**[SCHED\_ENTRY](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/5EDBDAD427D0F3328525636100504E3B)**


**[SCHED\_LIST](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/77A3B36469FBA9FD85256361004F207C)**



----------------------------------------------------------------------------------------------------------


 





