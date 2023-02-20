##### Function : Views
##### NIFGetCollectionData - Get information about the collection
---
```
#include <nif.h>
STATUS LNPUBLIC NIFGetCollectionData(

	HCOLLECTION  hCollection,
	DHANDLE far *rethCollData);
```
**Description :**

Retrieve detailed information about the collection itself, such as the number 
of documents in the collection and the total size of the document entries in 
the collection.  This function returns a handle to memory containing a 
COLLECTIONDATA structure;  please see that reference entry for more 
information.  Upon successful completion of the NIFGetCollectionData routine, a 
handle is returned as an output parameter.  The caller must lock this handle 
using OSLock in order to access the COLLECTIONDATA structure, and unlock it 
using OSUnlock and free it using OSMemFree when it is done.

 NIFGetCollectionData is only useful for providing information about a 
collection which is not categorized.  The index of a categorized collection is 
implemented using nested B-Trees, and it is not possible to provide useful 
information about all of the B-Trees which make up the index.  If  
NIFGetCollectionData is called for a categorized collection, the data that is 
returned pertains only to the top-level category entries, and not to the main 
notes in the collection.

**Parameters :**
Input :
hCollection  -  Handle to the collection.

Output :
(routine)  -  NOERROR - Successfully retrieved collection data
ERR_xxx - Errors returned by lower level functions: (memory management, file operations, network errors, etc.).  There are so many possible causes, that it is best to use the code in a call to OSLoadString and display/log the error for the user as your default error handling.


rethCollData  -  Handle to memory containing the COLLECTIONDATA structure.


**See Also :**
[COLLECTIONDATA](/reference/Data/COLLECTIONDATA)
[NIFOpenCollection](/reference/Func/NIFOpenCollection)
---
