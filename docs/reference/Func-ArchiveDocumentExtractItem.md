##### Function : archiving service
##### ArchiveDocumentExtractItem - Removes an item from an ArchiveDocument and returns the value to the caller.
---
##### #include <archsvc.h>
STATUS LNPUBLIC **ArchiveDocumentExtractItem(**

	HARCHIVEDOCUMENT  hArchDoc,
	const char *ItemName,
	WORD  NameLen,
	ITEMEXTRACTCALLBACK  ItemExtractCallback,
	void *pUserCtx);
**Description :**
Item(s) must be returned to the archive document using 
ArchiveDocumentInsertItem before the document can be restored to a database. 
See ArchiveDocumentRestore for more details on restoring a document to a 
database.
**Parameters :**
Input :
hArchDoc  -  Handle to ArchiveDocument.

ItemName  -  Name of the item to extract. Corresponds to item name in originating notes document. If there are multiple items with the same name all will be concatenated together and passed to the caller. 

NameLen  -  Length of ItemName.

ItemExtractCallback  -  Callback function that receives data. Note that data format passed to this function is opaque.

pUserCtx  -  Caller-defined context structure.

Output :
(routine)  -  ERR_ITEM_NOT_FOUND if there is no item with matching name. NOERROR if successful, error status	from lower level functions otherwise.


**See Also :**
[ITEMEXTRACTCALLBACK](D:/md_files/ITEMEXTRACTCALLBACK.md)
---
