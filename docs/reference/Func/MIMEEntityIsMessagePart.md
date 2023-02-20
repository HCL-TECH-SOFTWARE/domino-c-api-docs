##### Function : MIME
##### MIMEEntityIsMessagePart - test input MIME entity to determine if it is a 'message' content type with child entities.
---
```
#include <mimedir.h>
BOOL LNPUBLIC MIMEEntityIsMessagePart(

	PMIMEENTITY  pMIMEEntity);
```
**Description :**

This function MIMEEntityIsMessagePart returns TRUE if the input MIME entity is 
a message/rfc822 MIME entity and has child entities.


**Parameters :**
Input :
pMIMEEntity  -  a pointer to current MIME entity.

Output :
(routine)  -  TRUE if input MIME entity is a message/rfc822 entity with child entities, otherwise FALSE.



**Sample Usage :**
```
HMIMEDIRECTORY hMIMEDir;
STATUS error;
PMIMEENTITY pRootEntity;
BOOL bIsMessagePart = FALSE;

if (error = MIMEOpenDirectory(hNote, &hMIMEDir)) {
	goto exit;
}

if (error = MIMEGetRootEntity(hNote, &pRootEntity)) {
	goto exit;
}

bIsMessagePart = MIMEEntityIsMessagePart(pRootEntity);

if (error = MIMEFreeDirectory(hMIMEDir)) {
	goto exit;
}

```
**See Also :**
[MIMEEntityIsDiscretePart](/reference/Func/MIMEEntityIsDiscretePart)
[MIMEEntityIsMultiPart](/reference/Func/MIMEEntityIsMultiPart)
[PMIMEENTITY](/reference/Data/PMIMEENTITY)
---
