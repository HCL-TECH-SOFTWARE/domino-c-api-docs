




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



**Symbolic Value : Extension Manager**



**EM\_BEFORE, EM\_AFTER** **-** EMRECORD -
NotificationType


**----------------------------------------------------------------------------------------------------------**



**#include <extmgr.h>**


 **Symbolic Values :**      EM\_BEFORE            -  Call is before Domino or Notes core
processing.  

  

      EM\_AFTER   -  Call is after Domino or Notes core processing.  

  




**Description :**



Indicator
stored in the EMRECORD passed to an extension manager callback.  This value
tells the callback whether this call is before or after Domino or Notes has
performed the core processing for this operation.


 **See Also :**


**[EMRECORD](EMRECORD.md)**



----------------------------------------------------------------------------------------------------------


 





