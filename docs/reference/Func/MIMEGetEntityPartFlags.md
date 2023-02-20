##### Function : MIME
##### MIMEGetEntityPartFlags - get the MIME_PART_xxx flags for the input entity.
---
```
#include <mimedir.h>
STATUS LNPUBLIC MIMEGetEntityPartFlags(

	NOTEHANDLE  hNote,
	PMIMEENTITY  pEntity,
	DWORD *pdwFlags);
```
**Description :**

The function MIMEGetEntityPartFlags returns the MIME_PART_xxx flags for the 
input MIME entity.  The flags are:

MIME_PART_HAS_BOUNDARY  - part has a boundary; i.e., it is a child of a 
multipart entity.
MIME_PART_HAS_HEADERS  - part has headers; e.g., Content-Type.
MIME_PART_BODY_IN_DBOBJECT  - part data is stored in a file attachment
MIME_PART_SHARED_DBOBJECT  - part data is stored in an attachment and it is 
shared with another referrer. (rare usage.)


**Parameters :**
Input :
hNote  -  a handle to an open note

pEntity  -  a pointer to current MIME entity (from a MIME directory constructed from hNote).

Output :
(routine)  -  Return status from this call.
	NOERROR - Successfully accessed the MIMEDIRECTORY and allocated the parameter value memory.
	ERR_MISC_INVALID_ARGS - returned for various input parameter errors.
	ERR_MIME_NO_DATA - returned if no MIME data for input entity or if no data at requested offset.
	ERR_xxx - Errors returned by lower level functions.  Call to OSLoadString to interpret the error status as a string that you may display/log for the user.



pdwFlags  -  the returned bit flags; always set to 0 on entry by MIMEGetEntityPartFlags.


**Sample Usage :**
```
HMIMEDIRECTORY hMIMEDir;
STATUS error;
PMIMEENTITY pRootEntity;
DWORD dwFlags;
BOOL bPartHasBoundary;
BOOL bPartHasHeaders;
BOOL bPartDataInDBObject;


if (error = MIMEOpenDirectory(hNote, &hMIMEDir)) {
	goto exit;
}

if (error = MIMEGetRootEntity(hNote, &pRootEntity)) {
	goto exit;
}

if (error = MIMEGetEntityPartFlags(hNote, pRootEntity, &dwFlags)) {
	goto exit;
}

bPartHasBoundary    = (dwFlags & MIME_PART_HAS_BOUNDARY) != 0;
bPartHasHeaders     = (dwFlags & MIME_PART_HAS_HEADERS) != 0;
bPartDataInDBObject = (dwFlags & MIME_PART_BODY_IN_DBOBJECT) != 0;


if (error = MIMEFreeDirectory(hMIMEDir)) {
	goto exit;
}

```
**See Also :**
[MIME_PART_xxx](/reference/Symb/MIME_PART_xxx)
[NOTEHANDLE](/reference/Data/NOTEHANDLE)
[PMIMEENTITY](/reference/Data/PMIMEENTITY)
---
