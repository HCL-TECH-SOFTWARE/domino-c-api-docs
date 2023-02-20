##### Function : Profile Document
##### SECAttachIdFileToDB - Attach an ID file to a profile note.
---
```
#include <kfm.h>
STATUS LNPUBLIC SECAttachIdFileToDB(

	DBHANDLE  hDB,
	char *pProfileNoteName,
	DWORD  ProfileNoteNameLength,
	char *pUserName,
	DWORD  UserNameLength,
	char *pIDFileName,
	char *pPassword,
	DWORD  Reserved,
	void *pReserved);
```
**Description :**

This routine will search the database for a named profile note and, if the note 
exists, will delete any ID File attachments present, get the input ID file in a 
roamed state and attach it to the record.  If the note does not exists, it will 
create the note, get the input ID file in a roamed state and attach it to the 
named record.

**Parameters :**
Input :
hDB  -  Open database handle of database to have the ID file attached to in "roamed" state.

pProfileNoteName  -  Profile note name that the ID file will be attached to.

ProfileNoteNameLength  -  Length of the profile note name.

pUserName  -  Name of user requesting access to the profile note.  Should be NULL.

UserNameLength  -  Length of user name.  Should be zero.

pIDFileName  -  Name of ID file to be "roamed" and attached to the pProfileNoteName in the database.

pPassword  -  Password to the ID file to be roamed and attached to the pProfileNoteName in the database.

Reserved  -  Reserved, should be set to 0.

pReserved  -  Reserved, should be set to NULL.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is.   The return codes include:

NOERROR - action successful



**See Also :**
[SECKFMClose](/reference/Func/SECKFMClose)
[SECKFMOpen](/reference/Func/SECKFMOpen)
---
