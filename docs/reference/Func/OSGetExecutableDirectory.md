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
[NSFDbPathGet](/reference/Func/NSFDbPathGet)
[NSFDbLocateByReplicaID](/reference/Func/NSFDbLocateByReplicaID)
[NSFDbOpen](/reference/Func/NSFDbOpen)
[NSFDbOpenExtended](/reference/Func/NSFDbOpenExtended)
[OSPathNetConstruct](/reference/Func/OSPathNetConstruct)
[OSPathNetParse](/reference/Func/OSPathNetParse)
---
