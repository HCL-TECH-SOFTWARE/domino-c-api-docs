##### Symbolic Value : Database
##### DBOPTION_xxx - Database option flags.
---
```
#include <nsfdb.h>
```

**Symbolic Values :**

	DBOPTION_FT_INDEX	  -  Enable full text indexing.

	DBOPTION_IS_OBJSTORE	  -  TRUE if database is being used as an object store.

	DBOPTION_USES_OBJSTORE	  -  TRUE if database has notes which refer to an object store.

	DBOPTION_OBJSTORE_NEVER	  -  TRUE if notes in this database never use an object store.

	DBOPTION_IS_LIBRARY	  -  TRUE if database is a library.

	DBOPTION_UNIFORM_ACCESS	  -  TRUE if uniform access control should be enforced across all replicas.

	DBOPTION_OBJSTORE_ALWAYS	  -  TRUE if NoteUpdate of notes in this database should always try to use an object store.

	DBOPTION_NO_BGAGENT	  -  TRUE if database has no background agent.

	DBOPTION_OUT_OF_SERVICE	  -  TRUE if database is out-of-service, no new opens allowed.

	DBOPTION_IS_PERSONALJOURNAL	  -  TRUE if database is a personal journal.

	DBOPTION_MARKED_FOR_DELETE	  -  TRUE if database is marked for delete. No new opens are allowed; the database will be deleted when the reference count = 0.

	DBOPTION_HAS_CALENDAR	  -  TRUE if database stores calendar events.

	DBOPTION_IS_CATALOG_INDEX	  -  TRUE if database is a catalog index.

	DBOPTION_IS_ADDRESS_BOOK	  -  TRUE if database is an Address book or Domino Directory.

	DBOPTION_IS_SEARCH_SCOPE	  -  TRUE if database is a "multi-db-search" repository.

	DBOPTION_IS_UA_CONFIDENTIAL	  -  TRUE if database's user activity log is confidential, only.

	DBOPTION_RARELY_USED_NAMES	  -  TRUE if item names are to be treated as if the ITEM_RARELY_USED_NAME flag is set.

	DBOPTION_IS_SITEDB	  -  TRUE if db is a "multi-db-site" repository.


**Description :**

These option flags apply to the whole database.  These flags may be read using NSFDbGetOptions() and modified using NSFDbSetOptions().<br>
<br>
NSFDbGetOptions will not return the DBOPTION_OBJSTORE_xxx flags (even if any are set in the database) if the specified database is a remote database.  NSFDbSetOptions will not set the DBOPTION_OBJSTORE_xxx flags if the specified database is a remote database. 


**See Also :**
[NSFDbGetOptions](/domino-c-api-docs/reference/Func/NSFDbGetOptions)
[NSFDbSetOptions](/domino-c-api-docs/reference/Func/NSFDbSetOptions)
---
