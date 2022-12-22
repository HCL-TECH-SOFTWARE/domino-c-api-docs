




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



**Symbolic Value : Constants; Rich
Text**



**EXTENDEDPABFLAGS3** **-** Value for
DWORD extension to CDPABDEFINITION


**----------------------------------------------------------------------------------------------------------**



**#include <editods.h>**



**Description :**



This DWORD
extends the CDPABDEFINITION structure. 


 


If the
Flags2 member of CDPABDEFINITION is set to PABFLAG2\_MORE\_FLAGS, the
CDPABDEFINITION may be followed by a DWORD extension. If the value of this
DWORD extension is EXTENDEDPABFLAGS3, then a second DWORD extension may be
present with a value of PABFLAG3\_HIDE\_EE. These DWORD extensions follow the six
R5 margin extension WORDs, if they are present.


 **See Also :**


**[CDPABDEFINITION](CDPABDEFINITION.md)**


**[PABFLAG3\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/FA5ED726CA007728852569D7005FDC2B)**



----------------------------------------------------------------------------------------------------------


 





