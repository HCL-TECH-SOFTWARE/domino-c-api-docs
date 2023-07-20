##### Symbolic Value : Rich Text
##### CDLAYER_VERSIONxxx - Appended to the beginning and end of a CDLAYER record.
---
```
#include <editods.h>
```

**Symbolic Values :**

	CDLAYER_VERSION1	  -  Version one.

	CDLAYER_VERSION2	  -  Version two. (In CDPOSITIONING record added BrowserLeftOffset and BrowserRightOffset in reserved space).


**Description :**

A CDLAYER record may be encapsulated within a CDBEGINRECORD and CDENDRECORD.  This version number is applied to the Version member within a CDBEGINRECORD and to the Version member within a CDENDRECORD.


**See Also :**
[CDBEGINRECORD](/domino-c-api-docs/reference/Data/CDBEGINRECORD)
[CDENDRECORD](/domino-c-api-docs/reference/Data/CDENDRECORD)
[CDLAYER](/domino-c-api-docs/reference/Data/CDLAYER)
---
