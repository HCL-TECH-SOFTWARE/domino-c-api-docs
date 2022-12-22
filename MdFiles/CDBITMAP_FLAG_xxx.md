




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




 


**Symbolic Value : Rich Text**



**CDBITMAP\_FLAG\_xxx** **-** CDBITMAPHEADER
- Flags


**----------------------------------------------------------------------------------------------------------**



**#include <editods.h>**


 **Symbolic Values :**      CDBITMAP\_FLAG\_REQUIRES\_PALETTE    -  Bitmap uses >16
colors or >4 grey scale levels.  

  

      CDBITMAP\_FLAG\_COMPUTE\_PALETTE     -  Initialized by import code for
"first time" importing of bitmaps from clipboard or file, to tell
Notes that it should compute whether or not to use a color palette. All imports
and API programs should initially set this bit to let the Editor compute
whether it needs the palette or not.  

  




**Description :**



Option flags
set in the CDBITMAPHEADER record.


 **See Also :**


**[CDBITMAPHEADER](CDBITMAPHEADER.md)**



----------------------------------------------------------------------------------------------------------


 





