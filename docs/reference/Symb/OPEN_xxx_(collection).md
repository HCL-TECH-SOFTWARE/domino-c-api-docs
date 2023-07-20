##### Symbolic Value : Views
##### OPEN_xxx (collection) - NIFOpenCollection() - OpenFlags
---
```
#include <nif.h>
```

**Symbolic Values :**

	OPEN_REBUILD_INDEX	  -  Throw away existing index and rebuild it from scratch.

	OPEN_NOUPDATE	  -  Do not update index or unread list as part of the open.

	OPEN_DO_NOT_CREATE	  -  If collection object has not yet been created, do NOT create it automatically. Instead return a special internal error ERR_COLLECTION_NOT_CREATED.

	OPEN_SHARED_VIEW_NOTE	  -  Tells NIF to "own" the view note (which gets read while opening the collection) in memory, rather than the caller "owning" the view note by default. If this flag is specified on subsequent opens, and NIF currently owns a copy of the view note, it will just pass back the view note handle rather than re-reading it from disk/network. If specified, the the caller does NOT have to close the handle. If not specified, the caller gets a separate copy, and has to NSFNoteClose the handle when its done with it.

	OPEN_REOPEN_COLLECTION	  -  Force re-open of collection and thus, re-read of view note. Also implicitly prevents sharing of collection handle, and thus prevents any sharing of associated structures such as unread lists, etc..


**Description :**

These flags control the manner in which NIFOpenCollection opens a collection of notes.


**See Also :**
[NIFOpenCollection](/domino-c-api-docs/reference/Func/NIFOpenCollection)
---
