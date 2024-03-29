##### Function : Conversion
##### ConvertNotesBitmapFree - Converts a Domino Bitmap
---
```
#include <misc.h>
STATUS LNPUBLIC ConvertNotesBitmapFree(

	MEMHANDLE *phConvertContext);
```
**Description :**

This function is used to convert an image from the Domino bitmap format to 
another format. Once a context has been created using ConvertNotesBitmapRead, 
the conversion is processed using ConvertNotesBitmap. Then 
ConvertNotesBitmapFree is called to close the context and free the resources 
allocated by the context.

**Parameters :**
Input :
phConvertContext  -  Pointer to handle of context to be freed.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. 



**See Also :**
[ConvertNotesBitmap](/domino-c-api-docs/reference/Func/ConvertNotesBitmap)
[ConvertNotesBitmapRead](/domino-c-api-docs/reference/Func/ConvertNotesBitmapRead)
[CONVERT_NOTESBITMAP_TO_GIF](/domino-c-api-docs/reference/Symb/CONVERT_NOTESBITMAP_TO_GIF)
[pConvertNBmpWriter](/domino-c-api-docs/reference/Data/pConvertNBmpWriter)
---
