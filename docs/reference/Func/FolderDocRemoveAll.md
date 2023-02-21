##### Function : Folders
##### FolderDocRemoveAll - Removes all documents from a folder
---
```
#include <foldman.h>
STATUS LNPUBLIC FolderDocRemoveAll(

	DBHANDLE  hDataDB,
	DBHANDLE  hFolderDB,
	NOTEID  FolderNoteID,
	DWORD  dwFlags);
```
**Description :**

This function removes all documents from a specified folder.  Subfolders and 
documents within the subfolders are not removed.

**Parameters :**
Input :
hDataDB  -  The handle to the open database where the folder resides.

hFolderDB  -  Must be NULLHANDLE.

FolderNoteID  -  NOTEID of folder whose documents will be removed.

dwFlags  -  Reserved for future use.  Specify  0L.

Output :
(routine)  -  Return status of the call - indicates either success or what the error is. The return codes include:

NOERROR

ERR_xxx - Error returned by lower level functions. Call OSLoadString to interpret the code.



**Sample Usage :**
```
error = FolderDocRemoveAll (hDB, NULLHANDLE, FNoteID, 0L);
```
**See Also :**
[FolderCopy](/domino-c-api-docs/reference/Func/FolderCopy)
[FolderCreate](/domino-c-api-docs/reference/Func/FolderCreate)
[FolderDelete](/domino-c-api-docs/reference/Func/FolderDelete)
[FolderDocAdd](/domino-c-api-docs/reference/Func/FolderDocAdd)
[FolderDocCount](/domino-c-api-docs/reference/Func/FolderDocCount)
[FolderDocRemove](/domino-c-api-docs/reference/Func/FolderDocRemove)
[FolderMove](/domino-c-api-docs/reference/Func/FolderMove)
[FolderRename](/domino-c-api-docs/reference/Func/FolderRename)
---
