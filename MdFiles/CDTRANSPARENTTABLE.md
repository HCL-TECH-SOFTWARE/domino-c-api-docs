




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Courier;
 panose-1:2 7 4 9 2 2 5 2 4 4;}
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




**Initial Release 4.5**



**Data Type : Composite Data**



**CDTRANSPARENTTABLE** **-** Bitmap
transparency table.


**----------------------------------------------------------------------------------------------------------**



**#include
<editods.h>**



**Definition :**



typedef struct {  

   LSIG Header;           /\* Signature and length \*/  

   WORD Reserved;         /\* Reserved for future use \*/  

   WORD TransparentCount; /\* Count of entries that follow


                            
(0-256) \*/  

/\* One or more transparent color table entries \*/  

} CDTRANSPARENTTABLE;


 


**Description :**



Bitmap
Transparency Table (optionally one per bitmap).  The colors in this table
specify the bitmap colors that are "transparent".  The pixels in the
bitmap whose colors are in this table will not affect the background; the
background will "bleed through" into the bitmap.  The entries in the
transparency table should be in the same format as entries in the color table. 
If a transparency table is used for a bitmap, it must immediately follow the
CDBITMAPHEADER.


 **See Also :**


**[SIG\_CD\_xxx](SIG_CD_xxx.md)**



----------------------------------------------------------------------------------------------------------


 





