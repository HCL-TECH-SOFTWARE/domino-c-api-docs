




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




 


**Function : Font**



**FontGetFaceID** **- Returns
the value of the FONTID's Face byte.**


**----------------------------------------------------------------------------------------------------------**



**#include <fontid.h>**



BYTE **FontGetFaceID(**  

      FONTID  fontid**);**



**Description :**



Returns the
value of the FONTID's Face byte. This may be one of the standard type faces
defined by FONT\_FACE\_xxx or a font ID resolved by a font table.  Implemented as
a macro:  

  

#define FontGetFaceID(fontid) ((BYTE)(((fontid) >> FONT\_FACE\_SHIFT) &
0xff))


 


**Parameters :**



Input :  

fontid  -  The FONTID from which to read the Face byte.  

  




Output :  

(routine)  -  The value of the FONTID's Face byte.  

  

  




 **See Also :**


**[CDFONTTABLE](CDFONTTABLE.md)**


**[FONTID](FONTID.md)**


**[FONTIDFIELDS](FONTIDFIELDS.md)**


**[FontSetFaceID](FontSetFaceID.md)**


**[FONT\_FACE\_xxx](FONT_FACE_xxx.md)**



----------------------------------------------------------------------------------------------------------


 





