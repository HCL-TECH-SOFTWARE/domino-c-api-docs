




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




**Initial Release 4.5**



**Function : Calendaring and
Scheduling**



**SchContainer\_GetFirstSchedule** **- Get first
schedule object in a container.**


**----------------------------------------------------------------------------------------------------------**



**#include <schedule.h>**



STATUS
LNPUBLIC **SchContainer\_GetFirstSchedule(**  

      DHANDLE  hCntnr,  

      HSCHEDULE FAR \*rethObj,  

      SCHEDULE FAR \* FAR \*retpSchedule**);**



**Description :**



This
function is used to get a handle to the first schedule object in a container.


 


**Parameters :**



Input :  

hCntnr  -  The container handle.  

  




Output :  

(routine)  -  NOERROR - Successfully got first schedule.  

ERR\_xxx - There are many possible errors. It is best to use the code in a call
to OSLoadString and display/log the error for the user as your default error
handling.  

  

  

  

rethObj  -  Points to where we return the handle to the schedule.  

  

retpSchedule  -  Points to where we return a pointer to the actual data.  

  




 **See Also :**


**[SchContainer\_GetNextSchedule](notes:///852584E300582C9D/61FD4E9848264AD28525620B006BA8BD/1693AF3FEEDB673C482573FB00323571)**



----------------------------------------------------------------------------------------------------------


 





