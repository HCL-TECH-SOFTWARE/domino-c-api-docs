##### Function : Form
##### SubformRemove - Remove a subform from a form or subform design note.
---
```
#include <easycd.h>
STATUS LNPUBLIC SubformRemove(

	DBHANDLE  hDB,
	char *pSubForm,
	char *pForm,
	DWORD  Flags);
```
**Description :**

This function removes a subform from a form or subform.

**Parameters :**
Input :
hDB  -  Handle to the database.

pSubForm  -  Subform name to remove.

pForm  -  Parent form name or subform name from which the specified subform is to be removed.

Flags  -  Reserved for future use.  Specify  0L.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR
ERR_xxx - Errors returned by lower level functions.  There are so many possible causes, that it is best to use the code in a call to OSLoadString and display/log the error for the user.



**See Also :**
[SubformInsert](/domino-c-api-docs/reference/Func/SubformInsert)
---
