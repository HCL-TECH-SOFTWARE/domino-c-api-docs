##### Function : MIME
##### MIMEGetPrevSibling - Get the previous MIME entity at the current 'level'; e.g., the previous alternative within a multipart/alternative.
---
```
#include <mimedir.h>
STATUS LNPUBLIC MIMEGetPrevSibling(

	HMIMEDIRECTORY  hMIMEDir,
	PMIMEENTITY  pMIMEEntity,
	PMIMEENTITY *retpMIMEEntity);
```
**Description :**

This function MIMEGetPrevSibling returns a pointer to the previous sibling 
entity; i.e., the previous child entity of some parent multipart entity.  If 
there are no siblings or no previous siblings, MIMEPrevNextSibling returns a 
NULL pointer in the retpMIMEEntity output argument.


**Parameters :**
Input :
hMIMEDir  -  a handle to an open MIMEDIRECTORY.

pMIMEEntity  -  a pointer to current MIME entity.

Output :
(routine)  -  Return status from this call.
	NOERROR - Successfully accessed the MIMEDIRECTORY.
	ERR_xxx - Errors returned by lower level functions.  Call to OSLoadString to interpret the error status as a string that you may display/log for the user.



retpMIMEEntity  -  a pointer to the previous sibling entity.


**Sample Usage :**
```
HMIMEDIRECTORY hMIMEDir;
STATUS error;
PMIMEENTITY pRootEntity;
PMIMEENTITY pChildEntity;
PMIMEENTITY pEntityBeforeHTML;

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
	  if (error = MIMEGetPrevSibling(hMIMEDir, pChildEntity, 
&pEntityBeforeHTML)) {
	   goto exit
	  }
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
[HMIMEDIRECTORY](/domino-c-api-docs/reference/Data/HMIMEDIRECTORY)
[MIMEGetFirstSubpart](/domino-c-api-docs/reference/Func/MIMEGetFirstSubpart)
[MIMEGetNextSibling](/domino-c-api-docs/reference/Func/MIMEGetNextSibling)
[MIMEGetParent](/domino-c-api-docs/reference/Func/MIMEGetParent)
[PMIMEENTITY](/domino-c-api-docs/reference/Data/PMIMEENTITY)
---
