##### Data Type : Replica Info
##### DBREPLICAINFO - Identifies and configures a replica database.
---
```
#include <nsfdata.h>
```

**Definition :**

typedef struct {
   TIMEDATE ID;      /* ID that is same for all replica files */
   WORD     Flags;   /* Replication flags */
   WORD     CutoffInterval; /* Automatic Replication Cutoff
                        Interval (Days) */
   TIMEDATE Cutoff;  /* Replication cutoff date */
} DBREPLICAINFO;

**Description :**

This is the structure that identifies a replica database and stores the replication options that affect how the Server's Replicator Task will manipulate the database.  Some replication Flags, CutoffInterval, and Cutoff members correspond to the edit controls in the the Workstation's Replication Settings dialog box (in the File, Database, Properties InfoBox).<br>
<br>
The Replica ID is a TIMEDATE structure that contains the time/date of the replica's creation, used to uniquely identify the database replicas to each other.  This time/date is NOT normalized to Greenwich Mean Time (GMT), as keeping the local time zone and daylight savings time settings will further ensure that it is a unique time/date.


**See Also :**
[NSFDbReplicaInfoGet](/domino-c-api-docs/reference/Func/NSFDbReplicaInfoGet)
[NSFDbReplicaInfoSet](/domino-c-api-docs/reference/Func/NSFDbReplicaInfoSet)
[REPLFLG_xxx](/domino-c-api-docs/reference/Symb/REPLFLG_xxx)
---
