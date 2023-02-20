##### Function : Conversion
##### ConvertNotesBitmapRead - Converts a Domino Bitmap
---
```
#include <misc.h>
STATUS LNPUBLIC ConvertNotesBitmapRead(

	MEMHANDLE *phConvertContext,
	WORD  cdSignature,
	char far *pCDRecord,
	DWORD  recordLength);
```
**Description :**

This function is used to convert an image from the Domino bitmap format to 
another format. Once a context has been created using ConvertNotesBitmapRead, 
the conversion is processed using ConvertNotesBitmap. Then 
ConvertNotesBitmapFree is called to close the context and free the resources 
allocated by the context.

**Parameters :**
Input :
phConvertContext  -  Pointer to handle of conversion context. Should be initialized to NULLMEMHANDLE prior to first call.  Holds context data for future read calls and the conversion call. User must free this when no longer needed using ConvertNotesBitmapFree.

cdSignature  -  Signature of CD record to read. Should be one of the following and the first record should be the bitmap header:
       SIG_CD_BITMAPHEADER
       SIG_CD_BITMAPSEGMENT
       SIG_CD_COLORTABLE
       SIG_CD_PATTERNTABLE
       SIG_CD_TRANSPARENTTABLE

pCDRecord  -  Pointer to the current record data.

recordLength  -  Length of data.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. 



**See Also :**
[ConvertNotesBitmap](/reference/Func/ConvertNotesBitmap)
[ConvertNotesBitmapFree](/reference/Func/ConvertNotesBitmapFree)
[CONVERT_NOTESBITMAP_TO_GIF](/reference/Symb/CONVERT_NOTESBITMAP_TO_GIF)
[pConvertNBmpWriter](/reference/Data/pConvertNBmpWriter)
---
