




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



**FontSetFaceID** **- Sets the
FONTID's Face byte to the typeface specified in the faceid argument.**


**----------------------------------------------------------------------------------------------------------**



**#include <fontid.h>**



FONTID **FontSetFaceID(**  

      FONTID  fontid,  

      BYTE  faceid**);**



**Description :**



Sets the
FONTID's Face byte to the typeface specified in the faceid argument. The faceid
argument should be one of the values defined by FONT\_FACE\_xxx.  Implemented as
a macro:  

  

#define FontSetFaceID(fontid,faceid) (((DWORD)(fontid) &
~BYTEMASK(FONT\_FACE\_SHIFT)) | ((DWORD)(faceid)<<FONT\_FACE\_SHIFT))


 


**Parameters :**



Input :  

fontid  -  The FONTID  in which the Face byte is to be set.  

  

faceid  -  The typeface to which the Face byte is to be set.  

  




Output :  

(routine)  -  The specified FONTID with the Face byte set appropriately.  

  

  




 **See Also :**


**[FontGetFaceID](FontGetFaceID.md)**


**[FONTID](FONTID.md)**


**[FONTIDFIELDS](FONTIDFIELDS.md)**


**[FONT\_FACE\_xxx](FONT_FACE_xxx.md)**



----------------------------------------------------------------------------------------------------------


 





