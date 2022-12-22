




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



**BYTEMASK** **- Create a
mask byte in a DWORD, to be used to reference the bytes in a FONTID.**


**----------------------------------------------------------------------------------------------------------**



**#include <fontid.h>**



DWORD **BYTEMASK(**  

      DWORD  leftshift**);**



**Description :**



Returns a
DWORD containing a byte mask in one of its bytes. The byte mask may then be
used to reference the bytes in a FONTID.    

  

Implemented as a macro:  

  

#define
BYTEMASK(leftshift) ((DWORD)((DWORD)0x000000ff << (leftshift)))


 


**Parameters :**



Input :  

leftshift  -  The number of bits the number 0x000000ff must be left-shifted to
create the desired byte mask.  Use one of the values defined in FONT\_xxx\_SHIFT
to generate a mask for one of the bytes in a FONTID.  

  




Output :  

(routine)  -  A DWORD in which one of the bytes has all its bits set, and all
the bits in the other bytes are cleared.  

  

  




 **Sample Usage :**


#define
FontSetColor(fontid,colorid) (((DWORD)(fontid) &
~BYTEMASK(FONT\_COLOR\_SHIFT)) | ((DWORD)(colorid)<<FONT\_COLOR\_SHIFT))


 **See Also :**


**[FontSetColor](FontSetColor.md)**


**[FontSetFaceID](FontSetFaceID.md)**


**[FontSetSize](FontSetSize.md)**


**[FontSetStyle](FontSetStyle.md)**


**[FONT\_xxx\_SHIFT](FONT_xxx_SHIFT.md)**



----------------------------------------------------------------------------------------------------------


 





