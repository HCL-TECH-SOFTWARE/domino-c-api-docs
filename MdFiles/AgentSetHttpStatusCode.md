




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:"Tms Rmn";
 panose-1:2 2 6 3 4 5 5 2 3 4;}
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




 


**Function : Agents**



**AgentSetHttpStatusCode** **- Set an
agent's return http status code.**


**----------------------------------------------------------------------------------------------------------**



**#include <agents.h>**



STATUS **AgentSetHttpStatusCode(**  

      HAGENTCTX  hAgentCtx,  

      DWORD  retStatus**);**



**Description :**



Set an
agent's return HTTP status code. This must be a http status code as defined by <http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html>
and supported by the web server.


 


**Parameters :**



Input :  

hAgentCtx  -  The agent context.  

  

retStatus  -  The http status code.  

  




Output :  

(routine)  -  Returns status from the call, either success or an error.  

  

  




 **Sample Usage :**


      /\*
Assumes HAGENTCTX and DWORD http status code where kResultsOK = 200.\*/


 


            AgentSetHttpStatusCode(HAgentCtx,
kResultsOK); 


 **See Also :**




----------------------------------------------------------------------------------------------------------


 





