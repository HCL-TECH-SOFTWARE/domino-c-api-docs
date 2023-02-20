##### Function : archiving service
##### ArchiveDocumentGetText - Converts an item in an archive document to text.
---
```
#include <archsvc.h>
STATUS LNPUBLIC ArchiveDocumentGetText(

	HARCHIVEDOCUMENT  hArchDoc,
	const char *ItemName,
	DWORD  NameLen,
	ARCHIVETEXTOUTPUTCALLBACK  ArchiveTextOutputCallback,
	void *pUserCtx);
```
**Description :**

Just for supported types see NSFItemConvertToText. As well, all MIME subtypes 
of type text (i.e text/plain, text/html) are returned when an item contains 
MIME.

**Parameters :**
Input :
hArchDoc  -  Handle to ArchiveDocument.

ItemName  -  Name of the item to convert. Corresponds to item name in originating notes document.

NameLen  -  Length of ItemName.

ArchiveTextOutputCallback  -  Callback function that receives data.

pUserCtx  -  Caller-defined context structure.

Output :
(routine)  -  NOERROR return status means that it is successful.



**See Also :**
[ARCHIVETEXTOUTPUTCALLBACK](/reference/Data/ARCHIVETEXTOUTPUTCALLBACK)
---
