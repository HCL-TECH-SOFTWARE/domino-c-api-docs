




<!--
 /\* Font Definitions \*/
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




**Initial Release 6.0.2**



**Function : Conversion**



**ConvertNotesBitmapFree** **- Converts
a Domino Bitmap**


**----------------------------------------------------------------------------------------------------------**



**#include <misc.h>**



STATUS
LNPUBLIC **ConvertNotesBitmapFree(**  

      MEMHANDLE \*phConvertContext**);**



**Description :**



This
function is used to convert an image from the Domino bitmap format to another
format. Once a context has been created using ConvertNotesBitmapRead, the
conversion is processed using ConvertNotesBitmap. Then ConvertNotesBitmapFree
is called to close the context and free the resources allocated by the context.


 


**Parameters :**



Input :  

phConvertContext  -  Pointer to handle of context to be freed.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is.   

  

  




 **See Also :**


**[ConvertNotesBitmap](ConvertNotesBitmap.md)**


**[ConvertNotesBitmapRead](ConvertNotesBitmapRead.md)**


**[CONVERT\_NOTESBITMAP\_TO\_GIF](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/9E7655C69B89416A85256CFC006DE137)**


**[pConvertNBmpWriter](pConvertNBmpWriter.md)**



----------------------------------------------------------------------------------------------------------


 





