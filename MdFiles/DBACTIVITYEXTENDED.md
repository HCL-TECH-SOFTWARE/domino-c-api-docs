




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




**Initial Release 8.0**



**Data Type : Database**



**DBACTIVITYEXTENDED** **-** Database
Activity Extended Structure.


**----------------------------------------------------------------------------------------------------------**



**#include
<nsfdb.h>**



**Definition :**



typedef struct {


        TIMEDATE
First;                              /\* Beginning of reporting period \*/


        TIMEDATE
Last;                        /\* End of reporting period \*/


        DWORD
Uses;                                  /\* # of uses in reporting period \*/


        DWORD
Reads;                          /\* # of reads in reporting period \*/


        DWORD
Writes;                         /\* # of writes in reporting period \*/


        DWORD
Adds;


        DWORD
Updates;


        DWORD
Deletes;


        DWORD
PrevDayUses;                    /\* # of uses in previous 24 hours \*/


        DWORD
PrevDayReads;                   /\* # of reads in previous 24 hours \*/


        DWORD
PrevDayAdds;


        DWORD
PrevDayUpdates;


        DWORD
PrevDayDeletes;


        DWORD
PrevWeekUses;                   /\* # of uses in previous week \*/


        DWORD
PrevWeekReads;                  /\* # of reads in previous week \*/


        DWORD
PrevWeekAdds;


        DWORD
PrevWeekUpdates;


        DWORD
PrevWeekDeletes;


        DWORD
PrevMonthUses;                 /\* # of uses in previous month \*/


        DWORD
PrevMonthReads;                /\* # of reads in previous month \*/


        DWORD
PrevMonthAdds;


        DWORD
PrevMonthUpdates;


        DWORD
PrevMonthDeletes;


}
DBACTIVITYEXTENDED;


 


**Description :**



Database
Activity Extended Structure.


 




----------------------------------------------------------------------------------------------------------


 





