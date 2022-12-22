




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



**SchContainer\_FindSchedule** **- Get a
schedule.**


**----------------------------------------------------------------------------------------------------------**



**#include <schedule.h>**



STATUS
LNPUBLIC **SchContainer\_FindSchedule(**  

      HCNTNR  hCntnr,  

      char FAR \*pszUserName,  

      STATUS FAR \*retErrStatus,  

      DWORD FAR \*retdwErrGateway,  

      HSCHEDULE FAR \*retvbObj,  

      SCHEDULE FAR \* FAR \*retpSched**);**



**Description :**



This routine
gets a schedule from the passed in container for a given user.


 


**Parameters :**



Input :  

hCntnr  -  Points to the container.  

  

pszUserName  -  The name of the user or NULL for the composite schedule.  

  




Output :  

(routine)  -  NOERROR - Successfully found a schedule.  

ERR\_xxx - There are many possible errors. It is best to use the code in a call
to OSLoadString and display/log the error for the user as your default error
handling.  

  

  

  

retErrStatus  -  Points to where we return the Domino error if there is one.  

  

retdwErrGateway  -  Points to where we return the gateway error if there is
one.  

  

retvbObj  -  Points to  where we return the Vblock of sched object.  

  

retpSched  -  Returns pointer to the schedule object.  

  




 **See Also :**


**[SchContainer\_GetFirstSchedule](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/4E45B57B3215216B482573FB003235A6)**


**[SchContainer\_GetNextSchedule](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/1693AF3FEEDB673C482573FB00323571)**



----------------------------------------------------------------------------------------------------------


 





