##### Symbolic Value : Mail
##### DBCOMPACT_xxx - Optional values for the Options parameter of NSFDbCompact and NSFDbCompactExtended.
---
```
#include <nsfdb.h>
```

**Symbolic Values :**

	DBCOMPACT_NO_INDEXES	  -  Don't preserve view indexes

	DBCOMPACT_NO_LOCKOUT	  -  Don't lock out database users

	DBCOMPACT_REVERT_ODS	  -  Revert current ODS to the previous ODS version

	DBCOMPACT_MAX_4GB	  -  Create new file with 4GB file size limit

	DBCOMPACT_MAILBOX	  -  Compact a mail.box file for mail router and other MTAs

	DBCOMPACT_NO_INPLACE	  -  Don't do in-place compaction

	DBCOMPACT_DISABLE_UNREAD	  -  Disable unread marks in destination database

	DBCOMPACT_ENABLE_UNREAD	  -  Reenable unread marks in destination database (default)

	DBCOMPACT_DISABLE_RESPONSE_INFO	  -  Disable response info in resulting database

	DBCOMPACT_ENABLE_RESPONSE_INFO	  -  Reenable response info in resulting database (default)

	DBCOMPACT_ENABLE_FORM_BKT_OPT	  -  Enable form/bucket bitmap optimization

	DBCOMPACT_DISABLE_FORM_BKT_OPT	  -  Disable form/bucket bitmap optimization (default)

	DBCOMPACT_IGNORE_ERRORS	  -  Ignore errors encountered during compaction. That is, make best effort to get something at the end.

	DBCOMPACT_RECOVER_SPACE_ONLY	  -  If set, do only bitmap correction if in-place can be done.

	DBCOMPACT_ARCHIVE	  -  Archive/delete, then compact the database.

	DBCOMPACT_ARCHIVE_ONLY	  -  Just archive/delete, no need to compact.

	DBCOMPACT_RECOVER_ALL_SPACE	  -  If set, always do full space recovery compaction.


**Description :**

Optional values for the Options parameter of NSFDbCompact and NSFDbCompactExtended. Use DBCOMPACT_MAILBOX for NSFDbCompact and the others for NSFDbCompactExtended.


**See Also :**
[NSFDbCompact](/domino-c-api-docs/reference/Func/NSFDbCompact)
[NSFDbCompactExtended](/domino-c-api-docs/reference/Func/NSFDbCompactExtended)
---
