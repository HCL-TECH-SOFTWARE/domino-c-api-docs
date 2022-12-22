




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



**Symbolic Value : Agents**



**ACTIONREPLY\_FLAG\_xxx** **-** Option flags
for CDACTIONREPLY record.


**----------------------------------------------------------------------------------------------------------**



**#include <queryods.h>**


 **Symbolic Values :**      ACTIONREPLY\_FLAG\_REPLYTOALL           -  Send reply to all
(otherwise, just to sender).  

  

      ACTIONREPLY\_FLAG\_INCLUDEDOC          -  Include a copy of the original
document.  

  

      ACTIONREPLY\_FLAG\_SAVEMAIL    -  Save a copy of the reply.  

  

      ACTIONREPLY\_FLAG\_NOAGENTREPLY     -  Do not reply to agent-generated
mail.  

  

      ACTIONREPLY\_FLAG\_REPLYONCE            -  Only reply once per sender.  

  




**Description :**



These flags
specify options for the Reply action for a Agent.  These flags are stored in
the dwFlags field of the CDACTIONREPLY structure.


 **See Also :**


**[CDACTIONREPLY](CDACTIONREPLY.md)**



----------------------------------------------------------------------------------------------------------


 





