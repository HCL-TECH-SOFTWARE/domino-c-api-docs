




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




 


**Symbolic Value : Font**



**FONT\_xxx\_SHIFT** **-** Symbolic
definitions used in a call to BYTEMASK.


**----------------------------------------------------------------------------------------------------------**



**#include <fontid.h>**


 **Symbolic Values :**      FONT\_SIZE\_SHIFT   -  Create a mask for the PointSize byte in
a FONTID.  

  

      FONT\_COLOR\_SHIFT          -  Create a mask for the Color byte in a
FONTID.  

  

      FONT\_STYLE\_SHIFT           -  Create a mask for the Attrib byte in a
FONTID.  

  

      FONT\_FACE\_SHIFT             -  Create a mask for the Face byte in a
FONTID.  

  




**Description :**



These
symbolic definitions are used in calls to the function BYTEMASK to specify
which byte in a DWORD is be masked off. These values are usually used in macros
that access the bytes in a FONTID.


 **See Also :**


**[BYTEMASK](BYTEMASK.md)**


**[FONTID](FONTID.md)**


**[FONTIDFIELDS](FONTIDFIELDS.md)**



----------------------------------------------------------------------------------------------------------


 





