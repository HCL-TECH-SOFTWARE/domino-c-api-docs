##### Function : Database
##### NSFDbHasProfileNoteChanged - Determine whether a profile note has been modified since a given time. 
---
##### #include <nsfdb.h>
STATUS LNPUBLIC **NSFDbHasProfileNoteChanged(**

	DBHANDLE  hDb,
	NOTEID  noteid,
	DWORD *pSeqNum,
	TIMEDATE *Since,
	BOOL *HasChanged,
	TIMEDATE *retModTime);
**Description :**
This function determines whether a profile note has been modified since a given 
time.  The profile note modified sequence number for the database is also 
checked.  If the profile note has been modifed, its modified time is returned , 
along with the current profile note modified sequence number.
**Parameters :**
Input :
hDb  -  A handle to an open Domino database.

noteid  -  The NOTEID of the note whose particulars you wish to retrieve.

pSeqNum  -  Sequence number.

Since  -  Timedate since.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - Successfully retrieved the note information.

ERR_NOTE_DELETED - Document has been deleted.

ERR_xxx - Errors returned by lower level functions.  There are so many possible causes, that It is best to use the code in a call to OSLoadString and display/log the error for the user.


pSeqNum  -  Updated sequence number

HasChanged  -  TRUE - Note has changed  FALSE - Note has not changed

retModTime  -  Returns the populated TIMEDATE structure containing the note's last modified time and date normalized to Greenwich Mean Time (GMT).

**See Also :**
[EM_xxx](D:/md_files/EM_xxx.md)
---
