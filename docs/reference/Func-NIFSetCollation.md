##### Function : Views
##### NIFSetCollation - Select current collation for a collection.
---
##### #include <nif.h>
STATUS LNPUBLIC **NIFSetCollation(**

	HCOLLECTION  hCollection,
	WORD  CollationNum);
**Description :**
Beginning with Release 4, more than one collation may be defined for a view or 
folder.  A collation is a set of columns and sort specifications that 
determines how the view or folder will be sorted.  This function selects which 
collation is used when accessing the collection through the API.  The 
CollationNum parameter must be 0 or greater, and less than the number of 
collations supported by the view or folder.  The CollationNum parameter 
corresponds to one of the $Collation items in the view or folder note.  For 
example, $Collation corresponds to CollationNum=0, $Collation8 corresponds to 
CollationNum=8.

When a collection is first opened, its current collation is set to 0.

The NIFSetCollation() setting is retained as long as the collection is open 
until another call is made to NIFSetCollation().
**Parameters :**
Input :
hCollection  -  Handle to the open collection.

CollationNum  -  Collation to be used for the collection.  Must be in the range 0 <= CollationNum < Number of collations.

Output :
(routine)  -  Return status from this call -- indicates either sucess or what the error is. The return codes include:

NOERROR - Collation selected.

ERR_BAD_COLLATION_NUM - Collation number is less than 0 or greater than the number of collations supported by the view.

ERR_xxx - Errors returned by lower level functions.  There are so many possible causes, that it is best to use the code in a call to OSLoadString and display/log the error for the user. 


**See Also :**
[NIFGetCollation](D:/md_files/NIFGetCollation.md)
[NIFOpenCollection](D:/md_files/NIFOpenCollection.md)
---
