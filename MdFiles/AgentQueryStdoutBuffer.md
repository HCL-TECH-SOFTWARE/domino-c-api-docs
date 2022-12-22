




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




**Initial Release 4.5**



**Function : Agents**



**AgentQueryStdoutBuffer** **- Returns a
Handle to redirected LotusScript Agent output.**


**----------------------------------------------------------------------------------------------------------**



**#include <agents.h>**



void
LNPUBLIC **AgentQueryStdoutBuffer(**  

      HAGENTCTX  hAgentCtx,  

      DHANDLE FAR \*retHdl,  

      DWORD FAR \*retSize**);**



**Description :**



This routine
will return a handle and byte length of a buffer containing the redirected
standard output of a LotusScript based agent.   Only output redirection to an
in-memory buffer that has been configured for the specified Agent runtime
context, via AgentRedirectStdout(), is accessible by this routine.


 


**Parameters :**



Input :  

hAgentCtx  -  Handle to the Agent runtime context.  

  




Output :  

retHdl  -  Handle to redirected standard output buffer.   This handle is owned
by Notes and must not be freed by the API program.  

  

retSize  -  Byte length of retrieved buffer.  

  




 **Sample Usage :**


...


  
HAGENT               hOpenAgent


  
HAGENTCTX       hOpenAgentCtx


  
DHANDLE          hStdout;  

   DWORD           dwLen;  

   char            \*pStdout;


  
STATUS          error = NOERROR;


...


   /\* agent
run handle and runtime context handle already created \*/


   error =
AgentRedirectStdout (hOpenAgentCtx, AGENT\_REDIR\_MEMORY))


...   


   error =
AgentRun (hOpenAgent, hOpenAgentCtx, (DHANDLE) 0, (DWORD) 0);  

...


  
AgentQueryStdoutBuffer (hOpenAgentCtx, &hStdout, &dwLen);  

   pStdout = OSLock(char, hStdout);  

   pStdout[dwLen]='\0';


  
printf("Redirected PRINT statements:%s\n", pStdout);  

   OSUnlock(hStdout);


...


 


 **See Also :**


**[AgentCreateRunContext](AgentCreateRunContext.md)**


**[AgentRedirectStdout](AgentRedirectStdout.md)**


**[HAGENTCTX](HAGENTCTX.md)**



----------------------------------------------------------------------------------------------------------


 





