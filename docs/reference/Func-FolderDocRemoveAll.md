##### Function : Folders
##### FolderDocRemoveAll - Removes all documents from a folder
---
##### #include <foldman.h>
STATUS LNPUBLIC **FolderDocRemoveAll(**

	DBHANDLE  hDataDB,
	DBHANDLE  hFolderDB,
	NOTEID  FolderNoteID,
	DWORD  dwFlags);
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
[FolderCopy](D:/md_files/FolderCopy.md)
[FolderCreate](D:/md_files/FolderCreate.md)
[FolderDelete](D:/md_files/FolderDelete.md)
[FolderDocAdd](D:/md_files/FolderDocAdd.md)
[FolderDocCount](D:/md_files/FolderDocCount.md)
[FolderDocRemove](D:/md_files/FolderDocRemove.md)
[FolderMove](D:/md_files/FolderMove.md)
[FolderRename](D:/md_files/FolderRename.md)
---
