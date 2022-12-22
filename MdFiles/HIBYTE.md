




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




 


**Function : Data Manipulation**



**HIBYTE** **- Returns
the high-order BYTE of a WORD.**


**----------------------------------------------------------------------------------------------------------**



**#include <global.h>**



BYTE **HIBYTE(**  

      WORD  dataword**);**



**Description :**



A machine
independent macro that returns the high-order BYTE of a WORD.


 


**Parameters :**



Input :  

dataword  -  Machine independent value of which high-order BYTE is to be
returned.  

  




Output :  

(routine)  -  High-order BYTE of the WORD.  

  

  




 **See Also :**


**[LOBYTE](LOBYTE.md)**


**[HIWORD](HIWORD.md)**



----------------------------------------------------------------------------------------------------------


 





