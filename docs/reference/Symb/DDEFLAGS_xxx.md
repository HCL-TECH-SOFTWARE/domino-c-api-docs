##### Symbolic Value : DDE
##### DDEFLAGS_xxx - Specifies DDE link type.
---
```
#include <editods.h>
```

**Symbolic Values :**

	DDEFLAGS_AUTOLINK	  -  Link type == Automatic (hot).

	DDEFLAGS_MANUALLINK	  -  Link type == Manual (warm).

	DDEFLAGS_EMBEDDED	  -  Embedded document exists.

	DDEFLAGS_INITIATE	  -  Used on paste to indicate not to prompt user to initiate link.

	DDEFLAGS_CDP	  -  Used on paste to indicate that server uses Compound Document protocol.

	DDEFLAGS_NOTES_LAUNCHED	  -  Used on CDP paste/load to indicate that Notes launched the application to establish original conversation.

	DDEFLAGS_CONV_ACTIVE	  -  Used on non-CDP paste/load to indicate that conversation is already active.

	DDEFLAGS_EMBEDEXTRACTED	  -  Used on non-CDP paste/load to indicate that Notes extracted the embedded file so that it may later be closed.

	DDEFLAGS_NEWOBJECT	  -  Set if this DDE Range is a new inserted object which contains no embedded object yet, i.e. a "blank" object.


**Description :**

These values specify the DDE link flag used in the structure, CDDDEBEGIN.


**See Also :**
[CDDDEBEGIN](/domino-c-api-docs/reference/Data/CDDDEBEGIN)
---
