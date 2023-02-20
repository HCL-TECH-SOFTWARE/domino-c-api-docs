##### Function : MIME
##### MIMEEntityContentID - get the string for the Content-ID header; returns everything after the field name, colon.
---
```
#include <mimedir.h>
const char * LNPUBLIC MIMEEntityContentID(

	PMIMEENTITY  pMIMEEntity);
```
**Description :**

This function MIMEEntityContentID returns a pointer to the string value of the 
Content-ID header.  The string is everything after the header field name and 
colon.  If the current entity does not have a Content-ID header, 
MIMEEntityContentID returns NULL.

**Parameters :**
Input :
pMIMEEntity  -  a pointer to current MIME entity.

Output :
(routine)  -  pointer to the Content-ID header's string value.



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

pszHeaderValue = MIMEEntityContentID(pRootEntity);

if (error = MIMEFreeDirectory(hMIMEDir)) {
	goto exit;
}

```
**See Also :**
[PMIMEENTITY](/reference/Data/PMIMEENTITY)
---
