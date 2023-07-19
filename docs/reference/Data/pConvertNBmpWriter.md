##### Data Type : Conversion
##### pConvertNBmpWriter - Convert Bitmap writer function
---
```
#include <misc.h>
```

**Definition :**

typedef STATUS (LNCALLBACKPTR pConvertNBmpWriter) (void *pWriterCtx, /* user 
defined writer context */
	          BYTE *bytes,  /* data bytes */
	          DWORD byteCount, /* maxChunkSize or totalImageSizeInBytes */
	          DWORD totalImageSizeInBytes);

**Description :**

This is the datatype of the Callback function passed to function ConvertNotesBitmap.


**See Also :**
[ConvertNotesBitmap](/domino-c-api-docs/reference/Func/ConvertNotesBitmap)
---
