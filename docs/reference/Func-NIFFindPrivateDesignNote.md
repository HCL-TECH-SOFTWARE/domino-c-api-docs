##### Function : Views
##### NIFFindPrivateDesignNote - Returns the note ID of the specified private design note
---
##### #include <nif.h>
STATUS LNPUBLIC **NIFFindPrivateDesignNote(**

	DBHANDLE  hFile,
	const char far *Name,
	WORD  Class,
	NOTEID far *retNoteID);
**Description :**
Given the name and NOTE_CLASS_xxx of a private design note (form, view, folder, 
helpindex, macro, field, or replication formula ), this function returns the 
note ID.   The name is compared without regard to case (case insensitive).

Only the following NOTE_CLASS_xxx types are valid for this function:
NOTE_CLASS_FORM
NOTE_CLASS_VIEW
NOTE_CLASS_HELP_INDEX
NOTE_CLASS_FILTER
NOTE_CLASS_FIELD
NOTE_CLASS_REPLFORMULA
NOTE_CLASS_ALL

Specify NOTE_CLASS_VIEW for private folders as well as private views.  However, 
private folders that are stored in the user's desktop file, rather than in the 
database, cannot be accessed by the C API.  Also, the C API cannot store 
private folders in the user's desktop file.  Private folders are stored in the 
user's desktop file only by the Notes user interface and only if the user does 
not have the access right to create private folders in the database.

This function uses an on-disk index of these types of notes and is very 
efficient.
**Parameters :**
Input :
hFile  -  Handle to the database.

Name  -  Pointer to a null-terminated character string that holds the name of the note you want to find.

Class  -  The type of note which must be one of the following NOTE_CLASS_xxx types:
NOTE_CLASS_FORM
NOTE_CLASS_VIEW
NOTE_CLASS_HELP_INDEX
NOTE_CLASS_FILTER
NOTE_CLASS_FIELD
NOTE_CLASS_REPLFORMULA
NOTE_CLASS_ALL

If NOTE_CLASS_ALL is specified, then the id of the first note found with the specified name is returned.  The found note will be one of the above NOTE_CLASS_xxx types.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR
ERR_NOT_FOUND
ERR_xxx - Errors returned by lower level functions.  There are so many possible causes, that it is best to use the code in a call to OSLoadString and display/log the error for the user.


retNoteID  -  Pointer to the returned NOTEID.

**See Also :**
[NIFFindDesignNote](D:/md_files/NIFFindDesignNote.md)
[NIFFindDesignNoteByName](D:/md_files/NIFFindDesignNoteByName.md)
[NIFFindView](D:/md_files/NIFFindView.md)
---
