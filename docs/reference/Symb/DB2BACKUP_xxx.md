##### Symbolic Value : Backup
##### DB2BACKUP_xxx - NSFDB2 reconnect flags.
---
```
#include <nsfdb.h>
```

**Symbolic Values :**

	DB2BACKUP_FASTCONNECT	  -  Does not attempt to regenerate access views, tables, and add function and trigger definitions for access tables and views. This is useful if the caller knows that this work is unnecessary as the row data hasn't changed since the NSFDB2 database was taken offline.

	DB2BACKUP_NEWREPLICA	  -  Modifies replica ID of targetNSF in an effort to permanently disable replication for this Notes database.

	DB2BACKUP_COPY_REPLACE	  -  Indicates that the caller is intentionally going to erase and replace the table data currently in use for targetNSF. Otherwise, if targetNSF exists, the error ERR_DB2NSF_SCHEMA_INUSE will be returned.


	DB2BACKUP_COPY_DELETE_SRC	  -  Deletes NSFDB2 data for sourceNSF and removes the reference to the NSFDB2 database.

	DB2BACKUP_COPY_ISOLATE	  -  The groupName argument is ignored. targetNSF is placed in its own NSFDB2 group. The group (tablespace) name will be generated.

	DB2BACKUP_COPY_CLOSE	  -  Closes the NSFDB2 "database group" now containing targetNSF such that it can no longer receive additional NSFDB2 databases. This can be used in conjunction with groupName to effectively move or copy an NSFDB2 database into a DB2 tablespace (NSFDB2 group) by itself.

	DB2BACKUP_COPY_NONRECOVERABLE	  -  Performs a non-recoverable load into targetNSF. The load will be recoverable by default. See loadCopyLocation.

	DB2BACKUP_COPY_IGNORE_NIF	  -  Do not copy table data associated with views (NIF).

	DB2BACKUP_COPY_VENDOR_LOAD	  -  Use this option to treat loadParameter as the vendor supplied DB LOAD module.

	DB2BACKUP_NONSFID	  -  Pass this to NSFDB2ReconnectNotesDatabase to defer to the NSFID matching the FullPath stored in the properties table of the tablespace instead of the NSFID passed to this function.


**Description :**

These values are optional values for the flags parameter of NSFDB2ReconnectNotesDatabase.  


**See Also :**
[NSFDB2FastCopy](/domino-c-api-docs/reference/Func/NSFDB2FastCopy)
[NSFDB2ReconnectNotesDatabase](/domino-c-api-docs/reference/Func/NSFDB2ReconnectNotesDatabase)
---
