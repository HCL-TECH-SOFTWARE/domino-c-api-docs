##### Function : OS File
##### OSGetDataDirectory - Get the pathname of the local Domino or Notes data directory.
---
```
#include <osfile.h>
WORD LNPUBLIC OSGetDataDirectory(

	char far *retPathName);
```
**Description :**

Given the address of a text buffer, this function returns the path 
specification of the local Domino or Notes data directory.  It also returns the 
length of that null-terminated string.  OSGetDataDirectory is equivalent to 
using OSGetEnvironmentString to obtain the value of the "Directory=" 
environment variable from notes.ini.

**Parameters :**

Output :
(routine)  -  The length of the returned data directory path specification.


retPathName  -  The address of a text buffer dimensioned with MAXPATH, in which a null-terminated string containing the full path specification of the LOCAL Domino or Notes data directory is returned.


**See Also :**
[NSFDbPathGet](/reference/Func/NSFDbPathGet)
[NSFDbLocateByReplicaID](/reference/Func/NSFDbLocateByReplicaID)
[NSFDbOpen](/reference/Func/NSFDbOpen)
[NSFDbOpenExtended](/reference/Func/NSFDbOpenExtended)
[OSPathNetConstruct](/reference/Func/OSPathNetConstruct)
[OSPathNetParse](/reference/Func/OSPathNetParse)
[OSGetEnvironmentString](/reference/Func/OSGetEnvironmentString)
---
