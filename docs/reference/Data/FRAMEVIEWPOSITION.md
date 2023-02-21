##### Data Type : IDs
##### FRAMEVIEWPOSITION - Contains the UNID of the currently selected outline entry.
---
```
#include <fsods.h>
```
**Description :**

This structure is used ONLY in the bookmarks database.  It contains one entry 
per FRAME/FRAMESET.  At the end of all the frame information is a set of  these 
structures which contain the UNID (as a string of maximum length MAXUNIDSTRING) 
for the current position in the outline for that frame if there is one.  If 
not, the UNID is null.

**See Also :**
[CDFRAME](/domino-c-api-docs/reference/Data/CDFRAME)
[CDFRAMESET](/domino-c-api-docs/reference/Data/CDFRAMESET)
[MAXUNIDSTRING](/domino-c-api-docs/reference/Symb/MAXUNIDSTRING)
---
