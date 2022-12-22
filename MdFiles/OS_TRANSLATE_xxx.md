




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




 


**Symbolic Value : Miscellaneous**



**OS\_TRANSLATE\_xxx** **-** Controls the
direction in which OSTranslate converts strings.


**----------------------------------------------------------------------------------------------------------**



**#include <osmisc.h>**


 **Symbolic Values :**      OS\_TRANSLATE\_NATIVE\_TO\_LMBCS        -  Convert the input
string from the machine's native character set to LMBCS (optimized for Group
1).  

  

      OS\_TRANSLATE\_LMBCS\_TO\_NATIVE        -  Convert the input string from
LMBCS (optimized for Group 1) to the machine's native character set.  

  

      OS\_TRANSLATE\_LOWER\_TO\_UPPER        -  Current international case table.  

  

      OS\_TRANSLATE\_UPPER\_TO\_LOWER        -  Current international case table.  

  

      OS\_TRANSLATE\_UNACCENT         -  International unaccenting table.  

  

      OS\_TRANSLATE\_OSNATIVE\_TO\_LMBCS   -  Convert the input string from DOS
(code page) to LMBCS (optimized for Group 1).  

  

      OS\_TRANSLATE\_LMBCS\_TO\_OSNATIVE   -  Convert the input string from LMBCS
(optimized for Group 1) to DOS.  

  

      OS\_TRANSLATE\_LMBCS\_TO\_ASCII           -  Convert the input string from
LMBCS to character text.  

  

      OS\_TRANSLATE\_LMBCS\_TO\_UNICODE     -  Convert the input string from LMBCS
to UNICODE.  

  

      OS\_TRANSLATE\_LMBCS\_TO\_UTF8            -  Convert the input string from
LMBCS to UTF8.  

  

      OS\_TRANSLATE\_UNICODE\_TO\_LMBCS     -  Convert the input string from
UNICODE to LMBCS.  

  

      OS\_TRANSLATE\_UTF8\_TO\_LMBCS            -  Convert the input string from
UTF8 to LMBCS.  

  




**Description :**



These flags
control the direction in which OSTranslate converts character strings -- either
LMBCS to native, or native to LMBCS.   

  

LMBCS is the Lotus Multi-Byte Character Set.


 **See Also :**


**[OSTranslate](OSTranslate.md)**



----------------------------------------------------------------------------------------------------------


 





