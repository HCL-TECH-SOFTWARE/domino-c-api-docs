##### Function : Recovery
##### SECExtractRecoveryPassword - Extract password from a backup ID file
---
##### #include <kfm.h>
STATUS LNPUBLIC **SECExtractRecoveryPassword(**

	KFHANDLE  hKFC,
	char *pIDFileName,
	char *RecoveryPassword,
	WORD  MaxRecoveryPasswordLen,
	WORD *retRecoveryPasswordLen,
	TIMEDATE *retCreationTimeDate,
	TIMEDATE *retAcceptanceTimeDate,
	void *pReserved,
	DWORD  ReservedFlags);
**Description :**
Given a backup ID file and the hKFC of a recovery authority, extract the 
recovery password.
Routine:
	1.Get the RA's private key out of the hKFC.
	2.Open the encrypted backup ID file to be recovered (pointed to by 
pIDFileName).
	3.Get the keys extra from the just opened file
	4.Extract the creation timedate from the keys extra
 5.Get the cookies extra from the just opened file
	6.Extract the acceptance timedate out of the cookies extra.
	7. Find the corresponding recovery password to the RA's private key in 
the cookies extra.
	8. Return the recovery password to the caller in RecoveryPassword and 
set the length in retRecoveryPasswordLen.
**Parameters :**
Input :
hKFC  -  key file context of the recovery authority's ID file

pIDFileName  -  pointer to name of backed up ID file to be parsed for recovery password

RecoveryPassword  -  pointer to recovery password buffer to be filled in

MaxRecoveryPasswordLen  -  max size of pRecoveryPassword

pReserved  -  reserved - should be set to NULL

ReservedFlags  -  reserved - should be set to 0

Output :
(routine)  -  NOERROR - Successful.
	ERR_xxx - Errors returned by lower level functions.  Call to OSLoadString to interpret the error status as a string that you may display/log for the user.


RecoveryPassword  -  pointer to recovery password buffer to be filled in

retRecoveryPasswordLen  -  pointer to length of recovery password 

retCreationTimeDate  -  returns the timedate of when the recovery information was created.

retAcceptanceTimeDate  -  returns the timedate of when the recovery information was accepted.

**See Also :**
[](D:/md_files/.md)
---
