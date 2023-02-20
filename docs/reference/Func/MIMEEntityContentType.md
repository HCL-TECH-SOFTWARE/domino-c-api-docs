##### Function : MIME
##### MIMEEntityContentType - Return the content-type for the input MIME entity.
---
```
#include <mimedir.h>
MIMESYMBOL LNPUBLIC  MIMEEntityContentType(

	PMIMEENTITY  pMIMEEntity);
```
**Description :**

This function MIMEEntityContentType returns the content type of the input MIME 
Entity; i.e., a MIMESYMBOL.

**Parameters :**
Input :
pMIMEEntity  -  a pointer to a MIME entity.

Output :
(routine)  -  the MIMESYMBOL for the entity's content type.



**Sample Usage :**
```
HMIMEDIRECTORY hMIMEDir;
STATUS error;
PMIMEENTITY pMIMEEntity;
BOOL bIsMultiPart = FALSE;

if (error = MIMEOpenDirectory(hNote, &hMIMEDir)) {
	goto exit;
}

if (error = MIMEGetRootEntity(hNote, &pMIMEEntity)) {
	goto exit;
}

if (MIMEEntityContentType(pMIMEEntity) == MIME_SYMBOL_MULTIPART) {
	bIsMultiPart = TRUE;
}

if (error = MIMEFreeDirectory(hMIMEDir)) {
	goto exit;
}

```
**See Also :**
[MIMEEntityContentSubtype](/reference/Func/MIMEEntityContentSubtype)
[MIMESYMBOL](/reference/Data/MIMESYMBOL)
[PMIMEENTITY](/reference/Data/PMIMEENTITY)
---
