##### Function : OS File
##### OSGetExecutableDirectory - Get the pathname of the local Domino or Notes Executable directory.
---
```
#include <osfile.h>
void LNPUBLIC OSGetExecutableDirectory(

	char *retPathName);
```
**Description :**

Given the address of a text buffer, this function returns the path 
specification of the local Domino or Notes Executable directory. 

**Parameters :**

Output :
retPathName  -  The address of a text buffer dimensioned with MAXPATH, in which a null-terminated string containing the full path specification of the local Domino or Notes Executable directory is returned.


**See Also :**
[NSFDbPathGet](/domino-c-api-docs/reference/Func/NSFDbPathGet)
[NSFDbLocateByReplicaID](/domino-c-api-docs/reference/Func/NSFDbLocateByReplicaID)
[NSFDbOpen](/domino-c-api-docs/reference/Func/NSFDbOpen)
[NSFDbOpenExtended](/domino-c-api-docs/reference/Func/NSFDbOpenExtended)
[OSPathNetConstruct](/domino-c-api-docs/reference/Func/OSPathNetConstruct)
[OSPathNetParse](/domino-c-api-docs/reference/Func/OSPathNetParse)
---
