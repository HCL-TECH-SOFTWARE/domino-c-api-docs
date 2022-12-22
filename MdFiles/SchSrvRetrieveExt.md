




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



**SchSrvRetrieveExt** **- Retrieve
a schedule - extended**


**----------------------------------------------------------------------------------------------------------**



**#include <schedule.h>**



STATUS
LNPUBLIC **SchSrvRetrieveExt(**  

      LIST FAR \*pClientNames,  

      const UNID FAR \*pApptUnid,  

      TIMEDATE FAR \*pApptOrigDate,  

      DWORD  dwOptions,  

      TIMEDATE\_PAIR FAR \*pInterval,  

      LIST FAR \*pNames,  

      LIST FAR \*pDetails,  

      LIST FAR \*piCalList,  

      char FAR \*pszProxyUserName,  

      char FAR \*pszProxyPassword,  

      HCNTNR FAR \*rethCntnr**);**



**Description :**



When this
call is made on a server, it synchronously retrieves local or remote schedules
from the proper fanout servers. When this call is made on a client, it
retrieves only locally available information in busytime.nsf


 


This
container must be deallocated by the caller using SchContainer\_Free.


 


**Parameters :**



Input :  

pClientNames  -  List of users making query.  

  

pApptUnid  -  Ignore this UNID in computations.  

  

pApptOrigDate  -  This is the original start date of the appointment to ignore.
This is only here for Organizer 2.x compatibility.  

  

dwOptions  -  Option flags:  

SCHRQST\_COMPOSITE          default if dwOptions is 0  

SCHRQST\_EACHPERSON       return each person's schedule  

SCHRQST\_LOCAL                  only look up schedules locally  

SCHRQST\_FORCEREMOTE force remote even if you are using workstation based email  

SCHRQST\_EXTFORMAT get busytime in the SCHED\_ENTRY\_EXT format instead of the
normal SCHED\_ENTRY format from pre 6 Note: Use does not guarantee that data
will be in SCHED\_ENTRY\_EXT format since we do not convert data from pre 6
servers.  

  

pInterval  -  Pointer to a TIMEDATE\_PAIR structure that specifies the range
over which the free time search should be performed. In typical scheduling
applications this might be a range of 1 day or 5 days.  

  

pNames  -  Pointer to a list of distinguished names whose schedule should be
searched. This list is in TEXT\_LIST format without the datatype word. This list
can be build with the textlist package (e.g. ListAllocate)  

  

pDetails  -  Details  

  

piCalList  -  Call list  

  

pszProxyUserName  -  Proxy user name  

  

pszProxyPassword  -  Proxy password  

  




Output :  

(routine)  -  NOERROR - Successfully retrieved a schedule.  

ERR\_xxx - There are many possible errors. It is best to use the code in a call
to OSLoadString and display/log the error for the user as your default error
handling.  

  

  

rethCntnr  -  Handle of the container that results are returned in.  

  




 **See Also :**


**[SchContainer\_Free](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/1B1F99C51F7DAA688525635D006DEB1C)**


**[SCHRQST\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/619DE548C731AFEB8525635D00797CEC)**


**[SchRetrieve](SchRetrieve.md)**



----------------------------------------------------------------------------------------------------------


 





