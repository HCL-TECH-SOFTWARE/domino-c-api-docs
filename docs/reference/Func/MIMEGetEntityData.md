##### Function : MIME
##### MIMEGetEntityData - get the data for a MIME entity.  May fetch boundary, headers, and body separately or all together.

---
```
#include <mimedir.h>
STATUS LNPUBLIC MIMEGetEntityData(

	NOTEHANDLE  hNote,
	PMIMEENTITY  pME,
	WORD  wDataType,
	DWORD  dwOffset,
	DWORD  dwOffset,
	DHANDLE *phData,
	DWORD *pdwDataLen);
```
**Description :**

This function MIMEGetEntityData returns the requested MIME data for the input 
MIME entity by allocating a memory block for the data, copying the data to the 
block, and returning a handle to the allocated block.  Note that the caller is 
responsible for freeing the returned memory block and that the MIME entity data 
is returned in its original encoding; e.g., as base64 encoded data.

The caller may use the wDataType argument to specify which elements of the MIME 
entity data MIMEGetEntityData should return:

MIME_ENTITY_DATA_BOUNDARY - Get boundary only.
MIME_ENTITY_DATA_HEADERS - Get headers only.
MIME_ENTITY_DATA_BODY - Get body only.
MIME_ENTITY_DATA_RFC822TEXT - Get boundary, headers and body

**Parameters :**
Input :
hNote  -  a handle to an open note

pME  -  a pointer to current MIME entity (from a MIME directory constructed from hNote).

wDataType  -  what to get -- boundary, headers, body or all.

dwOffset  -  offset into MIME entity; should be 0 initially.

dwOffset  -  number of bytes to return in allocated block (see phData below).

Output :
(routine)  -  Return status from this call.
	NOERROR - Successfully accessed the MIMEDIRECTORY and allocated the parameter value memory.
	ERR_MISC_INVALID_ARGS - returned for various input parameter errors.
	ERR_MIME_NO_DATA - returned if no MIME data for input entity or if no data at requested offset.
	ERR_xxx - Errors returned by lower level functions.  Call to OSLoadString to interpret the error status as a string that you may display/log for the user.



phData  -  pointer to location for handle to allocated block of MIME entity data.  NULL is allowed in which case only the size of the requested data is returned.

pdwDataLen  -  pointer to location for number of bytes in requested MIME entity data.


**Sample Usage :**
```
HMIMEDIRECTORY hMIMEDir;
STATUS error;
PMIMEENTITY pRootEntity;
DWORD dwOffset = 0;
DWORD dwChunkLen = 1024;
DHANDLE hData;
DWORD dwDataLen;
char *pData;

if (error = MIMEOpenDirectory(hNote, &hMIMEDir)) {
	goto exit;
}

if (error = MIMEGetRootEntity(hNote, &pRootEntity)) {
	goto exit;
}

while (TRUE) {
	if (error = MIMEGetEntityData(hNote
	     pRootEntity,
	     MIME_ENTITY_DATA_RFC822TEXT,
	     dwOffset,
	     dwChunkLen,
	     &hData,
	     &dwDataLen)) {
	 if (error == ERR_NO_MIME_DATA) {
	  break;
	 }
	 goto exit;
	}

	pData = OSLock(char, hData);

	/* write data to file
	   ...
	*/

	dwOffset += dwDataLen;
	OSUnlockAndFree(hData);
}

if (error = MIMEFreeDirectory(hMIMEDir)) {
	goto exit;
}

```
**See Also :**
[MIME_ENTITY_DATA_xxx](/reference/Symb/MIME_ENTITY_DATA_xxx)
[NOTEHANDLE](/reference/Data/NOTEHANDLE)
[PMIMEENTITY](/reference/Data/PMIMEENTITY)
---
