##### Function : Views
##### NIFCloseCollection - Close a collection.
---
```
#include <nif.h>
STATUS LNPUBLIC NIFCloseCollection(

	HCOLLECTION  hCollection);
```
**Description :**

This function closes a collection.  You must close collections when you are 
finished using them -- doing so flushes information back to the disk and frees 
memory allocated to the collection.

**Parameters :**
Input :
hCollection  -  The handle of the collection you want to close.

Output :
(routine)  -  Return status from this call -- indicates either success, or what the error is. A successful call returns NOERROR.



**See Also :**
[NIFOpenCollection](/reference/Func/NIFOpenCollection)
[NIFUpdateCollection](/reference/Func/NIFUpdateCollection)
---
