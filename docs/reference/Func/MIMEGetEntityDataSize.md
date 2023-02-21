##### Function : MIME
##### MIMEGetEntityDataSize - Get the data size for a MIME entity.
---
```
#include <mimedir.h>
STATUS LNPUBLIC MIMEGetEntityDataSize(

	NOTEHANDLE  hNote,
	PMIMEENTITY  pME,
	WORD  wDataType,
	DWORD *pdwDataLen);
```
**Description :**

This is a simplification of MIMEGetEntityData.  Its definition  is:

         #define MIMEGetEntityDataSize(hNote, pME, wDataType, pdwDataLen) 
MIMEGetEntityData((hNote), (pME), (wDataType), NULL, MAXDWORD, NULL, 
(pdwDataLen))

        See the MIMEGetEntityData for more detail.

**Parameters :**
Input :
hNote  -  a handle to an open note

pME  -  a pointer to current MIME entity (from a MIME directory constructed from hNote).

wDataType  -  what to get -- boundary, headers, body or all.

Output :
(routine)  -  Return status from this call.
	NOERROR - Successfully accessed the MIMEDIRECTORY and allocated the parameter value memory.
	ERR_MISC_INVALID_ARGS - returned for various input parameter errors.
	ERR_MIME_NO_DATA - returned if no MIME data for input entity or if no data at requested offset.
	ERR_xxx - Errors returned by lower level functions.  Call to OSLoadString to interpret the error status as a string that you may display/log for the user.



pdwDataLen  -  pointer to location for number of bytes in requested MIME entity data.


**See Also :**
[MIMEGetEntityData](/domino-c-api-docs/reference/Func/MIMEGetEntityData)
[MIME_ENTITY_DATA_xxx](/domino-c-api-docs/reference/Symb/MIME_ENTITY_DATA_xxx)
[NOTEHANDLE](/domino-c-api-docs/reference/Data/NOTEHANDLE)
[PMIMEENTITY](/domino-c-api-docs/reference/Data/PMIMEENTITY)
---
