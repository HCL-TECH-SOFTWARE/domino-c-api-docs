##### Function : Views
##### NIFFindDesignNote - Returns the note ID of the specified form, view, shared folder, macro, or field note.
---
##### #include <nif.h>
STATUS LNPUBLIC **NIFFindDesignNote(**

	DBHANDLE  hFile,
	const char far *Name,
	WORD  Class,
	NOTEID far *retNoteID);
**Description :**
This function returns the note ID of a form, view, shared folder, macro, or 
field note, given the name and NOTE_CLASS_xxx.  The name is compared without 
regard to case (case insensitive).

Only the following NOTE_CLASS types are valid for this function:
NOTE_CLASS_FORM
NOTE_CLASS_VIEW
NOTE_CLASS_FILTER
NOTE_CLASS_FIELD
NOTE_CLASS_ALL

Specify NOTE_CLASS_VIEW for shared  folders as well as private views.

This function uses an on-disk index of these types of notes and is very 
efficient.
**Parameters :**
Input :
hFile  -  Handle to the database.

Name  -  Pointer to a null-terminated character string that holds the name of the note you want to find.

Class  -  The type of note which must be one of the following NOTE_CLASS_xxx types:
NOTE_CLASS_FORM
NOTE_CLASS_VIEW
NOTE_CLASS_FILTER
NOTE_CLASS_FIELD
NOTE_CLASS_ALL

If NOTE_CLASS_ALL is specified, then the id of the first note found with the specified name is returned.  The found note will be one of the above NOTE_CLASS_xxx types.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR
ERR_NOT_FOUND
ERR_xxx - Errors returned by lower level functions.  There are so many possible causes, that it is best to use the code in a call to OSLoadString and display/log the error for the user.


retNoteID  -  Pointer to the returned NOTEID.

**See Also :**
[NIFCloseCollection](D:/md_files/NIFCloseCollection.md)
[NIFFindDesignNoteExt](D:/md_files/NIFFindDesignNoteExt.md)
[NIFFindView](D:/md_files/NIFFindView.md)
[NIFOpenCollection](D:/md_files/NIFOpenCollection.md)
[NOTE_CLASS_xxx](D:/md_files/NOTE_CLASS_xxx.md)
---
