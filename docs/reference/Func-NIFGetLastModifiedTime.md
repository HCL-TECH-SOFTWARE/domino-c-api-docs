##### Function : Views
##### NIFGetLastModifiedTime - Get the collection modification sequence number.
---
##### #include <nif.h>
void LNPUBLIC **NIFGetLastModifiedTime(**

	HCOLLECTION  hCollection,
	TIMEDATE far *retLastModifiedTime);
**Description :**
Each time the number of documents in a collection is modified, a sequence 
number is incremented.  This function will return the modification sequence 
number, which may then be compared to a previous value (also obtained by 
calling NIFGetLastModifiedTime()) to determine whether or not the number of 
documents in the collection has been changed.

Note that the TIMEDATE value returned by this function is not an actual time.
**Parameters :**
Input :
hCollection  -  Handle to the collection.

Output :
retLastModifiedTime  -  Modification sequence number.

**See Also :**
[NIFCloseCollection](D:/md_files/NIFCloseCollection.md)
[NIFOpenCollection](D:/md_files/NIFOpenCollection.md)
[NIFUpdateCollection](D:/md_files/NIFUpdateCollection.md)
---
