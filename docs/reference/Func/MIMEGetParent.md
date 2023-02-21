##### Function : MIME
##### MIMEGetParent - get a pointer to the parent MIME entity for the input MIME entity.

---
```
#include <mimedir.h>
STATUS LNPUBLIC MIMEGetParent(

	HMIMEDIRECTORY  hMIMEDir,
	PMIMEENTITY  pMIMEEntity,
	PMIMEENTITY *retpMIMEEntity);
```
**Description :**

This function MIMEGetParent returns a pointer to the parent MIME entity for the 
input MIME entity.  If the input MIME entity has no parent --i.e., it is the 
root MIME entity for the MIME directory-- MIMEGetParent returns a NULL pointer 
in the retpMIMEEntity output argument.

**Parameters :**
Input :
hMIMEDir  -  a handle to an open MIMEDIRECTORY.

pMIMEEntity  -  a pointer to current MIME entity.

Output :
(routine)  -  Return status from this call.
	NOERROR - Successfully accessed the MIMEDIRECTORY.
	ERR_xxx - Errors returned by lower level functions.  Call to OSLoadString to interpret the error status as a string that you may display/log for the user.



retpMIMEEntity  -  a pointer to the parent entity.


**Sample Usage :**
```
HMIMEDIRECTORY hMIMEDir;
STATUS error;
PMIMEENTITY pRootEntity;
PMIMEENTITY pCurrEntity;
PMIMEENTITY pHTMLParentEntity;

if (error = MIMEOpenDirectory(hNote, &hMIMEDir)) {
	goto exit;
}

if (error = MIMEGetRootEntity(hNote, &pRootEntity)) {
	goto exit;
}

pCurrEntity = pRootEntity;

while (pCurrEntity) {
	if (MIMEEntityContentType(pChildEntity) == MIME_SYMBOL_HTML) {
	 if (error = MIMEGetParent(hMIMEDir, pChildEntity, &pHTMLParentEntity)) 
{
	  goto exit
	 }
	 break;
	}
	if (error = MIMEIterateNext(hMIMEDir, pRootEntity, pCurrEntity, 
&pCurrEntity)) {
	 goto exit;
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
[MIMEGetPrevSibling](/domino-c-api-docs/reference/Func/MIMEGetPrevSibling)
[PMIMEENTITY](/domino-c-api-docs/reference/Data/PMIMEENTITY)
---
