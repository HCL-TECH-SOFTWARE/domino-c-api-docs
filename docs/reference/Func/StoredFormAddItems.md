##### Function : Form
##### StoredFormAddItems - Add form and subform design note items to a data note to support "store form with note" functionality.
---
```
#include <dbmisc.h>
STATUS LNPUBLIC StoredFormAddItems(

	DBHANDLE  hSrcDbHandle,
	DHANDLE  hSrcNote,
	DHANDLE  hDstNote,
	BOOL  bDoSubforms,
	DWORD  dwFlags);
```
**Description :**

This function adds form and subform design note items to a data note to support 
"store form with note" functionality.

**Parameters :**
Input :
hSrcDbHandle  -  Handle of the database containing the design note of the form whose items are to be added to the destination data note.

hSrcNote  -  Note handle of the form's design note to copy items from.

hDstNote  -  Note handle of the data note to copy design note items to.

bDoSubforms  -  Copy items from design notes of all subforms used by form.

dwFlags  -  Reserved for future use. Should be 0

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - Successful.

ERR_xxx - Errors returned by lower level functions.  Call OSLoadString to interpret the error code for display.



**See Also :**
[StoredFormAppendSubformToken](/domino-c-api-docs/reference/Func/StoredFormAppendSubformToken)
[StoredFormRemoveItems](/domino-c-api-docs/reference/Func/StoredFormRemoveItems)
---
