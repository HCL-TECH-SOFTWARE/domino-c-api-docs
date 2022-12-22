




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




**Initial Release 5.0**



**Function : Calendaring and
Scheduling**



**Schedule\_Access** **- Get
access to a schedule object.**


**----------------------------------------------------------------------------------------------------------**



**#include <schedule.h>**



STATUS
LNPUBLIC **Schedule\_Access(**  

      HCNTNR  hCntnr,  

      HSCHEDULE  hSched,  

      SCHEDULE FAR \*\*pretSched**);**



**Description :**



This function
returns a pointer to a schedule object.


 


**Parameters :**



Input :  

hCntnr  -  A handle to the schedule container.  

  

hSched  -  A handle to the existing schedule.  

  




Output :  

(routine)  -  NOERROR - Successfully returned access to a SCHEDULE object.  

ERR\_xxx (See ERR\_xxx for possible values).  

  

  

pretSched  -  Returns a pointer to a SCHEDULE structure.  

  




 




----------------------------------------------------------------------------------------------------------


 





