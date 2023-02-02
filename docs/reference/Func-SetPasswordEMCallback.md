##### Function : Extension Manager
##### SetPasswordEMCallback - Extension Manager callback for EM_SETPASSWORD
---
##### #include <extmgr.h>
STATUS LNPUBLIC **SetPasswordEMCallback(**

	DWORD  MaxPwdLen,
	DWORD far *retLength,
	char far *retPassword,
	char far *FileName,
	char far *OwnerName,
	DWORD  DataLen,
	BYTE far *Data,
	DWORD  MaxNewData,
	DWORD far *retNewDataLen,
	BYTE far *retNewData);
**Description :**
EM_SETPASSWORD occurs when an ID file password is being set, either by a user 
or by administrator action.  EM_SETPASSWORD can only be registered with the 
EM_REG_BEFORE flag.  An extension manager hook for EM_SETPASSWORD cannot be 
called after Domino or Notes processes this operation.
**Parameters :**
Input :
MaxPwdLen  -  Longest password you may supply.

FileName  -  The name of the ID file.

OwnerName  -  The name of the owner of the ID file.

DataLen  -  The old length of the extra ID information.

Data  -  The old value of the extra ID information.

MaxNewData  -  The maximum amount of extra ID information you may supply.

Output :
(routine)  -  ERR_EM_CONTINUE - Continue processing.  Notes will prompt the user for a new password.
ERR_BSAFE_EXTERNAL_PASSWORD - Use the value in the retPassword for the new password and do not have Notes prompt the user.
ERR_BSAFE_EXTERNAL_PWD_AND_DATA - Use the value in the retPassword for the new password and save the data returned in retNewData.  Do not have Notes prompt the user.
ERR_BSAFE_USER_ABORT - The password request was canceled.
ERR_BSAFE_PASSWORD_REQUIRED - A password is required for this id file.


retLength  -  Return the length of the new password.

retPassword  -  Return the new password here.

retNewDataLen  -  Return the length of the new ID information (if any).

retNewData  -  Optional.  Return the new ID information here.    Domino and Notes know nothing about the contents of this information.  In order to be portable between platforms, the calling application is responsible for converting this information from host to cannonical format.  The extension manager must return ERR_BSAFE_EXTERNAL_PWD_AND_DATA if this new information is to be stored in the ID file.

**See Also :**
[EM_xxx](D:/md_files/EM_xxx.md)
---
