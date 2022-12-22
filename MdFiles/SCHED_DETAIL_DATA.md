




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



**SCHED\_DETAIL\_DATA** **-** Schedule
detail list actual data.


**----------------------------------------------------------------------------------------------------------**



**#include
<nsfdata.h>**



**Definition :**



typedef struct {


 


   
WORD        wType;          /\* Notes data type for the data \*/


   
WORD        wDataLen;       /\* Length of the data that immediately follows \*/


   
BYTE        Attr;           /\* SCHED\_DETAIL\_DATA\_ATTR\_xxx attributes \*/


   
BYTE        bReserved;      /\* Reserved space/padding for ODS \*/


 


    /\* Now
comes the actual data that corresponds to the item values \*/


}
SCHED\_DETAIL\_DATA;


 


**Description :**



Schedule
detail list actual data.


 **See Also :**


**[SCHED\_DETAIL\_ENTRY](SCHED_DETAIL_ENTRY.md)**


**[SCHED\_DETAIL\_LIST](SCHED_DETAIL_LIST.md)**



----------------------------------------------------------------------------------------------------------


 





