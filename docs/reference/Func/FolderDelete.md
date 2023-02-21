##### Function : Folders
##### FolderDelete - Deletes a folder.
---
```
#include <foldman.h>
STATUS LNPUBLIC FolderDelete(

	DBHANDLE  hDataDB,
	DBHANDLE  hFolderDB,
	NOTEID  FolderNoteID,
	DWORD  dwFlags);
```
**Description :**

This function deletes the given folder.  Subfolders within this folder are also 
deleted.

**Parameters :**
Input :
hDataDB  -  The handle to the open database where the folder resides.

hFolderDB  -  Must be NULLHANDLE.

FolderNoteID  -  NOTEID of folder to be deleted.

dwFlags  -  Reserved for future use.  Specify  0L.

Output :
(routine)  -  Return status of the call - indicates either success or what the error is. The return codes include:

NOERROR

ERR_xxx - Error returned by lower level functions. Call OSLoadString to interpret the code.



**Sample Usage :**
```
error = FolderDelete(hDB, NULLHANDLE, FNoteID, 0L);
```
**See Also :**
[FolderCopy](/domino-c-api-docs/reference/Func/FolderCopy)
[FolderCreate](/domino-c-api-docs/reference/Func/FolderCreate)
[FolderDocAdd](/domino-c-api-docs/reference/Func/FolderDocAdd)
[FolderDocCount](/domino-c-api-docs/reference/Func/FolderDocCount)
[FolderDocRemove](/domino-c-api-docs/reference/Func/FolderDocRemove)
[FolderDocRemoveAll](/domino-c-api-docs/reference/Func/FolderDocRemoveAll)
[FolderMove](/domino-c-api-docs/reference/Func/FolderMove)
[FolderRename](/domino-c-api-docs/reference/Func/FolderRename)
---
