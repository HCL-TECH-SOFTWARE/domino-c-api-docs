##### Function : MIME
##### MIMEFreeDirectory - Free the memory associated with an open MIMEDIRECTORY.
---
##### #include <mimedir.h>
STATUS LNPUBLIC **MIMEFreeDirectory(**

	HMIMEDIRECTORY  hMIMEDir);
**Description :**
This function MIMEFreeDirectory frees the memory associated with an open 
MIMEDIRECTORY.  You must specify as input a MIMEDIRECTORY handle.

Failure to call MIMEFreeDirectory for open MIMEDIRECTORY objects will cause 
significant memory leaks.

**Parameters :**
Input :
hMIMEDir  -  A handle to an open MIMEDIRECTORY.

Output :
(routine)  -  Return status from this call.
	NOERROR - Successfully freed the MIMEDIRECTORY.
	ERR_xxx - Errors returned by lower level functions.  Call to OSLoadString to interpret the error status as a string that you may display/log for the user.



**Sample Usage :**
```
HMIMEDIRECTORY hMIMEDir;
STATUS error;

if (error = MIMEFreeDirectory(hMIMEDir)) {
	goto exit;
}

```
**See Also :**
[HMIMEDIRECTORY](D:/md_files/HMIMEDIRECTORY.md)
[MIMEOpenDirectory](D:/md_files/MIMEOpenDirectory.md)
---
