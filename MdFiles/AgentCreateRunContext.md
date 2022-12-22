




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




**Initial Release 4.0**



**Function : Agents**



**AgentCreateRunContext** **- Create an
Agent run-time context.**


**----------------------------------------------------------------------------------------------------------**



**#include <agents.h>**



STATUS
LNPUBLIC **AgentCreateRunContext(**  

      HAGENT  hAgent,  

      void far \*pReserved,  

      DWORD  dwFlags,  

      HAGENTCTX far \*rethContext**);**



**Description :**



Create a
run-time context for execution of the specified Agent.  This context maintains
information about a single execution of the Agent, and must be created before
the agent can be run.  This run-time context must be freed by calling AgentDestroyRunContext().


 


**Parameters :**



Input :  

hAgent  -  Handle to the Agent.  

  

pReserved  -  Reserved;  must be NULL.  

  

dwFlags  -  Optional.  Use this flag to tell the run context that when it runs
an agent, you want it to check the privileges of the signer of that agent and
apply them.  For example, if the signer of the agent has "restricted"
agent privileges, then the agent will be restricted.  If you do not set this
flag, all agents run as unrestricted.  

  

List of security checks enabled by this flag:  

     Restricted/unrestricted agent  

     Can create databases  

     Is agent targeted to this machine  

     Is user allowed to access this machine  

     Can user run personal agents  

  




Output :  

(routine)  -  Return indicates either success or what the error is. The return
codes include:   

  

NOERROR - Operation was successful.  

  

ERR\_xxx - STATUS returned from a lower-level function call.  

  

  

rethContext  -  Handle to the Agent run-time context.  

  




 **See Also :**


**[AgentDestroyRunContext](AgentDestroyRunContext.md)**


**[AgentRun](AgentRun.md)**


**[HAGENT](HAGENT.md)**


**[HAGENTCTX](HAGENTCTX.md)**



----------------------------------------------------------------------------------------------------------


 





