##### Function : OLE
##### NSFNoteAttachOLE2Object - Attach an OLE structured storage object to the specified Note, creating the OLE $FILE objects using the specified storage file.
---
```
#include <nsfole.h>
STATUS LNPUBLIC NSFNoteAttachOLE2Object(

	NOTEHANDLE  hNote,
	char *pszFileName,
	char *pszObjectName,
	BOOL  fCreateInfoItem,
	char *pszObjDescription,
	char *pszFieldName,
	OLE_GUID *pOleObjClassID,
	WORD  wDisplayFormat,
	BOOL  fScripted,
	BOOL  fOleControl,
	DWORD  dwFlags);
```
**Description :**

Attach an OLE structured storage object to the specified Note, creating the OLE 
$FILE objects using the specified storage file.  Also, optionally create an 
$OLEOBJINFO note item using the specified parameters.

**Parameters :**
Input :
hNote  -  NSF Note Handle to open note

pszFileName  -  Input file name containing the OLE structured storage file

pszObjectName  -  The name of the NSF $FILE extendable file object to create. This MUST match the one created in the CDOLEBEGIN record in the body of the document.

fCreateInfoItem  -  TRUE to create a $OLEOBJINFO item.  The remaining parameters are propogated to the OLEOBJINFO item.

pszObjDescription  -  Object user description, i.e. "My Worksheet"

pszFieldName  -  Field name in which the OLE object resides within the document.

pOleObjClassID  -  The OLE object's GUID

wDisplayFormat  -  Visual rendering format, like bitmap, metafile,  DDEFORMAT_xxx from editods.h

fScripted  -  True if object is scripted (for ActiveX).  If this is true, it's up to the caller to attach the associated Lotus script source and object code to this note, using the following naming convention <xxxx>.lso for the Lotus Script compiled object code and <xxxx>.lss for the LotusScript source, where "xxxx" is identical to the the ObjectName used above.  If Object name is "foo" then "foo.lss" has the lotus script source, and "foo.lso" has the lotus script object code.

fOleControl  -  True if this object is registered an OLE ActiveX

dwFlags  -  see OLE_xxxISTORAGE_SUPPORTED

Output :
(routine)  -  Return indicates either success or what the error is. The return codes include: 

NOERROR - Operation was successful.

ERR_NSF_NOT_SUPPORTED - This function is not supported on this platform.  In Release 5.0 through 5.0.7 of Domino and Notes, this function was supported on Windows 32-bit platforms only.  As of Release 5.0.8, this function is supported on all Domino and Notes platforms.

ERR_xxx - STATUS returned from a lower level Notes function call.  Use OSLoadString and display/log the error.



**See Also :**
[NSFNoteDeleteOLE2Object](/domino-c-api-docs/reference/Func/NSFNoteDeleteOLE2Object)
[NSFNoteExtractOLE2Object](/domino-c-api-docs/reference/Func/NSFNoteExtractOLE2Object)
[OLE_xxxISTORAGE_SUPPORTED](/domino-c-api-docs/reference/Symb/OLE_xxxISTORAGE_SUPPORTED)
---
