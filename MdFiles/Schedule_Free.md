




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



**Schedule\_Free** **- Frees a
schedule from within a container.**


**----------------------------------------------------------------------------------------------------------**



**#include <schgtw.h>**



STATUS
LNPUBLIC **Schedule\_Free(**  

      HCNTNR  hCntnr,  

      HSCHEDULE  hSched**);**



**Description :**



This routine
frees a schedule from within a container.


 


**Parameters :**



Input :  

hCntnr  -  Handle of schedule container.  

  

hSched  -  The HCNTNROBJ of the schedule to free.  

  




Output :  

(routine)  -  NOERROR - Successfully freed schedule.  

ERR\_xxx - There are many possible errors. It is best to use the code in a call
to OSLoadString and display/log the error for the user as your default error
handling.  

  

  




 **See Also :**


**[SchContainer\_FindSchedule](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/2E4FE2D9B7788C5A8525635D006E1F86)**


**[SchContainer\_GetFirstSchedule](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/4E45B57B3215216B482573FB003235A6)**


**[SchContainer\_GetNextSchedule](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/1693AF3FEEDB673C482573FB00323571)**


**[Schedule\_NewFromSchedList](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/0158B37B2C0291238525635E00012DDC)**



----------------------------------------------------------------------------------------------------------


 





