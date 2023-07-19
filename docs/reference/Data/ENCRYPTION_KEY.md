##### Data Type : Note
##### ENCRYPTION_KEY - Decryption key for file attachment objects.
---
```
#include <nsfnote.h>
```

**Definition :**

typedef struct {                        
   BYTE Byte1;             
   WORD Word1;             
   BYTE Text[16];
} ENCRYPTION_KEY;

**Description :**

This structure is returned from NSFNoteDecrypt and can be used to decrypt file attachment objects in NSFNoteExtractFile and NSFNoteExtractFileExt.  File attachment objects are not decrypted until necessary.


**See Also :**
[NSFNoteDecrypt](/domino-c-api-docs/reference/Func/NSFNoteDecrypt)
[NSFNoteExtractFile](/domino-c-api-docs/reference/Func/NSFNoteExtractFile)
[NSFNoteExtractFileExt](/domino-c-api-docs/reference/Func/NSFNoteExtractFileExt)
---
