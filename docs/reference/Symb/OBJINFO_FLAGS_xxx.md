##### Symbolic Value : OLE
##### OBJINFO_FLAGS_xxx - OLE object information flags
---
```
#include <oleods.h>
```

**Symbolic Values :**

	OBJINFO_FLAGS_SCRIPTED	  -  Object is scripted.

	OBJINFO_FLAGS_RUNREADONLY	  -  Object is run in read-only mode.

	OBJINFO_FLAGS_CONTROL	  -  Object is a control.

	OBJINFO_FLAGS_FITTOWINDOW	  -  Object is sized to fit to window.

	OBJINFO_FLAGS_FITBELOWFIELDS	  -  Object is sized to fit below fields.

	OBJINFO_FLAGS_UPDATEFROMDOCUMENT	  -  Object is to be updated from document.

	OBJINFO_FLAGS_INCLUDERICHTEXT	  -  Object is to be updated from document.

	OBJINFO_FLAGS_ISTORAGE_ISTREAM	  -  Object is stored in IStorage/IStream.

	OBJINFO_FLAGS_HTMLDATA	  -  Object has HTML data. In this case, the CDOLEOBJ_INFO structure is followed by OLEOBJHTMLDATA which is followed by a number of OLEOBJHTMLEVENT strucutures, followed by a number of OLEHTMLPARAM structures.


**Description :**

These flags are stored in the Flags field of the CDOLEOBJ_INFO record.


**See Also :**
[CDOLEOBJ_INFO](/domino-c-api-docs/reference/Data/CDOLEOBJ_INFO)
---
