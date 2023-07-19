##### Data Type : Rich Text
##### ACTIVEOBJECTSTORAGELINK - Active object storage specification.
---
```
#include <editods.h>
```

**Definition :**

typedef struct {
   WORD  Length;   /* Length of the attachment name following */
   WORD  LinkType; /* Currently not used */
   DWORD Reserved;
/* Variable length string follows (not null terminated).  This
   string is the name of an attachment which contains data (e.g.,
   a .class file) used by the active object. */
} ACTIVEOBJECTSTORAGELINK;

**Description :**

Java code used for active object hotspots is stored in $FILE items.  The file name for the $FILE item containing a class file is specified in this record.  This record only appears following an ACTIVEOBJECT record, and is part of a CDHOTSPOTBEGIN record.  The fields of an ACTIVEOBJECTSTORAGELINK record are:
<ul><br>

<ul>Length		Length of the file attachment name.<br>
LinkType	Reserved;  must be 0.<br>
Reserved	Reserved;  must be 0.</ul>
<br>
This record is followed by the name of the $FILE attachment, in LMBCS format with no NULL delimiter.</ul>



**See Also :**
[ACTIVEOBJECT](/domino-c-api-docs/reference/Data/ACTIVEOBJECT)
[CDHOTSPOTBEGIN](/domino-c-api-docs/reference/Data/CDHOTSPOTBEGIN)
---
