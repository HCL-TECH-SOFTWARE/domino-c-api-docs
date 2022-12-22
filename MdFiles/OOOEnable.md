




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




**Initial Release 8.5.2**



**Function : OOO**



**OOOEnable** **- This
function changes the state of  the OOO functionality as indicated by the bState
variable.**


**----------------------------------------------------------------------------------------------------------**



**#include <oooapi.h>**



STATUS
LNPUBLIC **OOOEnable(**  

      OOOCTXPTR \*pOOOContext,  

      BOOL  bState**);**



**Description :**



This
function changes the state of  the OOO functionality as indicated by the bState
variable.If the OOO functionality is already in the state indicated by the
bState flag, this function does nothing and returns success.  


When
you need to enable OOO (i.e. call it with bState flag set to TRUE) you should
call **OOOSetAwayPeriod** prior to calling **OOOEnable**.  If **OOOSetAwayPeriod**is not called, **OOOEnable** will use the previous value for start and
end.  If they are in the past then the OOO functionality will not be
enabled.When you need to disable OOO (i.e. call it with bState set to FALSE)
OOOSetAwayPeriod does not need to be called.   When **OOOEnable** is called
with the bState set to FALSE it means you want to disable OOO immediately.  If
you don't want to disable OOO functionality immediately, but rather you just
want to change the time when OOO should stop operating, the sequence of calls
is : **OOOStartOperation**, **OOOSetAwayPeriod**, **OOOEndOperation**.If
OOO is configured to run as a service and **OOOEnable** is used to disable,
the OOO service will be auto-disabled immediately.  The summary report will be
generated on the first email received after the disable has been requested, or
if no messages are received it will generated during the nightly router
maintenance.  If OOO is configured as an agent, the user will receive a summary
report and a request to disable the agent on the next scheduled run of the
agent will occur.


 


**Parameters :**



Input :  

pOOOContext  -  pointer obtained from the OOOStartOperation call  

  

bState  -  boolean value TRUE to enable, FALSE to disable  

  




Output :  

(routine)  -  Return status from this call - indicates either success or what
the error is.   

NOERROR - Successfully performed this operationThis function can return Domino
errors.  

OOO specific errors:  

ERR\_OOO\_MISSING\_INIT - OOOGetState was called prior to OOOInit()  

ERR\_OOO\_MISSING\_PARAM - One or more mandatory parameters were not specified  

ERR\_OOO\_MISSING\_MAILFILE - Mailfile information is not specified  

ERR\_OOO\_NOACCESS - User access is below Editor.  OOO is supported for Editor or
higher.  

ERR\_AGENT\_SEC\_CONFIGURATION- Error in agent configuration. This message is
suitable for display to the end user, it informs them of a problem and requests
to alert the administrator.  There is an additional message generated to the
server console and DDM which has considerably more technical details on how to
repair the configuration.  

  

  




 **See Also :**


**[OOOStartOperation](OOOStartOperation.md)**


**[OOOEndOperation](OOOEndOperation.md)**



----------------------------------------------------------------------------------------------------------


 





