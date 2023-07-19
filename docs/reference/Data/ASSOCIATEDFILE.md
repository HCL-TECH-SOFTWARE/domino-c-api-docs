##### Data Type : File Attachment
##### ASSOCIATEDFILE - OLE Object - Associated file.
---
```
#include <oleods.h>
```

**Definition :**

typedef struct {
   WORD  wLength;          /* Size of this structure including both
                              fixed and variable sections */
   WORD  wcAssociatedFILE; /* Length of Associated $FILE name */
   WORD  wLinkType;        /* Unused, must be 0 */
   DWORD Reserved;         /* Unused, must be 0 */
/*
   Variable length portions go here in the following order:
   Associated $FILE name
*/
} ASSOCIATEDFILE;

**Description :**

An attached file associated with an embedded OLE 2 object.


**See Also :**
[ASSOCIATEDFILESDATA](/domino-c-api-docs/reference/Data/ASSOCIATEDFILESDATA)
---
