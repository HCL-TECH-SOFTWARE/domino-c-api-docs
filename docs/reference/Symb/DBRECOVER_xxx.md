##### Symbolic Value : Backup
##### DBRECOVER_xxx - Flags to control how databases are recovered.
---
```
#include <nsfdb.h>
```

**Symbolic Values :**

	DBRECOVER_WAIT	  -  Indicates the recovery should wait for resources to become available, instead of returning with a error of ERR_RM_SCAN_IN_PROGRESS. The most common busy resource is another recovery in progress.

	DBRECOVER_ZAP_ID	  -  Indicates the databases instance id (DBIID) should be refreshed with a new value after the recovery, thus allowing access to the original DB as well as this recovered version. This is a new instance, i.e. you will have to create a new backup after the recovery if you want the ability to recover the new instance.

	DBRECOVER_REFRESH_BACKUP	  -  Indicates you want to "roll-forward" the backup but keep it as a backup. This would be used to keep backups current if the cost of doing the backup is higher than the cost of a refresh. This option cannot be used with DBRECOVER_ZAP_ID.

	DBRECOVER_POINT_IN_TIME	  -  Indicates you want recover a database, not to the current time but to a selected time passed in the recoveryTime parameter. All updates completed prior to the selected time will appear in the recovered database but no latter ones. This option will always assign a new DBIID (see DBRECOVER_ZAP_ID). This option cannot be used with DBRECOVER_REFRESH_BACKUP.

	DBRECOVER_ZAP_REPLICAID	  -  Indicates you want the replica ID to be reset on the recovered database so it is will not conflict with the original database when replicating. This option will always assign a new DBIID (see DBRECOVER_ZAP_ID). This option cannot be used with DBRECOVER_REFRESH_BACKUP.

	DBRECOVER_ZAP_ID_IF_NECESSARY	  -  Make recovered DB a new instance if another copy of the DB with the same instance ID is on-line. Otherwise use the same instance ID, thus avoiding the need for creating a new backup.

	DBRECOVER_ALT_RETRIEVE_PATH	  -  Enables restoration of previously archived transaction log extent files to an alternate location during Media Recovery, when ARCHIVE style transaction logging is being used. Normally, the archived transaction log extent files are restored directly to the transaction log directory. Use of this flag can improve performance during database recovery . When this flag is specified, the LogSegmentPathName parameter of the LOGRESTORECALLBACKFUNCTION is filled in with the path location where previously archived extents are to be placed. The code which calls NSFRecoverDatabases should specifiy this location by setting the TRANSLOG_RECOVER_PATH value in NOTES.INI . 

Note: Although a path relative to the Domino directory is valid, to avoid ambiguity, specifying an absolute path for the TRANSLOG_RECOVER_PATH value is recommended.


**Description :**

Flags to control how databases are recovered using NSFRecoverDatabases.


**See Also :**
[NSFRecoverDatabases](/domino-c-api-docs/reference/Func/NSFRecoverDatabases)
---
