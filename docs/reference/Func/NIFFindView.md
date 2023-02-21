##### Function : Views
##### NIFFindView - Returns the note ID of the specified view or shared folder note, given the name.
---
```
#include <nif.h>
STATUS LNPUBLIC NIFFindView(

	DBHANDLE  hFile,
	const char far *Name,
	NOTEID far *retNoteID);
```
**Description :**

This is a macro used to return the note ID of a view or shared folder note, 
given the name.  The name is compared without regard to case (case insensitive).

This function uses an on-disk index of these types of notes and is very 
efficient.

#define NIFFindView(hFile,Name,retNoteID) 
NIFFindDesignNoteExt(hFile,Name,NOTE_CLASS_VIEW, DFLAGPAT_VIEWS_AND_FOLDERS, 
retNoteID, 0)

**Parameters :**
Input :
hFile  -   Handle to the database.

Name  -   Pointer to a null-terminated character string that holds the name of the note you want to find.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR
ERR_NOT_FOUND
ERR_xxx - Errors returned by lower level functions.  There are so many possible causes, that it is best to use the code in a call to OSLoadString and display/log the error for the user.


retNoteID  -  Pointer to the returned NOTEID.


**See Also :**
[NIFCloseCollection](/domino-c-api-docs/reference/Func/NIFCloseCollection)
[NIFFindDesignNote](/domino-c-api-docs/reference/Func/NIFFindDesignNote)
[NIFFindDesignNoteExt](/domino-c-api-docs/reference/Func/NIFFindDesignNoteExt)
[NIFOpenCollection](/domino-c-api-docs/reference/Func/NIFOpenCollection)
---
