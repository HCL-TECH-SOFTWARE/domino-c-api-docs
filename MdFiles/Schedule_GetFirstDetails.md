




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




**Initial Release 6**



**Function : Calendaring and
Scheduling**



**Schedule\_GetFirstDetails** **- Returns
the handle to the first detail object for the schedule.**


**----------------------------------------------------------------------------------------------------------**



**#include <schedule.h>**



STATUS
LNPUBLIC **Schedule\_GetFirstDetails(**  

      HCNTNR  hCntnr,  

      HSCHEDULE  hSchedObj,  

      HCNTNROBJ \*rethDetailObj,  

      SCHED\_\_DETAIL\_LIST FAR \* FAR \*retpDetail**);**



**Description :**



Returns the
handle to the first detail object for the schedule.


 


**Parameters :**



Input :  

hCntnr  -  Handle of container to get details from.  

  

hSchedObj  -  Handle to the current schedule.  

  




Output :  

(routine)  -  Return status from this call:   

  

NOERROR   

  

ERR\_xxx - Other errors returned by this function and includes errors returned
by lower level functions. Call OSLoadString to obtain a string to display to
the user.  

  

  

rethDetailObj  -  Points to the handle to the detail.  

  

retpDetail  -  Points to the poiner to the detail.  

  




 **See Also :**


**[HCNTNR](HCNTNR.md)**


**[HCNTNROBJ](HCNTNROBJ.md)**


**[HSCHEDULE](HSCHEDULE.md)**


**[SCHED\_DETAIL\_DATA](SCHED_DETAIL_DATA.md)**


**[SCHED\_DETAIL\_ENTRY](SCHED_DETAIL_ENTRY.md)**


**[SCHED\_DETAIL\_LIST](SCHED_DETAIL_LIST.md)**



----------------------------------------------------------------------------------------------------------


 





