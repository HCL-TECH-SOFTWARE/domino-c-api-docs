




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



**REG\_FILE\_DUP\_xxx** **-** Determine
the action When the registration API finds a duplicate Mail File or Roaming
folder. 


**----------------------------------------------------------------------------------------------------------**



**#include <reg.h>**


 **Symbolic Values :**      EG\_FILE\_DUP\_STOP           -  When a duplicate is found,
registration should stop.  

  

      REG\_FILE\_DUP       -  When a duplicate is found, registration should
generate a unique name and continue  

  

      REG\_FILE\_DUP       -  When a duplicate is found, registration should
continue by using the name (possibly overwriting the file)  

  




**Description :**



These
symobls are used to determine the action that the registration API should take
when finding a duplicate Mail File or Roaming folder. 


 **See Also :**


**[REG\_MAIL\_INFO\_EXT](notes:///852584E300582C9D/61FD4E9848264AD28525620B006BA8BD/37BEC1762987D083482573FB00322DB6)**


**[REG\_ROAMING\_INFO](REG_ROAMING_INFO.md)**



----------------------------------------------------------------------------------------------------------


 





