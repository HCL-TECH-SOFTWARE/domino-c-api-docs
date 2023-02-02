##### Function : Dir
##### DirEntryFree - Free the memory associated with an entry returned by a get operation. 
---
##### #include <direntry.h>
void LNPUBLIC **DirEntryFree(**

	DIRENTRY  hEntry);
**Description :**
Free the memory associated with an entry returned by a get operation,
**Parameters :**
Input :
hEntry  -  Handle to the entry to free. If NULLDIRENTRY then nothing is freed. 

Output :
(routine)  -  This function returns a VOLD,if the free fails a NULLDIRENTRY is returned in the parameter.


**See Also :**
[DirCtxGetEntryByID](D:/md_files/DirCtxGetEntryByID.md)
---
