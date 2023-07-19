##### Data Type : File Attachment
##### FILEOBJECT_HPFSEXT - Extension to FILEOBJECT structure for files in HPFS format.
---
```
#include <nsfdata.h>
```

**Definition :**

typedef struct {
   DWORD EAStart; /* offset into the object at which EAs begin */
   DWORD EALen;   /* length of EA section */
   DWORD Spare;   /* 0 */
} FILEOBJECT_HPFSEXT;

**Description :**

This structure specifies the extended attributes (EAs) for a file attachment that is in HPFS (High Performance File System) format.  If the HostType member of a FILEOBJECT structure is set to HOST_HPFS, then the FILEOBJECT structure is followed by a FILEOBJEC_HPFSEXT structure.


**See Also :**
[FILEOBJECT](/domino-c-api-docs/reference/Data/FILEOBJECT)
---
