##### Data Type : File Attachment
##### FILEOBJECT_MACEXT - Extension to FILEOBJECT structure for files in Macintosh format.
---
```
#include <nsfdata.h>
```

**Definition :**
```
typedef struct {
   char  FileCreator[4];  /* application that created the file */
   char  FileType[4];     /* type of file */
   DWORD ResourcesStart;  /* offset into the object at which resources
                             begin */
   DWORD ResourcesLen;    /* length of the resources section in bytes */
   WORD  CompressionType; /* compression used for Mac resources */
   DWORD Spare;           /* 0 */
} FILEOBJECT_MACEXT;
```

**Description :**

This structure specifies additional information for a file attachment in Macintosh format.  If the HostType member of a FILEOBJECT structure is set to HOST_MAC, then the FILEOBJECT structure is followed by a FILEOBJECT_MAC structure.


**See Also :**
[FILEOBJECT](/domino-c-api-docs/reference/Data/FILEOBJECT)
---
