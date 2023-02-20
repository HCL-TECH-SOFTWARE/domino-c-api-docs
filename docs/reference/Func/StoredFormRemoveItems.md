##### Function : Form
##### StoredFormRemoveItems - Remove items previously added as part of a stored form.
---
```
#include <dbmisc.h>
STATUS LNPUBLIC StoredFormRemoveItems(

	DHANDLE  hNote,
	DWORD  dwFlags);
```
**Description :**

This function removes the items from a note that have previously been added by 
StoredFormAddItems as part of a stored form.  The items removed start with '$' 
and end with "_StoredForm" or "_StoredSubform" or "_StoredSubform" followed by 
a subform index, such as  "_StoredSubform1". 

**Parameters :**
Input :
hNote  -  Handle to the data note to remove the items from.

dwFlags  -  Reserved for future use. Should be 0.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - Successful.

ERR_xxx - Errors returned by lower level functions.  Call OSLoadString to interpret the error code for display.



**See Also :**
[StoredFormAddItems](/reference/Func/StoredFormAddItems)
[StoredFormAppendSubformToken](/reference/Func/StoredFormAppendSubformToken)
---
