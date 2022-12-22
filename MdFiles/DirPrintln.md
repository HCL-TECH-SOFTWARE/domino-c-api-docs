




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




**Initial Release 8.5.2**



**Function : Dir**



**DirPrintln** **- A
DIRPRINTLN\_PROC that writes a line(s) to the Notes/Domino console via
xprintf().** 


**----------------------------------------------------------------------------------------------------------**



**#include <dirprint.h>**



void
LNCALLBACK **DirPrintln(**  

      void \*printctx,  

      const char \*line**);**



**Description :**



A
DIRPRINTLN\_PROC that writes a line(s) to the Notes/Domino console via
xprintf(). 


 


**Parameters :**



Input :  

printctx  -  Not used   

  

line  -  Line(s) to print. Multiple lines have '\n' separators. (does not
include '\n' terminator)   

  




 


 




----------------------------------------------------------------------------------------------------------


 





