




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



**Symbolic Value : Rich Text**



**STYLE\_FLAG\_xxx** **-** CDSTYLENAME
- Flags


**----------------------------------------------------------------------------------------------------------**



**#include <editods.h>**


 **Symbolic Values :**      STYLE\_FLAG\_FONTID         -  A FONTID follows the
CDSTYLENAME structure. The font is included in the style.  

  

      STYLE\_FLAG\_INCYCLE       -  This style is included in the Cycle Key
[F11]. The style is available when you press F11 to cyle through the named
styles  

  

      STYLE\_FLAG\_PERMANENT            -  A user name follows the CDSTYLENAME
structure. If STYLE\_FLAG\_FONTID is also set, the CDSTYLENAME structure is
followed by the FONTID which is then followed by the user name. The style is
available for all documents.  

  




**Description :**



Optional
values for the Flags member of the CDSTYLENAME structure.


 **See Also :**


**[CDSTYLENAME](CDSTYLENAME.md)**



----------------------------------------------------------------------------------------------------------


 





