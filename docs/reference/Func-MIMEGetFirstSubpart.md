##### Function : MIME
##### MIMEGetFirstSubpart - Get the first child of the current multipart entity.
---
##### #include <mimedir.h>
STATUS LNPUBLIC **MIMEGetFirstSubpart(**

	HMIMEDIRECTORY  hMIMEDir,
	PMIMEENTITY  pMIMEEntity,
	PMIMEENTITY *retpMIMEEntity);
**Description :**
This function MIMEGetFirstSubpart returns a pointer to the input entity's first 
child entity, if the input entity is a composite entity; i.e., a multipart 
entity.  If the current entity is not a multipart entity or if it contains no 
child entities, then MIMEGetFirstSubpart returns a NULL pointer in the output 
argument, retpMIMEEntity.
**Parameters :**
Input :
hMIMEDir  -  a handle to an open MIMEDIRECTORY.

pMIMEEntity  -  a pointer to a MIME entity.  This should be a multipart entity.

Output :
(routine)  -  Return status from this call.
	NOERROR - Successfully accessed the directory.
	ERR_xxx - Errors returned by lower level functions.  Call to OSLoadString to interpret the error status as a string that you may display/log for the user.



retpMIMEEntity  -  a pointer to the input entity's first child entity.

**Sample Usage :**
```
HMIMEDIRECTORY hMIMEDir;
STATUS error;
PMIMEENTITY pRootEntity;
PMIMEENTITY pChildEntity;
MIMESYMBOL  msContentType;

if (error = MIMEOpenDirectory(hNote, &hMIMEDir)) {
	goto exit;
}

if (error = MIMEGetRootEntity(hNote, &pRootEntity)) {
	goto exit;
}

if (MIMEEntityIsMultiPart(pRootEntity)) {
	if (error = MIMEGetFirstSubpart(hMIMEDir, pRootEntity, &pChildEntity)) {
	 goto exit;
	}

	msContentType = MIMEEntityContentType(pChildEntity);
}

if (error = MIMEFreeDirectory(hMIMEDir)) {
	goto exit;
}

```
**See Also :**
[HMIMEDIRECTORY](D:/md_files/HMIMEDIRECTORY.md)
[MIMEGetNextSibling](D:/md_files/MIMEGetNextSibling.md)
[MIMEGetParent](D:/md_files/MIMEGetParent.md)
[MIMEGetPrevSibling](D:/md_files/MIMEGetPrevSibling.md)
[PMIMEENTITY](D:/md_files/PMIMEENTITY.md)
---
