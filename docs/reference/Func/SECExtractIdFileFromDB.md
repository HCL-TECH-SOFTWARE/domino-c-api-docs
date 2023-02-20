##### Function : Profile Document
##### SECExtractIdFileFromDB - Extract an ID file from a profile note.
---
```
#include <kfm.h>
STATUS LNPUBLIC SECExtractIdFileFromDB(

	DBHANDLE  hDB,
	char *pProfileNoteName,
	DWORD  ProfileNoteNameLength,
	char *pUserName,
	DWORD  UserNameLength,
	char *pPassword,
	char *pPutIDFileHere,
	DWORD  Reserved,
	void *pReserved);
```
**Description :**

This routine will search the database for a named profile note and, if the note 
is found, will extract the attached ID file to a specified location.  After the 
file has been extracted, it will be "unroamed".  There is no updating to the ID 
file after it has been detached. 

**Parameters :**
Input :
hDB  -  Open database handle of database to be searched for ID file.

pProfileNoteName  -  Profile note name that the ID file will be extracted from.

ProfileNoteNameLength  -  Length of the profile note name.

pUserName  -  Name of user requesting access to the profile note.  Should be NULL.

UserNameLength  -  Length of user name.  Should be zero.

pPassword  -  Password to the ID file to be extracted from the database.

pPutIDFileHere  -  File name to extract the ID file to.

Reserved  -  Reserved, should be set to 0.

pReserved  -  Reserved, should be set to NULL.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is.   The return codes include:

NOERROR - action successful



**See Also :**
[SECKFMClose](/reference/Func/SECKFMClose)
[SECKFMOpen](/reference/Func/SECKFMOpen)
---
