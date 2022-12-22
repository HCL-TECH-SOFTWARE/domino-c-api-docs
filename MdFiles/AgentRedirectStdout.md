




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



**Function : Agents**



**AgentRedirectStdout** **- Set
standard output redirection for LotusScript Agents**


**----------------------------------------------------------------------------------------------------------**



**#include <agents.h>**



STATUS
LNPUBLIC **AgentRedirectStdout(**  

      HAGENTCTX  hAgentCtx,  

      WORD  redirType**);**



**Description :**



This routine
is used to either disable standard output of LotusScript agent actions that use
PRINT statements, or to redirect it to the log file or to an in-memory buffer. 
The output of the PRINT statements is assigned to the specified runtime
context, and is controlled by the redirType argument.    This argument can be
set to one of the following constant values defined in agents.h, as described.


 


**redirType
Value                             Redirected Standard Output**


AGENT\_REDIR\_NONE                   Disabled


AGENT\_REDIR\_LOG                     Log
file (log.nsf)


AGENT\_REDIR\_MEMORY             Memory
buffer - reset with each call to AgentRun() 


AGENT\_REDIR\_MEMAPPEND       Memory
buffer - appended to with each call to AgentRun()


 


When
redirecting to memory, you must call AgentQueryStdoutBuffer() after the agent
execution to read the output buffer.   Since this redirection is associated
with the runtime context, the desired action can be changed prior to each call
to AgentRun().


 


 


**Parameters :**



Input :  

hAgentCtx  -  Handle to the Agent runtime context.  

  

redirType  -  Standard output redirection type.   Must be set to appropriate
AGENT\_REDIR\_xxx value.  

  




Output :  

(routine)  -  Return indicates either success or what the error is. The return
codes include:   

  

NOERROR - Operation was successful.  

  

ERR\_xxx - STATUS returned from a lower-level function call.  

  

  




 **See Also :**


**[AgentQueryStdoutBuffer](AgentQueryStdoutBuffer.md)**


**[AgentRun](AgentRun.md)**


**[AGENT\_REDIR\_xxx](AGENT_REDIR_xxx.md)**


**[HAGENTCTX](HAGENTCTX.md)**



----------------------------------------------------------------------------------------------------------


 





