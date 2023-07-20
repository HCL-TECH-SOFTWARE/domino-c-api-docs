##### Symbolic Value : File Attachment
##### NTEXT_xxx - NSFNoteExtractFileExt - wFlags
---
```
#include <nsfnote.h>
```

**Symbolic Values :**

	NTEXT_RESONLY	  -  If a Mac attachment, extract resource fork only (by default, only the data fork is extracted).

	NTEXT_FTYPE_MASK	  -  File type mask.

	NTEXT_FTYPE_FLAT	  -  Normal, one fork file.

	NTEXT_FTYPE_MACBIN	  -  MacBinaryII file.

	NTEXT_RAWMIME	  -  Do not decode MIME content transfer encoding.

	NTEXT_IGNORE_HUFF2	  -  Ignore checksum mismatch and save data anyway.


**Description :**

These symbols specify the possible values for the wFlags parameter of NSFNoteExtractFileExt and NSFNoteExtractWithCallback.


**See Also :**
[NSFNoteExtractFileExt](/domino-c-api-docs/reference/Func/NSFNoteExtractFileExt)
[NSFNoteExtractWithCallback](/domino-c-api-docs/reference/Func/NSFNoteExtractWithCallback)
---
