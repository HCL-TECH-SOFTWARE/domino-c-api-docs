##### Function : MIME
##### MIMEIterateNext - Get the next MIME entity in the MIME directory
---
```
#include <mimedir.h>
STATUS LNPUBLIC MIMEIterateNext(

	HMIMEDIRECTORY  hMIMEDir,
	PMIMEENTITY  pTopMIMEEntity,
	PMIMEENTITY  pPrevMIMEEntity,
	PMIMEENTITY *retpMIMEEntity);
```
**Description :**

This function MIMEIterateNext returns a pointer to the next entity in an open 
MIMEDIRECTORY.  Note that MIMEIterateNext traverses the MIME directory in depth 
first order so that it visits the MIME entities in the order in which they 
appear in the original MIME message.


**Parameters :**
Input :
hMIMEDir  -  a handle to an open MIMEDIRECTORY.

pTopMIMEEntity  -  a pointer to topmost MIME entity for this traversal; typically the root entity.

pPrevMIMEEntity  -  a pointer to the previously visited MIME entity; usually the initial value for this is the root entity pointer.

Output :
(routine)  -  Return status from this call.
	NOERROR - Successfully accessed the MIMEDIRECTORY.
	ERR_xxx - Errors returned by lower level functions.  Call to OSLoadString to interpret the error status as a string that you may display/log for the user.



retpMIMEEntity  -  a pointer to the previously visited MIME entity; usually the initial value for this is the root entity pointer.


**Sample Usage :**
```
HMIMEDIRECTORY hMIMEDir;
STATUS error;
PMIMEENTITY pRootEntity;
PMIMEENTITY pCurrEntity;
BOOL bIsMultiPart = FALSE;
BOOL bIsMessagePart = FALSE;
BOOL bIsDiscretePart = FALSE;

if (error = MIMEOpenDirectory(hNote, &hMIMEDir)) {
	goto exit;
}

if (error = MIMEGetRootEntity(hNote, &pRootEntity)) {
	goto exit;
}

pCurrEntity = pRootEntity;
do {
	if (MIMEEntityIsMultiPart(pCurrEntity)) {
	 bIsMultiPart = TRUE;
	}
	else if (MIMEEntityIsMessagePart(pCurrEntity)) {
	 bIsMessagePart = TRUE;
	}
	else if (MIMEEntityIsDiscretePart(pCurrEntity)) {
	 bIsDiscretePart = TRUE;
	}

	error = MIMEIterateNext(hMIMEDir, pRootEntity, pCurrEntity, 
&pCurrEntity);
} while (error == NOERROR && pCurrEntity != NULL);

if (error = MIMEFreeDirectory(hMIMEDir)) {
	goto exit;
}

```
**See Also :**
[HMIMEDIRECTORY](/reference/Data/HMIMEDIRECTORY)
[PMIMEENTITY](/reference/Data/PMIMEENTITY)
---
