##### Function : Folders
##### FolderDocRemove - Removes the specified document(s) from a folder.
---
```
#include <foldman.h>
STATUS LNPUBLIC FolderDocRemove(

	DBHANDLE  hDataDB,
	DBHANDLE  hFolderDB,
	NOTEID  FolderNoteID,
	DHANDLE  hTable,
	DWORD  dwFlags);
```
**Description :**

This function removes the document(s) specified in an ID Table from a folder.

**Parameters :**
Input :
hDataDB  -  The handle to the open database where the folder resides.

hFolderDB  -  Must be NULLHANDLE.

FolderNoteID  -  NOTEID of folder containing document(s) to be removed.

hTable  -  Handle to the ID Table of document(s) to be removed.

dwFlags  -  Reserved for future use.  Specify  0L.

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
[FolderDocRemoveAll](/reference/Func/FolderDocRemoveAll)
[FolderMove](/reference/Func/FolderMove)
[FolderRename](/reference/Func/FolderRename)
---
