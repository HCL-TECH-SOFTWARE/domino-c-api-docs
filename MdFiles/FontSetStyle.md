




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



**FontSetStyle** **- Sets the
FONTID's Attrib byte as specified in the styleid argument.**


**----------------------------------------------------------------------------------------------------------**



**#include <fontid.h>**



FONTID **FontSetStyle(**  

      FONTID  fontid,  

      DWORD  styleid**);**



**Description :**



Sets all of
the font's style characteristics (ITALIC, BOLD, etc) as specified in the
styleid argument by setting the FONTID's Attrib byte appropriately. The values
the Attrib byte can take are defined by the symbolic definition ISxxx., so the
styleid argument should consist of one or more of those values bitwise OR-ed
together.  Implemented as a macro:  

  

#define
FontSetStyle(fontid,styleid) (((DWORD)(fontid) &
~BYTEMASK(FONT\_STYLE\_SHIFT)) | ((DWORD)(styleid)<<FONT\_STYLE\_SHIFT))


 


**Parameters :**



Input :  

fontid  -  The FONTID in which to set the Attrib byte.  

  

styleid  -  ID of the style to set.  

  




Output :  

(routine)  -  The specified FONTID with the Attrib byte set appropriately.  

  

  

fontid  -  The specified FONTID with the style attributes appropriately set.  

  




 **Sample Usage :**


pCDText->FontID =
FontSetStyle(pCDText->FontID, ISBOLD | ISITALIC | ISUNDERLINE);


 **See Also :**


**[FontGetStyle](FontGetStyle.md)**


**[FONTID](FONTID.md)**


**[FONTIDFIELDS](FONTIDFIELDS.md)**


**[ISxxx](ISxxx.md)**



----------------------------------------------------------------------------------------------------------


 





