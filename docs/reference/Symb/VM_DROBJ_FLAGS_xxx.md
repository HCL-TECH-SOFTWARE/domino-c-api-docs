##### Symbolic Value : Navigators
##### VM_DROBJ_FLAGS_xxx - Navigator display flags
---
```
#include <vmods.h>
```

**Symbolic Values :**

	VM_DROBJ_FLAGS_VISIBLE	  -  The object is visible

	VM_DROBJ_FLAGS_SELECTABLE	  -  The object can be select (i.e. is not background)

	VM_DROBJ_FLAGS_LOCKED	  -  The object can't be edited

	VM_DROBJ_FLAGS_IMAGEMAP_BITMAP	  -  Stored only for objects of type SIG_CD_VMBITMAP. The bitmap was generated for display in Web browsers via a Domino server, and is not displayed when opened in Notes.


**Description :**

These flags control how a graphic object in a Navigator is displayed.  These flags are stored in the flags field of the common record headers (VMODSdrobj and VMODSbigobj) in the Navigator records (VIEWMAP_xxx_RECORD).


**See Also :**
[VMODSbigobj](/domino-c-api-docs/reference/Data/VMODSbigobj)
[VMODSdrobj](/domino-c-api-docs/reference/Data/VMODSdrobj)
---
