##### Symbolic Value : Database
##### REPLFLG_xxx - Replication Flags.
---
```
#include <nsfdata.h>
```

**Symbolic Values :**

	REPLFLG_DISABLE	  -  If set, the Server's Replicator Task ignores this database. Enable replication by clearing this bit.

	REPLFLG_IGNORE_DELETES	  -  If set, don't propogate deleted notes (deletion stubs), when replicating from this database. Enable propogation by clearing this bit.

	REPLFLG_HIDDEN_DESIGN	  -  If set, hide the design of this database. Disable hide design by clearing this bit.

	REPLFLG_DO_NOT_CATALOG	  -  If set, Server's Catalog Task will not add this database to CATALOG.NSF. Enable cataloging by clearing this bit.

	REPLFLG_CUTOFF_DELETE	  -  If set, the Server's Replicator Task automatically deletes notes that are older than the cutoff date. Disable automatic document deletions by clearing this bit.

	REPLFLG_NEVER_REPLICATE	  -  If set, the Server's Replicator Task Ignores this database. Enable replication by clearing this bit. Since this can only be done programatically, it is a more bullet-proof method than REPLFLG_DISABLE, which can be modified from the user interface.

	REPLFLG_ABSTRACT	  -  If set, truncate large documents and remove attachments. Disable truncation by clearing this bit.

	REPLFLG_DO_NOT_BROWSE	  -  If set, do not list in Open Database dialog box. Enable listing in Open Database dialog box by clearing this bit.

	REPLFLG_NO_CHRONOS	  -  If set, disable background macros for this database. Enable background macros by clearing this bit.

	REPLFLG_IGNORE_DEST_DELETES	  -  If set, don't replicate deleted notes
 into destination database.

	REPLFLG_MULTIDB_INDEX	  -  Include in Multi Database indexing.

	REPLFLG_PRIORITY_LOW	  -  If set, replicator has low priority.

	REPLFLG_PRIORITY_MED	  -  If set, replicator has medium priority.

	REPLFLG_PRIORITY_HI	  -  If set, replicator has high priority.

	REPLFLG_PRIORITY_SHIFT	  -  Shift count for prioirty field within the WORD member.

	REPLFLG_PRIORITY_MASK	  -  Mask for priority field after shifting.

	REPLFLG_PRIORITY_INVMASK	  -  Mask for clearing the priority field.

	REPLFLG_USED_MASK	  -  Mask for determining whether any of the replication flags are set.

	REPLFLG_UNREADIFFNEW	  -  If set, modified documents are not marked as unread.


**Description :**

These flags are used by the Server's Replicator Task to control just what is done and not done during the replication process on a per-database level.<br>
<br>
Note that you cannot set the replicate database title, categories, and template option with the C API.<br>
<br>
The flags REPALFLG_DO_NOT_CATALOG, REPALFLG_HIDDEN_DESIGN, REPLFLG_DO_NOT_BROWSE, and REPALFLG_NO_CHRONOS refer to the Database Information, Other Settings options.<br>
<br>
Note the distinction between REPLFLG_DISABLE and REPLFLG_NEVER_REPLICATE. The former is used to temporarily disable replication.  The latter is used to indicate that this database should NEVER be replicated.  The former may be set and cleared by the Notes user interface. The latter is intended to be set programmatically and SHOULD NEVER be able to be cleared by the user interface.  The latter was invented to avoid having to set the replica ID to the known value of REPLICA_ID_NEVERREPLICATE.  This latter method has the failing that databases  that use it cannot have DocLinks to them.


**See Also :**
[NSFDbReplicaInfoGet](/domino-c-api-docs/reference/Func/NSFDbReplicaInfoGet)
[NSFDbReplicaInfoSet](/domino-c-api-docs/reference/Func/NSFDbReplicaInfoSet)
[DBREPLICAINFO](/domino-c-api-docs/reference/Data/DBREPLICAINFO)
---
