##### Symbolic Value : Database
##### DBCREATE_xxx - NSFDbCreateExtended - Options
---
```
#include <nsfdb.h>
```

**Symbolic Values :**

	DBCREATE_LOCALSECURITY	  -  Create a locally encrypted database.

	DBCREATE_OBJSTORE_NEVER	  -  NSFNoteUpdate will not use an object store for notes in the database.

	DBCREATE_MAX_SPECIFIED	  -  The maximum database length is specified in bytes in NSFDbCreateExtended.

	DBCREATE_NORESPONSE_INFO	  -  Don't support note hierarchy - ODS21 and up only

	DBCREATE_NOUNREAD	  -  Don't maintain unread lists for this DB

	DBCREATE_NO_FREE_OVERWRITE	  -  Skip overwriting freed disk buffer space

	DBCREATE_FORM_BUCKET_OPT	  -  Maintain form/bucket bitmap

	DBCREATE_DISABLE_TXN_LOGGING	  -  Disable transaction logging for this database if specified

	DBCREATE_MAINTAIN_LAST_ACCESSED	  -  Enable maintaining last accessed time

	DBCREATE_IS_MAILBOX	  -  TRUE if database is a mail[n].box database

	DBCREATE_LARGE_UNKTABLE	  -  TRUE if database should allow "large" (>64K bytes) UNK table


**Description :**

Database creation options.


**See Also :**
[NSFDbCreateExtended](/domino-c-api-docs/reference/Func/NSFDbCreateExtended)
---
