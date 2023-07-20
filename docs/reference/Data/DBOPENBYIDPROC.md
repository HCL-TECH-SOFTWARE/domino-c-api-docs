##### Data Type : Database Drivers
##### DBOPENBYIDPROC - Type of procedure passed to an external database driver's context function.
---
```
#include <dbdrv.h>
```

**Definition :**
```
typedef STATUS (LNCALLBACKPTR DBOPENBYIDPROC)(
   DBID ReplicaID,
   char far *FileTitle,
   DHANDLE hNames,
   DBHANDLE far *rethDB);
```

**Description :**

Data type of a function that can be passed to the SetOpenContext function of an external database driver.  It is recommended that you do not define a function for the SetOpenContext function.  This function is reserved for use by Domino and Notes.


**See Also :**
[DBVEC](/domino-c-api-docs/reference/Data/DBVEC)
---
