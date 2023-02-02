##### Function : MIME
##### MIMEGetRootEntity - Get the root entity of the MIME directory; i.e., the first part in the MIME message.
---
##### #include <mimedir.h>
STATUS LNPUBLIC **MIMEGetRootEntity(**

	HMIMEDIRECTORY  hMIMEDir,
	PMIMEENTITY *retpMIMEEntity);
**Description :**
This function MIMEGetRootEntity returns a pointer to the root entity of an open 
MIMEDIRECTORY.  The "root entity" is the first part in the MIME message from 
which the directory was constructed.  The root entity pointer can be used in 
other MIME API calls to traverse the directory or to get specific information 
about the root entity; e.g., the MIME content type.

**Parameters :**
Input :
hMIMEDir  -  a handle to an open MIMEDIRECTORY.

Output :
(routine)  -  Return status from this call.
	NOERROR - Successfully accessed the MIMEDIRECTORY.
	ERR_xxx - Errors returned by lower level functions.  Call to OSLoadString to interpret the error status as a string that you may display/log for the user.



retpMIMEEntity  -  a pointer to the directory's root entity.

**Sample Usage :**
```
HMIMEDIRECTORY hMIMEDir;
STATUS error;
PMIMEENTITY pMIMEEntity;
BOOL bIsMultiPart = FALSE;
BOOL bIsMessagePart = FALSE;
BOOL bIsDiscretePart = FALSE;

if (error = MIMEOpenDirectory(hNote, &hMIMEDir)) {
	goto exit;
}

if (error = MIMEGetRootEntity(hNote, &pMIMEEntity)) {
	goto exit;
}

if (MIMEEntityIsMultiPart(pMIMEEntity)) {
	bIsMultiPart = TRUE;
}
else if (MIMEEntityIsMessagePart(pMIMEEntity)) {
	bIsMessagePart = TRUE;
}
else if (MIMEEntityIsDiscretePart(pMIMEEntity)) {
	bIsDiscretePart = TRUE;
}

if (error = MIMEFreeDirectory(hMIMEDir)) {
	goto e

```
**See Also :**
[HMIMEDIRECTORY](D:/md_files/HMIMEDIRECTORY.md)
[PMIMEENTITY](D:/md_files/PMIMEENTITY.md)
---
