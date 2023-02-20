##### Function : IDs
##### SECKFMSwitchToIDFile - Switch to a new ID.
---
```
#include <kfm.h>
STATUS LNPUBLIC SECKFMSwitchToIDFile(

	char *pIDFileName,
	char *pPassword,
	char *pUserName,
	WORD  MaxUserNameLength,
	DWORD  Flags,
	void *pReserved);
```
**Description :**

This function switches to the specified ID file and returns the user name 
associated with it.  Multiple passwords are not supported.

NOTE: This function should only be used in a C API stand alone application.

**Parameters :**
Input :
pIDFileName  -  Points to a null-terminated string containing the path to the ID file that is to be switched to.

pPassword  -  Points to a null-terminated string containing the password of the ID file that is to be switched to.

MaxUserNameLength  -  Maximum length of buffer pointed to by pUserName.

Flags  -  Optional, may be set to 0.  See fKFM_switchid_xxx.  If fKFM_switchid_DontSetEnvVar is not specified, the notes.ini file (either ServerKeyFileName or KeyFileName) is modified to reflect the ID change.

pReserved  -  Reserved, should be set to NULL.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is.   The return codes include:

NOERROR - Action successful.

ERR_NOEXIST - The ID file specified does not exist.

ERR_BSAFE_BADPASSWORD - The password specified is incorrect.

ERR_BSAFE_TOOSMALL - The MaxUserNameLength specified is too small.

ERR_BSAFE_SUBPROCESS - A sub-process cannot change to a new ID file or prompt for passwords.

ERR_xxx  -  Various OS, and KFM errors.  Call to OSLoadString to interpret the error status as a string that you may display/log for the user.


pUserName  -  Points to a buffer where the user name, in the ID file that is to be switched to, will be returned.


**See Also :**
[fKFM_switchid_xxx](/reference/Symb/fKFM_switchid_xxx)
---
