##### Function : OS File
##### OSGetExecutableDirectory - Get the pathname of the local Domino or Notes Executable directory.
---
##### #include <osfile.h>
void LNPUBLIC **OSGetExecutableDirectory(**

	char *retPathName);
**Description :**
Given the address of a text buffer, this function returns the path 
specification of the local Domino or Notes Executable directory. 
**Parameters :**

Output :
retPathName  -  The address of a text buffer dimensioned with MAXPATH, in which a null-terminated string containing the full path specification of the local Domino or Notes Executable directory is returned.

**See Also :**
[NSFDbPathGet](D:/md_files/NSFDbPathGet.md)
[NSFDbLocateByReplicaID](D:/md_files/NSFDbLocateByReplicaID.md)
[NSFDbOpen](D:/md_files/NSFDbOpen.md)
[NSFDbOpenExtended](D:/md_files/NSFDbOpenExtended.md)
[OSPathNetConstruct](D:/md_files/OSPathNetConstruct.md)
[OSPathNetParse](D:/md_files/OSPathNetParse.md)
---
