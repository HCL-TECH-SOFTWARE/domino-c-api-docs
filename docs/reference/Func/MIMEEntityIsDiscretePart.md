##### Function : MIME
##### MIMEEntityIsDiscretePart - returns TRUE if the input MIME entity is neither a message nor a multipart entity.

---
```
#include <mimedir.h>
BOOL LNPUBLIC MIMEEntityIsDiscretePart(

	PMIMEENTITY  pMimeEntity);
```
**Description :**

This function MIMEEntityIsDiscretePart returns TRUE if the input MIME entity is 
neither a multipart entity nor a message/rfc822 entity.

**Parameters :**
Input :
pMimeEntity  -  a pointer to current MIME entity.

Output :
(routine)  -  TRUE if input MIME entity is neither a multipart entity nor a message entity, otherwise FALSE.



**Sample Usage :**
```
HMIMEDIRECTORY hMIMEDir;
STATUS error;
PMIMEENTITY pRootEntity;
BOOL bIsDiscretePart = FALSE;

if (error = MIMEOpenDirectory(hNote, &hMIMEDir)) {
	goto exit;
}

if (error = MIMEGetRootEntity(hNote, &pRootEntity)) {
	goto exit;
}

bIsDiscretePart = MIMEEntityIsDiscretePart(pRootEntity);

if (error = MIMEFreeDirectory(hMIMEDir)) {
	goto exit;
}

```
**See Also :**
[MIMEEntityIsMessagePart](/reference/Func/MIMEEntityIsMessagePart)
[MIMEEntityIsMultiPart](/reference/Func/MIMEEntityIsMultiPart)
[PMIMEENTITY](/reference/Data/PMIMEENTITY)
---
