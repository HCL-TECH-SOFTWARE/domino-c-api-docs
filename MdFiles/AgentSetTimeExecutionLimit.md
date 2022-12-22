




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



**Function : Agents**



**AgentSetTimeExecutionLimit** **- Set time
limit for Agent execution.**


**----------------------------------------------------------------------------------------------------------**



**#include <agents.h>**



STATUS
LNPUBLIC **AgentSetTimeExecutionLimit(**  

      HAGENTCTX  hAgentCtx,  

      DWORD  timeLimit**);**



**Description :**



Allow API
users to set time limit for Agent execution.  If the time limit is not set, the
default is 0 which means no time limit for the execution.  


 


If
an agent takes less than the specified time limit when a time limit is not set,
then if that specified time limit is set, the call to AgentRun for this agent
will take up the full amount of the time limit.


 


**Parameters :**



Input :  

hAgentCtx  -  Handle to the Agent.  

  

timeLimit  -  Time limit, in seconds, for the execution.  

  




Output :  

(routine)  -  Return status of the call - indicates either success or what the
error is.  The return error codes include:  

  

NOERROR  

  

ERR\_xxx - Error returned by lower level functions. Call OSLoadString to
interpret code.  

  

  




 **See Also :**


**[AgentCreateRunContext](AgentCreateRunContext.md)**



----------------------------------------------------------------------------------------------------------


 





