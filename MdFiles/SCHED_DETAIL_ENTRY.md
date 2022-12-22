




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



**SCHED\_DETAIL\_ENTRY** **-** Schedule
detail list entry.


**----------------------------------------------------------------------------------------------------------**



**#include
<nsfdata.h>**



**Definition :**



typedef struct {


   
WORD        wPrefixLen;     /\* Length of THIS prefix entry, in case it


                  
             \*\* ever grows, so that new items can be 


                               
\*\* easily skipped


                               
\*/


   
WORD        wEntryLen;      /\* Length of THIS entire entry and ALL of 


                               
\*\* its related data.


                               
\*/


   
UNID        Unid;           /\* UNID of the entry this is details of \*/


   
WORD        wOffsetDetails; /\* Offset from entry start to actual data \*/


   
BYTE        Attr;           /\* SCHED\_DETAIL\_ENTRY\_ATTR\_xxx attributes (TBD) \*/


   
BYTE        bReserved;      /\* Reserved space/padding for ODS \*/


 


    /\* Now
comes the data that corresponds to the item values (1 per item name)


    \*\*
UNLESS dwEntryLen == wPrefixLen (which means NO details available


    \*\* for
this UNID)


    \*/


}
SCHED\_DETAIL\_ENTRY;


 


**Description :**



Schedule
detail list entry.


 **See Also :**


**[SCHED\_DETAIL\_DATA](SCHED_DETAIL_DATA.md)**


**[SCHED\_DETAIL\_LIST](SCHED_DETAIL_LIST.md)**



----------------------------------------------------------------------------------------------------------


 





