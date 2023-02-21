##### Function : Views
##### NIFFindDesignNoteExt - Returns the note ID of the specified form, view, shared folder, macro, or field note.
---
```
#include <nif.h>
STATUS LNPUBLIC NIFFindDesignNoteExt(

	DBHANDLE  hFile,
	const char far *Name,
	WORD  Class,
	const char *pszFlagsPattern,
	NOTEID far *retNoteID,
	DWORD  Options);
```
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

The "pszFlagsPattern" parameter provides a way to extend the specification of 
certain NOTE_CLASS_xxx types by incorporating Design Flag Patterns when 
searching for specific design notes.  Design Flag Pattern definitions are 
described in the Tech Note "Design Flag Patterns".  Tech Notes are listed in 
the view, Reference Tools/Tech Notes.

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

pszFlagsPattern  -  Pointer to a character string defining a Design Flag Pattern.  See "stdnames.h" for a list of common Design Flag Patterns (DFLAGPAT_xxx).

Options  -  Please see FIND_DESIGN_NOTE_xxx for options or zero for no options.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR
ERR_NOT_FOUND
ERR_xxx - Errors returned by lower level functions.  There are so many possible causes, that it is best to use the code in a call to OSLoadString and display/log the error for the user.


retNoteID  -  Pointer to the returned NOTEID.


**See Also :**
[FIND_DESIGN_NOTE_xxx](/domino-c-api-docs/reference/Symb/FIND_DESIGN_NOTE_xxx)
[NIFCloseCollection](/domino-c-api-docs/reference/Func/NIFCloseCollection)
[NIFFindDesignNote](/domino-c-api-docs/reference/Func/NIFFindDesignNote)
[NIFFindView](/domino-c-api-docs/reference/Func/NIFFindView)
[NIFOpenCollection](/domino-c-api-docs/reference/Func/NIFOpenCollection)
[NOTE_CLASS_xxx](/domino-c-api-docs/reference/Symb/NOTE_CLASS_xxx)
---
