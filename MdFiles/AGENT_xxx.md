




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



**AGENT\_xxx** **-** AgentRun -
dwFlags


**----------------------------------------------------------------------------------------------------------**



**#include <agents.h>**


 **Symbolic Values :**      AGENT\_REOPEN\_DB          -  If AGENT\_REOPEN\_DB is set, the
AgentRun call will reopen the agent's database with the privileges of the
signer of the agent. If the flag is not set, the agent's "context"
database will be open with the privileges of the current user (the current
Notes id or the current Domino web user).  

  




**Description :**



Possible
values for the dwFlags parameter of AgentRun.


 **See Also :**


**[AgentRun](AgentRun.md)**



----------------------------------------------------------------------------------------------------------


 





