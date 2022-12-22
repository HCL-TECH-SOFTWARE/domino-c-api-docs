




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



**AgentOpen** **- Open a
note containing an Agent.**


**----------------------------------------------------------------------------------------------------------**



**#include <agents.h>**



STATUS
LNPUBLIC **AgentOpen(**  

      DHANDLE  hDB,  

      NOTEID  AgentNoteID,  

      HAGENT far \*rethAgent**);**



**Description :**



Open the
note (identified by note ID) containing an Agent.  The handle returned by this
function must be closed by calling AgentClose().


 


**Parameters :**



Input :  

hDB  -  Handle to an open Domino database.  

  

AgentNoteID  -  ID of the note containing the Agent.  

  




Output :  

(routine)  -  Return indicates either success or what the error is. The return
codes include:   

  

NOERROR - Operation was successful.  

  

ERR\_xxx - STATUS returned from a lower-level function call.  

  

  

rethAgent  -  Handle to the open agent.  

  




 **See Also :**


**[AgentClose](AgentClose.md)**


**[AgentCreateRunContext](AgentCreateRunContext.md)**


**[AgentRun](AgentRun.md)**


**[HAGENT](HAGENT.md)**



----------------------------------------------------------------------------------------------------------


 





