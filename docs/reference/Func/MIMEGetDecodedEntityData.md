##### Function : MIME
##### MIMEGetDecodedEntityData - get decoded body of input MIME entity.
---
```
#include <mimedir.h>
STATUS LNPUBLIC MIMEGetDecodedEntityData(

	DHANDLE  hNote,
	PMIMEENTITY  pMimeEntity,
	DWORD  dwEncodedOffset,
	DWORD  dwChunkLen,
	DHANDLE *phData,
	DWORD *pdwDecodedDataLen,
	DWORD *pdwEncodedDataLen);
```
**Description :**

This function MIMEGetDecodedEntityData returns the requested MIME data for the 
input MIME entity by allocating a memory block for the data, copying the data 
to the block, and returning a handle to the allocated block.  Note that the 
caller is responsible for freeing the returned memory block.


**Parameters :**
Input :
hNote  -  a handle to an open note

pMimeEntity  -  a pointer to current MIME entity (from a MIME directory constructed from hNote).

dwEncodedOffset  -  offset into the encoded MIME entity; should be 0 initially.

dwChunkLen  -  number of bytes to return in allocated block (see phData below).

Output :
(routine)  -  Return status from this call.
	NOERROR - Successfully accessed the MIMEDIRECTORY and allocated the parameter value memory.
	ERR_MISC_INVALID_ARGS - returned for various input parameter errors.
	ERR_MIME_NO_DATA - returned if no MIME data for input entity or if no data at requested offset.
	ERR_xxx - Errors returned by lower level functions.  Call to OSLoadString to interpret the error status as a string that you may display/log for the user.



phData  -  pointer to location for handle to allocated block of MIME entity data.  NULL is allowed in which case only the size of the requested data is returned.

pdwDecodedDataLen  -  pointer to location for number of decoded bytes returned for requested MIME entity data.

pdwEncodedDataLen  -  pointer to location for number of encoded bytes processed in requested MIME entity data.


**Sample Usage :**
```
HMIMEDIRECTORY hMIMEDir;
STATUS error;
PMIMEENTITY pRootEntity;
DWORD dwEncodedOffset = 0;
DWORD dwChunkLen = 1024;
DHANDLE hData;
DWORD dwDecodedDataLen;
DWORD dwEncodedDataLen;
char *pData;

if (error = MIMEOpenDirectory(hNote, &hMIMEDir)) {
	goto exit;
}

if (error = MIMEGetRootEntity(hNote, &pRootEntity)) {
	goto exit;
}

while (TRUE) {
	if (error = MIMEGetDecodedEntityData(hNote
	       pRootEntity,
	       dwEncodedOffset,
	       dwChunkLen,
	       &hData,
	       &dwDecodedDataLen,
	       &dwEncodedDataLen)) {
	 if (error == ERR_NO_MIME_DATA) {
	  break;
	 }
	 goto exit;
	}

	pData = OSLock(char, hData);

	/* write data to file
	   ...
	*/

	dwEncodedOffset += dwEncodedDataLen;
	OSUnlockAndFree(hData);
}

if (error = MIMEFreeDirectory(hMIMEDir)) {
	goto exit;
}

```
**See Also :**
---
