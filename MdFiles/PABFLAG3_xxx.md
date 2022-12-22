




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




**Initial Release 6**



**Symbolic Value : Rich Text**



**PABFLAG3\_xxx** **-** Values for
DWORD extension to CDPABDEFINITION


**----------------------------------------------------------------------------------------------------------**



**#include <editods.h>**


 **Symbolic Values :**      PABFLAG3\_HIDE\_EE           -  Hide when embedded.  

  

      PABFLAG3\_HIDE\_MOBILE   -  Hide from mobile clients.  

  

      PABFLAG3\_LAYER\_USES\_DRM      -  True if boxes in a layer have set
PABFLAG\_DISPLAY\_RM on pabs.  

  




**Description :**



If the
Flags2 member of CDPABDEFINITION is set to PABFLAG2\_MORE\_FLAGS, the
CDPABDEFINITION may be followed by a DWORD extension. If the value of this
DWORD extension is EXTENDEDPABFLAGS3, then a second DWORD extension may be
present . These DWORD extensions follow the six R5 margin extension WORDs, if
they are present.


 


If the
second DWORD extension is set to PABFLAG3\_HIDE\_EE, hide when embedded. If it is
set to PABFLAG3\_HIDE\_MOBILE, hide from mobile clients. It is set to
PABFLAG3\_LAYER\_USES\_DRM if boxes in a layer have set PABFLAG\_DISPLAY\_RM for the
Flags member of CDPABDEFINITION.


 **See Also :**


**[CDPABDEFINITION](CDPABDEFINITION.md)**


**[EXTENDEDPABFLAGS3](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/E48F9EDCE17226DF852569D7005F8FAF)**



----------------------------------------------------------------------------------------------------------


 





