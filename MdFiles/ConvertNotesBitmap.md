




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



**ConvertNotesBitmap** **- Converts
a Domino Bitmap**


**----------------------------------------------------------------------------------------------------------**



**#include <misc.h>**



STATUS
LNPUBLIC **ConvertNotesBitmap(**  

      MEMHANDLE  hConvertContext,  

      WORD  convertTo,  

      DWORD  maxChunkSize,  

      pConvertNBmpWriter  pWriter,  

      void \*pWriterCtx**);**



**Description :**



This
function is used to convert an image from the Domino bitmap format to another
format. Once a context has been created using ConvertNotesBitmapRead, the
conversion is processed using ConvertNotesBitmap. Then ConvertNotesBitmapFree
is called to close the context and free the resources allocated by the context.


 


**Parameters :**



Input :  

hConvertContext  -  Handle to context created by ConvertNotesBitmapRead.  

  

convertTo  -  CONVERT\_NOTESBITMAP\_TO\_GIF  

  

maxChunkSize  -  If zero, will pass entire bitmap in bytes parameter of pWriter
function.  

  

pWriter  -  User defined writer (callback function used to write the image
data) of type pConvertNBmpWriter.  

  

pWriterCtx  -  Context passed to the user defined writer.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is.   

  

  




 **See Also :**


**[ConvertNotesBitmapFree](ConvertNotesBitmapFree.md)**


**[ConvertNotesBitmapRead](ConvertNotesBitmapRead.md)**


**[CONVERT\_NOTESBITMAP\_TO\_GIF](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/9E7655C69B89416A85256CFC006DE137)**


**[EnumCompositeBuffer](EnumCompositeBuffer.md)**


**[pConvertNBmpWriter](pConvertNBmpWriter.md)**



----------------------------------------------------------------------------------------------------------


 





