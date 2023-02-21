##### Function : MIME
##### MIMEEntityContentSubtype - return the content subtype for the input MIME entity.

---
```
#include <mimedir.h>
MIMESYMBOL LNPUBLIC MIMEEntityContentSubtype(

	PMIMEENTITY  pMIMEEntity);
```
**Description :**

This function MIMEEntityContentSubtype returns the content subtype of the input 
MIME Entity; i.e., a MIMESYMBOL.

**Parameters :**
Input :
pMIMEEntity  -  a pointer to a MIME entity.

Output :
(routine)  -  the MIMESYMBOL for the entity's content subtype.




**Sample Usage :**
```
HMIMEDIRECTORY hMIMEDir;
STATUS error;
PMIMEENTITY pMIMEEntity;
BOOL bIsAlternative = FALSE;

if (error = MIMEOpenDirectory(hNote, &hMIMEDir)) {
	goto exit;
}

if (error = MIMEGetRootEntity(hNote, &pMIMEEntity)) {
	goto exit;
}

if (MIMEEntityContentType(pMIMEEntity) == MIME_SYMBOL_MULTIPART
&&  MIMEEntityContentSubtype(pMIMEEntity) == MIME_SYMBOL_ALTERNATIVE) {
	bIsAlternative = TRUE;
}

if (error = MIMEFreeDirectory(hMIMEDir)) {
	goto exit;
}

```
**See Also :**
[MIMEEntityContentType](/domino-c-api-docs/reference/Func/MIMEEntityContentType)
[PMIMEENTITY](/domino-c-api-docs/reference/Data/PMIMEENTITY)
---
