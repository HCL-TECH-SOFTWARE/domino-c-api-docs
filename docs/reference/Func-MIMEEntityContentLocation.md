##### Function : MIME
##### MIMEEntityContentLocation - get the string for the Content-Location header; returns everything after the field name, colon.
---
##### #include <mimedir.h>
const char * LNPUBLIC **MIMEEntityContentLocation(**

	PMIMEENTITY  pMIMEEntity);
**Description :**
This function MIMEEntityContentLocation returns a pointer to the string value 
of the Content-Location header.  The string is everything after the header 
field name and colon.  If the current entity does not have a Content-Location 
header, MIMEEntityContentLocation returns NULL.

**Parameters :**
Input :
pMIMEEntity  -  a pointer to current MIME entity

Output :
(routine)  -  pointer to the Content-Location header's string value.


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

pszHeaderValue = MIMEEntityContentLocation(pRootEntity);

if (error = MIMEFreeDirectory(hMIMEDir)) {
	goto exit;
}

```
**See Also :**
[PMIMEENTITY](D:/md_files/PMIMEENTITY.md)
---
