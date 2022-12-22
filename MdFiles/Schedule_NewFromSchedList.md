




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



**Schedule\_NewFromSchedList** **- Adds a
schedule to a schedule container**


**----------------------------------------------------------------------------------------------------------**



**#include <schgtw.h>**



STATUS
LNPUBLIC **Schedule\_NewFromSchedList(**  

      HCNTNR  hCntnr,  

      TIMEDATE\_PAIR FAR \*pInterval,  

      SCHED\_LIST FAR \*pSchedList,  

      char FAR \*pUsername,  

      STATUS  errStatus,  

      DWORD  dwErrGateway,  

      HSCHEDULE FAR \*rethSched**);**



**Description :**



This routine
addes a schedule to a schedule container.


 


**Parameters :**



Input :  

hCntnr  -  A handle to the schedule container  

  

pInterval  -  Points to the overall interval of the schedule.  

  

pSchedList  -  Points to the SCHED\_LIST  

  

pUsername  -  The name of the owner of this schedule  

  

errStatus  -  Domino error status returned if schedule couldn't be created.  

  

dwErrGateway  -  Native gateway error returned if schedule couldn't be created.  

  




Output :  

(routine)  -  NOERROR - Successfully added a schedule.  

ERR\_xxx - There are many possible errors. It is best to use the code in a call
to OSLoadString and display/log the error for the user as your default error
handling.  

  

  

rethSched  -  Returns the HCNTNROBJ of the new schedule  

  




 **See Also :**


**[Schedule\_AddSchedList](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/C321056B194D6140852563B800419FE9)**


**[Schedule\_ExtractMoreSchedList](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/F4DB02C55DAF2FBE482573FB00323559)**


**[Schedule\_ExtractSchedList](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/E39E4EA3A47231D8482573FB003235A4)**


**[SCHED\_LIST](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/77A3B36469FBA9FD85256361004F207C)**



----------------------------------------------------------------------------------------------------------


 





