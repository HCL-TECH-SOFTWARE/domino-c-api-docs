##### Function : Extension Manager
##### GetPasswordEMCallback - Extension Manager callback for EM_GETPASSWORD.
---
```
#include <extmgr.h>
STATUS LNPUBLIC GetPasswordEMCallback(

	DWORD  MaxPwdLen,
	DWORD far *retLength,
	char far *retPassword,
	char far *FileName,
	char far *OwnerName,
	DWORD  DataLen,
	BYTE far *Data);
```
**Description :**

EM_GETPASSWORD occurs when a user is about to be prompted for a password to 
decrypt an ID file.  EM_GETPASSWORD can only be registered with the 
EM_REG_BEFORE flag.  An extension manager hook for EM_GETPASSWORD cannot be 
called after Domino or Notes processes this operation.

**Parameters :**
Input :
MaxPwdLen  -  Longest password you may supply.

FileName  -  The name of the ID file.

OwnerName  -  The name of the owner of the ID file.

DataLen  -  The length of the extra ID information.

Data  -  The extra ID information (if any).  Domino and Notes know nothing about the contents of this information.  In order to be portable between platforms, the calling application is responsible for converting this information from cannonical to host format.

Output :
(routine)  -  
ERR_EM_CONTINUE - Continue processing.  Domino or Notes will prompt the user for a password.
ERR_BSAFE_EXTERNAL_PASSWORD - Use the value in the retPassword for the new password and do not have Domino or Notes prompt the user.
ERR_BSAFE_USER_ABORT - The password request was canceled.
ERR_BSAFE_PASSWORD_REQUIRED - A password is required for this id file.


retLength  -  Return the length of the password here.

retPassword  -  Return the password here.


**See Also :**
[EM_xxx](/reference/Symb/EM_xxx)
---
