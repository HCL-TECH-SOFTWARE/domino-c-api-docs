##### Function : Folders
##### FolderMove - Moves a folder under another folder.
---
```
#include <foldman.h>
STATUS LNPUBLIC FolderMove(

	DBHANDLE  hDataDB,
	DBHANDLE  hFolderDB,
	NOTEID  FolderNoteID,
	DBHANDLE  hParentDB,
	NOTEID  ParentNoteID,
	DWORD  dwFlags);
```
**Description :**

This function moves the specified folder under a given parent folder.  If the 
parent folder is a shared folder, then the child folder must be a shared 
folder.  If the parent folder is a private folder, then the child folder must 
be a private folder.

**Parameters :**
Input :
hDataDB  -  The handle to the open database where the folder to be moved resides.

hFolderDB  -  Must be NULLHANDLE.

FolderNoteID  -  NOTEID of folder to be moved.

hParentDB  -  Must be NULLHANDLE.  The parent database will be the same as the child database.

ParentNoteID  -  NOTEID of the parent folder.

dwFlags  -   Reserved for future use.  Specify  0L.

Output :
(routine)  -  Return status of the call - indicates either success or what the error is. The return codes include:

NOERROR

ERR_xxx - Error returned by lower level functions. Call OSLoadString to interpret the code.



**See Also :**
[FolderCopy](/reference/Func/FolderCopy)
[FolderCreate](/reference/Func/FolderCreate)
[FolderDelete](/reference/Func/FolderDelete)
[FolderDocAdd](/reference/Func/FolderDocAdd)
[FolderDocCount](/reference/Func/FolderDocCount)
[FolderDocRemove](/reference/Func/FolderDocRemove)
[FolderDocRemoveAll](/reference/Func/FolderDocRemoveAll)
[FolderRename](/reference/Func/FolderRename)
---