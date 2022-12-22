




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




**Initial Release 5.0**



**Symbolic Value : Constants; Rich
Text**



**DT\_xxx [CDEXT2FIELD - DTFlags]** **-** CDEXT2FIELD
- DTFlags


**----------------------------------------------------------------------------------------------------------**



**#include <misc.h>**


 **Symbolic Values :**      DT\_VALID    -  Validity bit: If 1, use new DTFMT; if 0, use
old TFMT  

  

      DT\_4DIGITYEAR      -  Require 4 digit year on INPUT (not output)  

  

      DT\_ALPHAMONTH   -  Require months be INPUT as letters, not digits (e.g.
"jan", not 01)  

  

      DT\_SHOWTIME       -  Display time element on output  

  

      DT\_SHOWDATE      -  Display date element on output  

  

      DT\_24HOUR            -  Display time on output using 24 hour clock format  

  

      DT\_STYLE\_YMD      -  Date element order: Year, Month, Day, Day-of-week  

  

      DT\_STYLE\_MDY      -  Date element order: Day-of-week, Month, Day, Year  

  

      DT\_STYLE\_DMY      -  Date element order: Day-of-week, Day, Month, Year  

  

      DT\_STYLE\_MSK      -  This is where we store the style value in DTFlags  

  




 **See Also :**


**[CDEXT2FIELD](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/6807B7F2AFEC3988482573FB00322DA5)**


**[DT\_GET\_STYLE](DT_GET_STYLE.md)**


**[DT\_SET\_STYLE](DT_SET_STYLE.md)**



----------------------------------------------------------------------------------------------------------


 





