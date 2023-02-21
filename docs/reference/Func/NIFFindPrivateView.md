##### Function : Folders
##### NIFFindPrivateView - Returns the note ID of the specified private view or folder
---
```
#include <nif.h>
STATUS LNPUBLIC NIFFindPrivateView(

	DBHANDLE  hFile,
	char far *Name,
	NOTEID far *retNoteID);
```
**Description :**

Given the name of a private view or folder, this function returns the note 
ID.   The name is compared without regard to case (case insensitive).

This function uses an on-disk index of these types of notes and is very 
efficient.

Private folders that are stored in the user's desktop file, rather than in the 
database, cannot be accessed by the C API.  Also, the C API cannot store 
private folders in the user's desktop file.  Private folders are stored in the 
user's desktop file only by the Notes user interface and only if the user does 
not have the access right to create private folders in the database.

Note: This function is implemented as a macro:

#define NIFFindPrivateView(hFile,Name,retNoteID) 
NIFFindPrivateDesignNote(hFile,Name,NOTE_CLASS_VIEW,retNoteID)

**Parameters :**
Input :
hFile  -  Handle to the database.

Name  -  Pointer to a null-terminated character string that holds the name of the note you want to find.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR
ERR_NOT_FOUND
ERR_xxx - Errors returned by lower level functions.  There are so many possible causes, that it is best to use the code in a call to OSLoadString and display/log the error for the user.


retNoteID  -  Pointer to the returned NOTEID.


**See Also :**
[NIFFindDesignNote](/domino-c-api-docs/reference/Func/NIFFindDesignNote)
[NIFFindDesignNoteByName](/domino-c-api-docs/reference/Func/NIFFindDesignNoteByName)
[NIFFindPrivateDesignNote](/domino-c-api-docs/reference/Func/NIFFindPrivateDesignNote)
[NIFFindView](/domino-c-api-docs/reference/Func/NIFFindView)
---
