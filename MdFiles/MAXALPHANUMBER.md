




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




 


**Symbolic Value : Limits**



**MAXALPHANUMBER** **-** The maximum
length of a NUMBER that can be represented as a character string.


**----------------------------------------------------------------------------------------------------------**



**#include <misc.h>**



**Description :**



This symbol
defines the maximum length of a character string that represents a number.  By
declaring a character array of size MAXALPHANUMBER, callers of
ConvertTextToFLOAT() or ConvertFLOATToText() are assured that the array will be
large enough to hold the worst-case (largest) NUMBER character string.


 **See Also :**


**[ConvertFLOATToText](ConvertFLOATToText.md)**


**[ConvertTextToFLOAT](ConvertTextToFLOAT.md)**



----------------------------------------------------------------------------------------------------------


 





