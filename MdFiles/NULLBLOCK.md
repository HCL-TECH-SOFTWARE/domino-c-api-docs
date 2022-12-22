




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




 


**Symbolic Value : Constants**



**NULLBLOCK** **-** An empty
(non-existent) BLOCK.


**----------------------------------------------------------------------------------------------------------**



**#include <pool.h>**



**Description :**



NULLBLOCK is
used to define a non-existent block.  There is no need for an API application
to use this;  API applications access this data at the BLOCKID level. 
NULLBLOCK should be considered a lower level data type from which ISNULLBLOCKID
is abstracted. 


 **See Also :**


**[BLOCK](BLOCK.md)**


**[BLOCKID](BLOCKID.md)**


**[ISNULLBLOCKID](ISNULLBLOCKID.md)**



----------------------------------------------------------------------------------------------------------


 





