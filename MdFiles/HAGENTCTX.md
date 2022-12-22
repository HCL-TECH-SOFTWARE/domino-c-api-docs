




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Courier;
 panose-1:2 7 4 9 2 2 5 2 4 4;}
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



**Data Type : Agents**



**HAGENTCTX** **-** Handle to an
Agent runtime context.


**----------------------------------------------------------------------------------------------------------**



**#include
<agents.h>**



**Definition :**



typedef void far
\*HAGENTCTX;


 


**Description :**



In order to
actually run an agent, a "runtime context" must be created.  This
context maintains information specific to a single execution of the agent.  The
agent runtime context is created with the function AgentCreateRunContext(), and
must be freed with the function AgentDestroyRunContext().


 **See Also :**


**[AgentCreateRunContext](AgentCreateRunContext.md)**


**[AgentDestroyRunContext](AgentDestroyRunContext.md)**


**[AgentRun](AgentRun.md)**



----------------------------------------------------------------------------------------------------------


 





