##### Function : Conversion
##### ConvertNotesBitmap - Converts a Domino Bitmap
---
```
#include <misc.h>
STATUS LNPUBLIC ConvertNotesBitmap(

	MEMHANDLE  hConvertContext,
	WORD  convertTo,
	DWORD  maxChunkSize,
	pConvertNBmpWriter  pWriter,
	void *pWriterCtx);
```
**Description :**

This function is used to convert an image from the Domino bitmap format to 
another format. Once a context has been created using ConvertNotesBitmapRead, 
the conversion is processed using ConvertNotesBitmap. Then 
ConvertNotesBitmapFree is called to close the context and free the resources 
allocated by the context.

**Parameters :**
Input :
hConvertContext  -  Handle to context created by ConvertNotesBitmapRead.

convertTo  -  CONVERT_NOTESBITMAP_TO_GIF

maxChunkSize  -  If zero, will pass entire bitmap in bytes parameter of pWriter function.

pWriter  -  User defined writer (callback function used to write the image data) of type pConvertNBmpWriter.

pWriterCtx  -  Context passed to the user defined writer.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. 



**See Also :**
[ConvertNotesBitmapFree](/domino-c-api-docs/reference/Func/ConvertNotesBitmapFree)
[ConvertNotesBitmapRead](/domino-c-api-docs/reference/Func/ConvertNotesBitmapRead)
[CONVERT_NOTESBITMAP_TO_GIF](/domino-c-api-docs/reference/Symb/CONVERT_NOTESBITMAP_TO_GIF)
[EnumCompositeBuffer](/domino-c-api-docs/reference/Func/EnumCompositeBuffer)
[pConvertNBmpWriter](/domino-c-api-docs/reference/Data/pConvertNBmpWriter)
---
