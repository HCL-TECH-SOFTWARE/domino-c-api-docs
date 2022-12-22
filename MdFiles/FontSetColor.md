




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




 


**Function : Font**



**FontSetColor** **- Sets the
FONTID's Color byte to the color specified in the colorid argument.**


**----------------------------------------------------------------------------------------------------------**



**#include <fontid.h>**



FONTID **FontSetColor(**  

      FONTID  fontid,  

      BYTE  colorid**);**



**Description :**



Sets the
FONTID's Color byte to the color specified in the colorid argument. The colorid
argument should be one of the values defined by NOTES\_COLOR\_xxx.  Implemented
as a macro:  

  

#define
FontSetColor(fontid,colorid) (((DWORD)(fontid) &
~BYTEMASK(FONT\_COLOR\_SHIFT)) | ((DWORD)(colorid)<<FONT\_COLOR\_SHIFT))


 


**Parameters :**



Input :  

fontid  -  The FONTID in which the Color byte is to be set.  

  

colorid  -  The symbolic value defined in NOTES\_COLOR\_xxx for the desired
color.  

  




Output :  

(routine)  -  The specified FONTID with the Color byte set appropriately.  

  

  




 **See Also :**


**[FontGetColor](FontGetColor.md)**


**[FONTID](FONTID.md)**


**[FONTIDFIELDS](FONTIDFIELDS.md)**


**[FontSetColor](FontSetColor.md)**


**[NOTES\_COLOR\_xxx](NOTES_COLOR_xxx.md)**



----------------------------------------------------------------------------------------------------------


 





