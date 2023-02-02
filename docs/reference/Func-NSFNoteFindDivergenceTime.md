##### Function : Note
##### NSFNoteFindDivergenceTime - Find when two notes were last in synch.
---
##### #include <nsfnote.h>
STATUS LNPUBLIC **NSFNoteFindDivergenceTime(**

	NOTEHANDLE  hNote1,
	NOTEHANDLE  hNote2,
	DWORD  dwFlags,
	TIMEDATE *tdLastSyncTime);
**Description :**
This routine returns the last TIMEDATE two notes were in synch (ie replicated).
**Parameters :**
Input :
hNote1  -  Handle to the first note.

hNote2  -  Handle to the second note.

dwFlags  -  Reserved for future use.  Must be set to 0L.

Output :
(routine)  -  NOERROR - Successfully found the last synch time.
ERR_SYNC_TIME_NOT_FOUND - The two notes do not have a common revision time.
ERR_xxx - There are many possible errors. It is best to use the code in a call to OSLoadString and display/log the error for the user as your default error handling.


tdLastSyncTime  -  TIMEDATE when the notes were last in synch.

**See Also :**
[NSFDbGetNoteInfo](D:/md_files/NSFDbGetNoteInfo.md)
---
