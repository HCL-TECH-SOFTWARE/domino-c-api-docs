##### Function : MIME
##### MIMEEntityIsMultiPart - test input MIME entity to determine if it is a multipart content type.

---
##### #include <mimedir.h>
BOOL LNPUBLIC **MIMEEntityIsMultiPart(**

	PMIMEENTITY  pMimeEntity);
**Description :**
This function MIMEEntityIsMultiPart returns TRUE if the input MIME entity is a 
multipart entity and has child entities.

**Parameters :**
Input :
pMimeEntity  -  a pointer to current MIME entity.

Output :
(routine)  -  TRUE if input MIME entity is a multipart entity with child entities, otherwise FALSE.



**Sample Usage :**
```
HMIMEDIRECTORY hMIMEDir;
STATUS error;
PMIMEENTITY pRootEntity;
BOOL bIsMultiPart = FALSE;

if (error = MIMEOpenDirectory(hNote, &hMIMEDir)) {
	goto exit;
}

if (error = MIMEGetRootEntity(hNote, &pRootEntity)) {
	goto exit;
}

bIsMultiPart = MIMEEntityIsMultiPart(pRootEntity);

if (error = MIMEFreeDirectory(hMIMEDir)) {
	goto exit;
}

```
**See Also :**
[MIMEEntityIsDiscretePart](D:/md_files/MIMEEntityIsDiscretePart.md)
[MIMEEntityIsMessagePart](D:/md_files/MIMEEntityIsMessagePart.md)
[PMIMEENTITY](D:/md_files/PMIMEENTITY.md)
---
