##### Function : Dir
##### NIFGetViewRebuildDir - Return a view directory name.
---
```
#include <nif.h>
BOOL NIFGetViewRebuildDir(

	char *szTempDir,
	WORD  wBufLen);
```
**Description :**

Validate that a view directory exists and if so return its name.

**Parameters :**
Input :

wBufLen  -  Maximum lenth of the buffer

Output :
(routine)  -  view directory name


szTempDir  -  Place holder for view directory


**Sample Usage :**
```
char szTempDir[MAXPATH] = { 0 };

NIFGetViewRebuildDir(szTempDir, sizeof(szTempDir)-1) 

/* Processing using szTempDir */ 	 
```
**See Also :**
---
