##### Function : MIME
##### MIMEFreeEntityDataObject - free the database object (i.e., file attachment) which contains entity's MIME data.
---
```
#include <mimedir.h>
STATUS LNPUBLIC MIMEFreeEntityDataObject(

	NOTEHANDLE  hNote,
	PMIMEENTITY  pEntity);
```
**Description :**

If the input MIME entity's data is stored in a database object (i.e., a file 
attachment), the function MIMEFreeEntityDataObject deletes the $FILE item and 
associated database object for the MIME entity without deleting the MIME 
entity's item.  If the MIME entity's data is not stored in a database object, 
the function does nothing.


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




**Sample Usage :**
```
HMIMEDIRECTORY hMIMEDir;
STATUS error;
PMIMEENTITY pRootEntity;
DWORD dwFlags;

if (error = MIMEOpenDirectory(hNote, &hMIMEDir)) {
	goto exit;
}

if (error = MIMEGetRootEntity(hNote, &pRootEntity)) {
	goto exit;
}

if (error = MIMEGetEntityPartFlags(hNote, pRootEntity, &dwFlags)) {
	goto exit;
}

if ((dwFlags & (MIME_PART_BODY_IN_DBOBJECT|MIME_PART_SHARED_DBOBJECT)) == 
MIME_PART_BODY_IN_DBOBJECT) {
	if (error = MIMEFreeEntityDataObject(hNote, pRootEntity)) {
	 goto exit;
	}
}

if (error = MIMEFreeDirectory(hMIMEDir)) {
	goto exit;

```
**See Also :**
[NOTEHANDLE](/reference/Data/NOTEHANDLE)
[PMIMEENTITY](/reference/Data/PMIMEENTITY)
---
