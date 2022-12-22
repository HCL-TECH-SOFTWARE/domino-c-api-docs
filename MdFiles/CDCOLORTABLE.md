




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Courier;
 panose-1:2 7 4 9 2 2 5 2 4 4;}
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




 


**Data Type : Composite Data; Rich
Text**



**CDCOLORTABLE** **-** Bitmap color
table


**----------------------------------------------------------------------------------------------------------**



**#include
<editods.h>**



**Definition :**



typedef struct {  

    LSIG Header;  

    /\* One or more color table entries go here \*/  

} CDCOLORTABLE;


 


**Description :**



A color
table is one of the optional records following a CDBITMAPHEADER record.  The
color table specifies the mapping between 8-bit bitmap samples and 24-bit
Red/Green/Blue colors.  

  

The color table consists of a record header, which identifies this as a Color
Table record, followed by up to 256 3-byte color table entries.  The number of
color entries is specified in the ColorCount field of CDBITMAPHEADER.  Color
table entries are only required for the range of color values stored in the
bitmap;  for example, a bitmap that uses 16 color values (0 to 15) would only
require 16 color table entries (not the 256 that the 8-bit samples allow).  

  

Each color table entry consists of 3 bytes, Red (byte 0), Green (byte 1), and
Blue (byte 2).  Each byte is a color value in the range 0 to 255.


 **See Also :**


**[CDBITMAPHEADER](CDBITMAPHEADER.md)**



----------------------------------------------------------------------------------------------------------


 





