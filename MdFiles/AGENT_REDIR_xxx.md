




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



**Symbolic Value : Agents**



**AGENT\_REDIR\_xxx** **-** Definitions
for stdout redirection types.


**----------------------------------------------------------------------------------------------------------**



**#include <agents.h>**


 **Symbolic Values :**      AGENT\_REDIR\_NONE         -  Goes to the bit bucket.  

  

      AGENT\_REDIR\_LOG           -  Goes to the log file (default).  

  

      AGENT\_REDIR\_MEMORY   -  Goes to a memory buffer, cleared each AgentRun.  

  

      AGENT\_REDIR\_MEMAPPEND         -  Goes to buffer, append mode for each
agent.  

  




**Description :**



This
specifies where output from the LotusScript "print" statement will
go.


 **See Also :**


**[AgentRedirectStdout](AgentRedirectStdout.md)**



----------------------------------------------------------------------------------------------------------


 





