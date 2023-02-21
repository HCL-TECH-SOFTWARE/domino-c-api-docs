##### Function : MIME
##### MIMEEntityGetHeader - get the string value for the indicated header; returns a pointer to everything after the field name, colon.
---
```
#include <mimedir.h>
const char * LNPUBLIC MIMEEntityGetHeader(

	PMIMEENTITY  pMIMEEntity,
	MIMESYMBOL  symKey);
```
**Description :**

This function MIMEGetEntityHeader returns a pointer to the string value of the 
header indicated by 'symKey'.  The string is everything after the header field 
name and colon.  If the header is not found, MIMEGetEntityHeader returns NULL.

**Parameters :**
Input :
pMIMEEntity  -  a pointer to current MIME entity.

symKey  -   the MIMESYMBOL defined for the header.

Output :
(routine)  -  pointer to the header's string value.



**Sample Usage :**
```
HMIMEDIRECTORY hMIMEDir;
STATUS error;
PMIMEENTITY pRootEntity;
const char *pszHeaderValue;

if (error = MIMEOpenDirectory(hNote, &hMIMEDir)) {
	goto exit;
}

if (error = MIMEGetRootEntity(hNote, &pRootEntity)) {
	goto exit;
}

pszHeaderValue = MIMEEntityGetHeader(pRootEntity, MIME_SYMBOL_CONTENT_TYPE);

if (error = MIMEFreeDirectory(hMIMEDir)) {
	goto exit;
}

```
**See Also :**
[MIMESYMBOL](/domino-c-api-docs/reference/Data/MIMESYMBOL)
[PMIMEENTITY](/domino-c-api-docs/reference/Data/PMIMEENTITY)
---
