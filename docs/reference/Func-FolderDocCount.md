##### Function : Folders
##### FolderDocCount - Finds the number of entries in a folder's index.
---
##### #include <foldman.h>
STATUS LNPUBLIC **FolderDocCount(**

	DBHANDLE  hDataDB,
	DBHANDLE  hFolderDB,
	NOTEID  FolderNoteID,
	DWORD  dwFlags,
	DWORD far *pdwNumDocs);
**Description :**
This function returns the number of entries in the specified folder's index.  
This is the number of documents plus the number of cateogories (if any) in the 
folder.  Subfolders and documents in subfolders are not included in the count.
**Parameters :**
Input :
hDataDB  -  The handle to the open database where the folder resides.

hFolderDB  -  Must be NULLHANDLE.

FolderNoteID  -  NOTEID of folder.

dwFlags  -  Reserved for future use.  Specify  0L.

Output :
(routine)  -  Return status of the call - indicates either success or what the error is. The return codes include:

NOERROR

ERR_xxx - Error returned by lower level functions. Call OSLoadString to interpret the code.


pdwNumDocs  -  Pointer to the returned number of documents in the folder.

**Sample Usage :**
```
error = FolderDocCount (hDB, NULLHANDLE, FNoteID, 0L, &DocCount);
```
**See Also :**
[FolderCopy](D:/md_files/FolderCopy.md)
[FolderCreate](D:/md_files/FolderCreate.md)
[FolderDelete](D:/md_files/FolderDelete.md)
[FolderDocAdd](D:/md_files/FolderDocAdd.md)
[FolderDocRemove](D:/md_files/FolderDocRemove.md)
[FolderDocRemoveAll](D:/md_files/FolderDocRemoveAll.md)
[FolderMove](D:/md_files/FolderMove.md)
[FolderRename](D:/md_files/FolderRename.md)
---
