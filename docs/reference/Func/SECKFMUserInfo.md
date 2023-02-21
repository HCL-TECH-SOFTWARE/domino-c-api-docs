##### Function : User
##### SECKFMUserInfo - Get current Username and/or License ID.
---
```
#include <kfm.h>
STATUS LNPUBLIC SECKFMUserInfo(

	WORD  Function,
	char far *lpName,
	LICENSEID far *lpLicense);
```
**Description :**

This function allows access to both the Username and the LICENSEID structure 
associated with the workstation's or server's ID where this function is 
executed.

**Parameters :**
Input :
Function  -  Only one action supported:   KFM_ui_GetUserInfo - Get the Username and LICENSEID structure.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - action successful


lpName  -  The address of a text buffer in which a null-terminated user name string obtained from the local ID file is returned.   The buffer must have a minumum length of  MAXUSERNAME + 1 (see names.h).  This argument may be NULL if you do not wish this string to be returned.

lpLicense  -  The address of a LICENSEID structure in which the LICENSEID obtained from the local ID file is returned.  This argument may be NULL if you do not wish this structure to be returned.


**Sample Usage :**
```
/* Get the User Name associated w/  current USER.ID */

if (error_status = SECKFMUserInfo(KFM_ui_GetUserInfo, user_name,
                                     user_license_ptr))
   goto Exit;
```
**See Also :**
[SECKFMGetUserName](/domino-c-api-docs/reference/Func/SECKFMGetUserName)
---
