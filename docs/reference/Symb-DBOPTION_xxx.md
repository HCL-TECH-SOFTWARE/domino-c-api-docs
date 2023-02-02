##### Symbolic Value : Database
##### DBOPTION_xxx - Database option flags.
---
##### #include <nsfdb.h>
**Description :**
These option flags apply to the whole database.  These flags may be read using 
NSFDbGetOptions() and modified using NSFDbSetOptions().

NSFDbGetOptions will not return the DBOPTION_OBJSTORE_xxx flags (even if any 
are set in the database) if the specified database is a remote database.  
NSFDbSetOptions will not set the DBOPTION_OBJSTORE_xxx flags if the specified 
database is a remote database. 
**See Also :**
[NSFDbGetOptions](D:/md_files/NSFDbGetOptions.md)
[NSFDbSetOptions](D:/md_files/NSFDbSetOptions.md)
---
