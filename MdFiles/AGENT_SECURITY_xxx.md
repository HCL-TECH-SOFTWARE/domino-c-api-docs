




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




**Initial Release 4.51**



**Symbolic Value : Agents**



**AGENT\_SECURITY\_xxx** **-** AgentCreateRunContext
- dwFlags


**----------------------------------------------------------------------------------------------------------**



**#include <agents.h>**


 **Symbolic Values :**      AGENT\_SECURITY\_OFF     -  Turn off the security option for
this run context.  

  

      AGENT\_SECURITY\_ON       -  This flag tells the run context that when it
runs an agent, check the privileges of the signer of that agent and apply them.
For example, if the signer of the agent has "restricted" agent
privileges, then the agent will be restricted. If you do not set this flag, all
agents run as unrestricted. This flag enables the following security checks:  

 Restricted/unrestricted agent  

 Can create databases  

 Is agent targeted to this machine  

 Is user allowed to access this machine  

 Can user run personal agents  

  




**Description :**



Possible
values for the dwFlags parameter in AgentCreateRuncontext.  Specifies to the
run context when it runs an agent, whether to check the privileges of the
signer and apply them.


 **See Also :**


**[AgentCreateRunContext](AgentCreateRunContext.md)**



----------------------------------------------------------------------------------------------------------


 





