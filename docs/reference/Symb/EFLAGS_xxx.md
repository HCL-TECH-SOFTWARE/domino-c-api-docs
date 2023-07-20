##### Symbolic Value : File Attachment
##### EFLAGS_xxx - Additional NSFNoteAttachFile encoding types.
---
```
#include <nsfdata.h>
```

**Symbolic Values :**

	EFLAGS_MASK	  -  Bit mask specifiying the possible EFLAGS_xxx values.

	EFLAGS_INDOC	  -  Set the FILEFLAG_INDOC flag in the Flags member of the FILEOBJECT structure.

	EFLAGS_KEEPPATH	  -  Don't strip off path in the filename.

	EFLAGS_AUTOCOMPRESSED	  -  Set the FILEFLAG_AUTOCOMPRESSED flag in the Flags member of the FILEOBJECT structure.


**Description :**

These values may optionally be bitwised OR'd in the encoding_type parameter of NSFNoteAttachFile.


**See Also :**
[NSFNoteAttachFile](/domino-c-api-docs/reference/Func/NSFNoteAttachFile)
---
