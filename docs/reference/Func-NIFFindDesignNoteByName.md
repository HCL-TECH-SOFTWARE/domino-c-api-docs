##### Function : Views
##### NIFFindDesignNoteByName - * OBSOLETE * Calls NIFFindDesignNote with the Class argument set to NOTE_CLASS_ALL.
---
##### #include <nif.h>
STATUS LNPUBLIC **NIFFindDesignNoteByName(**

	DBHANDLE  hFile,
	char *Name,
	NOTEID *retNoteID);
**Description :**
This is a macro that calls NIFFindDesignNote with the Class argument set to 
NOTE_CLASS_ALL.  If there are more than one form, view, helpindex, macro, 
field, or replication formula note with the given name, only the first one 
found is returned.

This function provides compatibility for applications prior to version 3.0 of 
the API.  Otherwise, this function is obsolete.  Use NIFFindDesignNote or 
NIFFindView instead.
**Parameters :**
Input :
hFile  -  Handle to the database.

Name  -  A pointer to a null-terminated character string, that holds the name of the form, view, helpindex, macro, field, or replication formula note, you want to find.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR
ERR_NOT_FOUND
ERR_xxx - Errors returned by lower level functions.  There are so many possible causes, that it is best to use the code in a call to OSLoadString and display/log the error for the user.


retNoteID  -  Pointer to the returned NOTEID.

**Sample Usage :**
```
/* This code fragment shows how to get a collection of
the notes in a view, given the view's name. */

       if (error = NIFFindDesignNoteByName(
                   hDB, 
                   szViewName, 
                   &ViewID))
           return(error);

       if (error = NIFOpenCollection(
                   hDB,  
                   hDB,   
                   ViewID,  
                   0,     
                   NULLHANDLE,   
                  &hCollection,  
                   NULL,     
                   NULL,  
                   NULL,      
                   NULL)) 
           return(error);


```
**See Also :**
[NIFFindDesignNote](D:/md_files/NIFFindDesignNote.md)
[NIFFindView](D:/md_files/NIFFindView.md)
---
