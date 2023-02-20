##### Function : Recovery
##### SECRecoverIDFile - Recover an ID file with multiple passwords
---
```
#include <kfm.h>
STATUS LNPUBLIC SECRecoverIDFile(

	char *pIDFileName,
	WORD  NumPasswords,
	char *pPassword[8],
	char *newPassword,
	WORD  newPasswordLen,
	void *pReserved,
	DWORD  ReservedFlags);
```
**Description :**

Given the name of an ID file to recover, array of recovery passwords, and new 
password recover the ID file and set it to have the new password.
Routine:
	1. Open the ID file to be recovered (pointed to by pIDFileName).
	2. Create a multi password context from the just opened ID file.
	3. Go through the array of passwords and hit the ID file with the 
multipassword context with each password.
	4. Check to see if the qurom has been reached for valid passwords to 
open the ID file.
	5. Unlock the ID file via the recovery mechanism and get the key that 
unlocks the ID file.
	6.Close the ID file and reopen so that we may change the password.
	7.Restore any saved keys
	8. Delete any smart card extras
	9. Update the acceptance recovery info so the recovery info will become 
obsolete for next recovery info import
	10.Change the password on the ID file.

**Parameters :**
Input :
pIDFileName  -  pointer to name of the ID file to be recovered

NumPasswords  -  number of recovery passwords to recovery ID file

pPassword[8]  -  array of null terminated passwords to be used to recovery pIDFileName

newPassword  -  pointer to the new password to set pIDFileName to after it has been recovered

newPasswordLen  -  length of newPassword

pReserved  -  reserved - should be set to NULL

ReservedFlags  -  reserved - should be set to 0

Output :
(routine)  -  NOERROR - Successful.
	ERR_xxx - Errors returned by lower level functions.  Call to OSLoadString to interpret the error status as a string that you may display/log for the user.



**See Also :**
---
