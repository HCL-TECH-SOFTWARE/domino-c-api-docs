




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



**Data Type : Calendaring and
Scheduling**



**SCHED\_LIST** **-** Calendar
busy time schedule list structure


**----------------------------------------------------------------------------------------------------------**



**#include
<nsfdata.h>**



**Definition :**



typedef struct {


    DWORD  
NumEntries;         /\* Total number of schedule entries follow \*/


    WORD    wApplicationID;    
/\* Application id for UserAttr interpretation \*/


    WORD   
Spare;              /\* Pre Notes/Domino 6: spare 


                               
\*\* Notes/Domino 6: This now conveys the length of a single


                               
\*\* SCHED\_ENTRY\_xxx that follows.  Use this value


                               
\*\* to skip entries that MAY be larger (ie: a later version may


                               
\*\* extend SCHED\_ENTRY\_EXT by appending values


                               
\*\* that Notes/Domino 6 does not know about so SCHED\_ENTRY\_xxx


                               
\*\* would actually be larger than the Notes/Domino 6


                               
\*\* SCHED\_ENTRY\_EXT


                               
\*/


                               
/\* Now come the schedule entries... 


                               
\*\* IF Spare==0 then SCHED\_ENTRYs follow


                                \*\*
Otherwise Spare==the length of the


                               
\*\* SCHED\_ENTRY\_EXTs that follow


                               
\*/


} SCHED\_LIST;


 


**Description :**



This is the
schedule data. The SCHED\_LIST is followed by NumEntries of SCHED\_ENTRY or
SCHED\_ENTRY\_EXT.


 **See Also :**


**[Schedule\_AddSchedList](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/C321056B194D6140852563B800419FE9)**


**[Schedule\_NewFromSchedList](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/0158B37B2C0291238525635E00012DDC)**


**[SCHED\_ENTRY](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/5EDBDAD427D0F3328525636100504E3B)**


**[SCHED\_ENTRY\_EXT](SCHED_ENTRY_EXT.md)**



----------------------------------------------------------------------------------------------------------


 





