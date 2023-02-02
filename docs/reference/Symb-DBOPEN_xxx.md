##### Symbolic Value : Clusters
##### DBOPEN_xxx - Database open options.
---
##### #include <nsfdb.h>
**Description :**
Database open options controlling Domino based file locking (scan lock), the 
removal of deleted note stubs, the removal of documents whose last modified 
date is past the replication cutoff date (and whose REPLFLG_CUTOFF_DELETE 
replication flag is set), the forcing of an Access Control List (ACL) check 
during local database access, and initiation of a database fixup covering 
various levels of detail.

These flags can only be specified with NSFDbOpenExtended, and not with 
NSFDbOpen.
**See Also :**
[NSFDbOpenExtended](D:/md_files/NSFDbOpenExtended.md)
---
