##### Symbolic Value : OLE
##### OLEREC_FLAG_xxx - OLE object definition flags.
---
```
#include <editods.h>
```

**Symbolic Values :**

	OLEREC_FLAG_OBJECT	  -  The data is an OLE embedded object.

	OLEREC_FLAG_LINK	  -  The data is an OLE link.

	OLEREC_FLAG_AUTOLINK	  -  If this is a link, it is an Automatic (hot) link.

	OLEREC_FLAG_MANUALLINK	  -  If this is a link, it is a Manual (warm) link.

	OLEREC_FLAG_NEWOBJECT	  -  This is a new object that was just inserted into the note.

	OLEREC_FLAG_PASTED	  -  This is a new object that was just pasted into the note.

	OLEREC_FLAG_SAVEOBJECTWHENCHANGED	  -  This object came from a form and should be saved every time it changes in the server.

	OELREC_FLAG_NOVISUALIZE	  -  This object was inherited from a form, or object incapable of rendering itself, so don't visualize it.


**Description :**

These flags are used to define the type of OLE object a note contains.  These flags are used by the Flags member of the CDOLEBEGIN data structure.


**See Also :**
[CDOLEBEGIN](/domino-c-api-docs/reference/Data/CDOLEBEGIN)
---
