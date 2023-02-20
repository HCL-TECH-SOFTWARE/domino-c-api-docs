##### Function : OS File
##### OSGetSharedDataDirectory - If a shared data directory is used, get its path.
---
```
#include <osfile.h>
WORD OSGetSharedDataDirectory(

	char *retPathName);
```
**Description :**

If a shared directory is used, get the name and length of the shared directory. 
A length of zero indicates there is no shared directory defined. A shared data 
directory is used to store templates, help files, and other shared components 
used in Notes/Domino installation and configuration. 

**Parameters :**
Input :
retPathName  -  Holds templates, help files, etc.

Output :
(routine)  -  Returns length of the directory name. Returns zero if there is no shared directory.



**Sample Usage :**
```
	char FilePath[MAXPATH] = { 0 }; 

	if (OSGetSharedDataDirectory(FilePath) != 0) 
	{ 
	 OSPathConstruct(FilePath, "pubnames.ntf", FilePath); 
	 if (OSFileOpenRead(FilePath, &fd)) 
	  return; 
	} 
```
**See Also :**
---
