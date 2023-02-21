##### Function : Views
##### NIFGetCollation - Get current collation for a collection.
---
```
#include <nif.h>
STATUS LNPUBLIC NIFGetCollation(

	HCOLLECTION  hCollection,
	WORD *retCollationNum);
```
**Description :**

Beginning with Release 4, more than one collation may be defined for a view or 
folder.  A collation is a set of columns and sort specifications that 
determines how the view or folder will be sorted.  

When a collection is first opened, its current collation is set to 0.

**Parameters :**
Input :
hCollection  -  Handle to the open collection.

Output :
(routine)  -  Return status from this call -- indicates either sucess or what the error is. The return codes include:

NOERROR - Successfully retrieved Collation information.

ERR_xxx - Errors returned by lower level functions.  There are so many possible causes, that it is best to use the code in a call to OSLoadString and display/log the error for the user. 


retCollationNum  -  Word containing the Collation Number.


**See Also :**
[NIFOpenCollection](/domino-c-api-docs/reference/Func/NIFOpenCollection)
[NIFSetCollation](/domino-c-api-docs/reference/Func/NIFSetCollation)
---
