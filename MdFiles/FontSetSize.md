




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



**FontSetSize** **- Sets the
FONTID's PointSize byte to the specified value.**


**----------------------------------------------------------------------------------------------------------**



**#include <fontid.h>**



FONTID **FontSetSize(**  

      FONTID  fontid,  

      DWORD  size**);**



**Description :**



Implemented
as a macro:  

  

#define FontSetSize(fontid,size) (((DWORD)(fontid) &
~BYTEMASK(FONT\_SIZE\_SHIFT)) | ((DWORD)(size)<<FONT\_SIZE\_SHIFT))


 


**Parameters :**



Input :  

fontid  -  The FONTID in which to set the PointSize byte.  

  

size  -  The size (in points) to which  the FONTID's PointSize byte is to be
set.  

  




Output :  

(routine)  -  The specified FONTID with the PointSize set to the specified
value.  

  

  




 **See Also :**


**[FontGetSize](FontGetSize.md)**


**[FONTID](FONTID.md)**


**[FONTIDFIELDS](FONTIDFIELDS.md)**



----------------------------------------------------------------------------------------------------------


 





