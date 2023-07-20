##### Symbolic Value : Clusters
##### DBOPEN_xxx - Database open options.
---
```
#include <nsfdb.h>
```

**Symbolic Values :**

	DBOPEN_WITH_SCAN_LOCK	  -  Open with scan lock to prevent other opens that also use this flag from opening the database (used by replicator). This is not file locking, and only works with processes that cooperate by specifying the same flag.

	DBOPEN_PURGE	  -  When opening the database, purge any deleted document place-holders (deleted note stubs) that are older than the DBREPLICAINFO.Cutoff date and, if the REPLFLG_CUTOFF_DELETE DBREPLICAINFO.Flag is set, purge documents that have not been modified since the DBREPLICAINFO.Cutoff date. This flag will prevent the replicator from opening the specified database.

	DBOPEN_NO_USERINFO	  -  When a C API application calls NSFDbOpenExtended with this option set, and an Extension Manager is running on a client or server that traps this call (EM_NSFDBOPENEXTENDED), the Extension Manager will receive a NULL User Name when calling NSFDbUserNameGet.

	DBOPEN_FORCE_FIXUP	  -  Force a database fixup, even if the file was properly closed previously. This flag is not necessary if the database was improperly closed, since Domino and Notes will automatically verify the database contents of improperly closed databases. This process involves three steps: 1) Perform a consistancy check that compares the database's header information against the on-disk image of the database and if possible, repair any discrepancies found. 2) Perform a document by document consistancy check of the entire database, that compares each note's header information against its on-disk image and if possible, repair any discrepancies found. 3) Delete all bad documents/notes that could not be corrected during the consistancy check.NSFDbOpenExtended with DBOPEN_FORCE_FIXUP will not succeed if db_name specifies a directory. This flag will prevent the replicator from opening the specified database.

	DBOPEN_FIXUP_FULL_NOTE_SCAN	  -  Scan all notes and all items for validity.Note: NSFDbOpenExtended with DBOPEN_FIXUP_FULL_NOTE_SCAN will not succeed if db_name specifies a directory.

	DBOPEN_FIXUP_NO_NOTE_DELETE	  -  Do not delete bad notes during note scan (skip step 4.3).Note: NSFDbOpenExtended with DBOPEN_FIXUP_NO_NOTE_DELETE will not succeed if db_name specifies a directory.

	DBOPEN_CLUSTER_FAILOVER	  -  If open fails, failover to another server in the same cluster that has a replica copy of this database. If the input server is not a member of a cluster or if the database is not replicated on other servers in the cluster, then this flag will have no effect.

	DBOPEN_CLOSE_SESS_ON_ERROR	  -  Disconnect the remote LAN or WAN connection to the server containing the database if the NSFDbOpenExtended call fails for any reason. This flag should only be used in the case where there is only one database to be accessed on a remote server. It is useful with a dialup connection -- the phone connection will be dropped right away if an error occurs connecting to the remote database.

	DBOPEN_NOLOG	  -  Do not log any errors that occur while accessing this database. This flag should only be used when opening the log database.


**Description :**

Database open options controlling Domino based file locking (scan lock), the removal of deleted note stubs, the removal of documents whose last modified date is past the replication cutoff date (and whose REPLFLG_CUTOFF_DELETE replication flag is set), the forcing of an Access Control List (ACL) check during local database access, and initiation of a database fixup covering various levels of detail.<br>
<br>
These flags can only be specified with NSFDbOpenExtended, and not with NSFDbOpen.


**See Also :**
[NSFDbOpenExtended](/domino-c-api-docs/reference/Func/NSFDbOpenExtended)
---
