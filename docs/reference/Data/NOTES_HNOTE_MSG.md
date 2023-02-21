##### Data Type : Notes/FX data
##### NOTES_HNOTE_MSG - Notes/FX data sent by  OLE server to Notes to update an embedded object.
---
```
#include <olenotes.h>
```
**Description :**

This is the structure of the Notes/FX data that an OLE server's GetData method 
sends to Notes to update an object embedded in a note. The hNote parameter is 
the handle of a copy of the hFXNote that Notes sent to the OLE server 
application in a previous NOTES_DOC_INFO_MSG.

**Sample Usage :**
```
 
```
**See Also :**
[DOC_FLAGS_xxx](/domino-c-api-docs/reference/Symb/DOC_FLAGS_xxx)
[DOC_OPENMODE_xxx](/domino-c-api-docs/reference/Symb/DOC_OPENMODE_xxx)
[NOTES_DOC_INFO_VERSIONxxx](/domino-c-api-docs/reference/Symb/NOTES_DOC_INFO_VERSIONxxx)
[NSFDbReopen](/domino-c-api-docs/reference/Func/NSFDbReopen)
[USER_ACCESS_xxx](/domino-c-api-docs/reference/Symb/USER_ACCESS_xxx)
---
