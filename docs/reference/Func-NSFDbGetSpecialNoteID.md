##### Function : Database
##### NSFDbGetSpecialNoteID - Get Note ID of Policy, Help or other special notes.
---
##### #include <nsfdb.h>
STATUS LNPUBLIC **NSFDbGetSpecialNoteID(**

	DBHANDLE  hDB,
	WORD  Index,
	NOTEID far *retNoteID);
**Description :**
This function allows you to obtain the Note ID (NOTEID) of several unique 
database documents.  It is quicker and less complicated than NSFSearch 
(sequential access with an action routine) using various NOTE_CLASS_xxx 
combinations and/or formula.
**Parameters :**
Input :
hDB  -  A handle to a database.

Index  -  SPECIAL_ID_NOTE OR'ed with a NOTE_CLASS_xxx:

SPECIAL_ID_NOTE | NOTE_CLASS_INFO  - get database Policy Document (Help-About Database document) NOTEID.
SPECIAL_ID_NOTE | NOTE_CLASS_ICON -  get database Icon NOTEID.
SPECIAL_ID_NOTE | NOTE_CLASS_HELP - get database Help Document (Help-Using Database document) NOTEID.
SPECIAL_ID_NOTE | NOTE_CLASS_DESIGN - get database design collection view NOTEID.
SPECIAL_ID_NOTE | NOTE_CLASS_VIEW - get the default view.
SPECIAL_ID_NOTE | NOTE_CLASS_FORM - get the default form.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - Successfully obtained the special note ID (NID).

ERR_SPECIAL_ID - Special database object cannot be located.

ERR_xxx - Errors returned by lower level functions.  There are so many possible causes, that It is best to use the code in a call to OSLoadString and display/log the error for the user.


retNoteID  -  The address of a NOTEID in which the Note ID of the special note/document is returned.

**Sample Usage :**
```

   /* Find some SPECIAL notes */
 
  if (error_status = NSFDbGetSpecialNoteID(db_handle_src,
                          SPECIAL_ID_NOTE | NOTE_CLASS_INFO,
                          &policy_nid_src))
   {
       if (ERR(error_status) == ERR_SPECIAL_ID)
           printf("\n%s has no Policy Note\n", src_name);
       else
           goto Exit;
   }

```
**See Also :**
[NOTE_CLASS_xxx](D:/md_files/NOTE_CLASS_xxx.md)
[NSFNoteOpen](D:/md_files/NSFNoteOpen.md)
[NSFSearch](D:/md_files/NSFSearch.md)
[SPECIAL_ID_NOTE](D:/md_files/SPECIAL_ID_NOTE.md)
---
