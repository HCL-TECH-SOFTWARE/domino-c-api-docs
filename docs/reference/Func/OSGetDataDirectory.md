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
[NSFDbPathGet](/domino-c-api-docs/reference/Func/NSFDbPathGet)
[NSFDbLocateByReplicaID](/domino-c-api-docs/reference/Func/NSFDbLocateByReplicaID)
[NSFDbOpen](/domino-c-api-docs/reference/Func/NSFDbOpen)
[NSFDbOpenExtended](/domino-c-api-docs/reference/Func/NSFDbOpenExtended)
[OSPathNetConstruct](/domino-c-api-docs/reference/Func/OSPathNetConstruct)
[OSPathNetParse](/domino-c-api-docs/reference/Func/OSPathNetParse)
[OSGetEnvironmentString](/domino-c-api-docs/reference/Func/OSGetEnvironmentString)
---
