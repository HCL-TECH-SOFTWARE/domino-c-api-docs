##### Function : MIME
##### MIMEGetNextSibling - Get the next MIME entity at the current 'level'; e.g., the next alternative within a multipart/alternative.
---
```
#include <mimedir.h>
STATUS LNPUBLIC MIMEGetNextSibling(

	HMIMEDIRECTORY  hMIMEDir,
	PMIMEENTITY  pMIMEEntity,
	PMIMEENTITY *retpMIMEEntity);
```
**Description :**

This function MIMEGetNextSibling returns a pointer to the next sibling entity; 
i.e., the next child entity of some parent multipart entity.  If there are no 
siblings or no subsequent siblings, MIMEGetNextSibling returns a NULL pointer 
in the retpMIMEEntity output argument.

**Parameters :**
Input :
hMIMEDir  -  a handle to an open MIMEDIRECTORY.

pMIMEEntity  -  a pointer to current MIME entity.

Output :
(routine)  -  Return status from this call.
	NOERROR - Successfully accessed the MIMEDIRECTORY.
	ERR_xxx - Errors returned by lower level functions.  Call to OSLoadString to interpret the error status as a string that you may display/log for the user.



retpMIMEEntity  -  a pointer to the next sibling entity.


**Sample Usage :**
```
HMIMEDIRECTORY hMIMEDir;
STATUS error;
PMIMEENTITY pRootEntity;
PMIMEENTITY pChildEntity;

if (error = MIMEOpenDirectory(hNote, &hMIMEDir)) {
	goto exit;
}

if (error = MIMEGetRootEntity(hNote, &pRootEntity)) {
	goto exit;
}

if (MIMEEntityIsMultiPart(pRootEntity)) {
	if (error = MIMEGetFirstSubPart(hMIMEDir, pRootEntity, &pChildEntity)) {
	 goto exit;
	}

	while (pChildEntity) {
	 if (MIMEEntityContentType(pChildEntity) == MIME_SYMBOL_HTML) {
	  break;
	 }

	 if (error = MIMEGetNextSibling(hMIMEDir, pChildEntity, &pChildEntity)) 
{
	  goto exit;
	 }
	}
}

if (error = MIMEFreeDirectory(hMIMEDir)) {
	goto exit;
}

```
**See Also :**
[HMIMEDIRECTORY](/reference/Data/HMIMEDIRECTORY)
[MIMEGetFirstSubpart](/reference/Func/MIMEGetFirstSubpart)
[MIMEGetParent](/reference/Func/MIMEGetParent)
[MIMEGetPrevSibling](/reference/Func/MIMEGetPrevSibling)
[PMIMEENTITY](/reference/Data/PMIMEENTITY)
---
