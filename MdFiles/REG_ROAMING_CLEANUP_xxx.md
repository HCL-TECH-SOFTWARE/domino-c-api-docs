




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




**Initial Release 7.0**



**Symbolic Value : User Registration**



**REG\_ROAMING\_CLEANUP\_xxx** **-** Roaming
cleanup values.


**----------------------------------------------------------------------------------------------------------**



**#include <reg.h>**


 **Symbolic Values :**      REG\_ROAMING\_CLEANUP\_NEVER            -  Roaming client will
not cleanup.  

  

      REG\_ROAMING\_CLEANUP\_EVERY\_NDAYS           -  Roaming client will cleanup
every N days.  

  

      REG\_ROAMING\_CLEANUP\_AT\_SHUTDOWN          -  Roaming client will cleanup
at shutdown.  

  

      REG\_ROAMING\_CLEANUP\_PROMPT         -  Roaming client will prompt for
cleanup.  

  




**Description :**



Roaming
cleanup values for the CleanupSetting member of the REG\_ROAMING\_INFO structure.


 **See Also :**


**[REG\_ROAMING\_INFO](REG_ROAMING_INFO.md)**



----------------------------------------------------------------------------------------------------------


 





