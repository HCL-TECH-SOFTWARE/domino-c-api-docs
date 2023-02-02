##### Function : Folders
##### FolderDocRemove - Removes the specified document(s) from a folder.
---
##### #include <foldman.h>
STATUS LNPUBLIC **FolderDocRemove(**

	DBHANDLE  hDataDB,
	DBHANDLE  hFolderDB,
	NOTEID  FolderNoteID,
	DHANDLE  hTable,
	DWORD  dwFlags);
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
[FolderCopy](D:/md_files/FolderCopy.md)
[FolderCreate](D:/md_files/FolderCreate.md)
[FolderDelete](D:/md_files/FolderDelete.md)
[FolderDocAdd](D:/md_files/FolderDocAdd.md)
[FolderDocCount](D:/md_files/FolderDocCount.md)
[FolderDocRemoveAll](D:/md_files/FolderDocRemoveAll.md)
[FolderMove](D:/md_files/FolderMove.md)
[FolderRename](D:/md_files/FolderRename.md)
---
