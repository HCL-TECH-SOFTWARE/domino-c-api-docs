##### Function : Views
##### NIFFindByKey - Finds notes using single or multiple sort keys.
---
```
#include <nif.h>
STATUS LNPUBLIC NIFFindByKey(

	HCOLLECTION  hCollection,
	void far *KeyBuffer,
	WORD  FindFlags,
	COLLECTIONPOSITION far *retIndexPos,
	DWORD far *retNumMatches);
```
**Description :**

This function searches through a collection for the first note whose sort 
column values match the given search keys.  The search key consists of a buffer 
containing one or several values structured as an ITEM_TABLE. This function 
matches each value in the search key against the corresponding sorted column of 
the view or folder. Only sorted columns are used. The values in the search key 
item table must be specified in the same order as the sorted columns in the 
view or folder, from left to right.  Other unsorted columns may lie between the 
sorted columns to be searched.  For example, suppose view columns 1, 3, 4 and 5 
are sorted.  The key buffer may contain search keys for: just column 1; columns 
1 and 3; or for columns 1, 3, and 4.

This function yields the COLLECTIONPOSITION of the first note in the collection 
that matches the keys. It also yields a count of the number of notes that match 
the keys. Since all notes that match the keys appear contiguously in the view 
or folder, you may pass the resulting COLLECTIONPOSITION and match count as 
inputs to NIFReadEntries to read all the entries in the collection that match 
the keys.

If multiple notes match the specified (partial) keys, and FIND_FIRST_EQUAL (the 
default flag) is specified, then the position of the first matching note is 
returned ("first" is defined by the note which collates before all the others 
in the view).  The position of the last matching note is returned if 
FIND_LAST_EQUAL is specified.  If FIND_LESS_THAN is specified, then the last 
note with a key value less than the specified key is returned.  If 
FIND_GREATER_THAN is specified, then the first note with a key value greater 
than the specified key is returned.

This routine cannot be used to locate notes that are categorized under multiple 
categories (the resulting position is unpredictable), and also cannot be used 
to locate responses.

This routine is usually not appropriate for equality searches of key values of 
TYPE_TIME.  A match will only be found if the key value is as precise as and is 
equal to the internally stored data.  TYPE_TIME data is displayed with less 
precision than what is stored internally.  Use inequality searches, such as 
FIND_GREATER_THAN or FIND_LESS_THAN, for TYPE_TIME key values to avoid having 
to find an exact match of the specified value.  If the precise key value is 
known, however, equality searches of TYPE_TIME values are supported.

Returning the number of matches on an inequality search is not supported.  In 
other words, if you specify any one of the following for the FindFlags argument:
	FIND_LESS_THAN
	FIND_LESS_THAN | FIND_EQUAL
	FIND_GREATER_THAN
	FIND_GREATER_THAN | FIND_EQUAL
this function cannot determine the number of notes that match the search 
condition.  In this case you may want to specify NULL for the retNumMatches 
argument.  If you do not specify NULL for the retNumMatches argument, then 
*retNumMatches will be set to 1.

**Parameters :**
Input :
hCollection  -  The handle of the collection you want to search.

KeyBuffer  -  A pointer to a Domino memory object containing an ITEM_TABLE and its accompanying array of ITEMs.  The ITEMs must be specified in the same order as the sorted columns of the view or folder.  The ITEM's  '.NameLength' value may be set to zero and the ITEM's name may be omitted from the information following the ITEM header.  If the ITEM's name and NameLength values are specified, they are ignored by this function.  Each ITEM must match the data type of the information in the corresponding sorted column. 

FindFlags  -  Flags that control the comparison rules used when a key is compared to the notes in the collection. The find flags are described in FIND_xxx, and may be OR'ed together to combine functionailty.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR
ERR_NOT_FOUND


retIndexPos  -  The address of a COLLECTIONPOSITION in which the position within the collection where the match is found is returned. The exact position that is returned depends on the value of the FIND_FLAGS that are specified.  If more than one matching note was found, the position of the first matching note will be returned.  You can use retIndexPos with NIFReadEntries to get the notes found by this search.

retNumMatches  -  The address of a DWORD in which the number of matching notes is returned.  This value is usually passed-on to a subsequent call to NIFReadEntries().  It can also be used simply to determine if the name has multiple matches or not (ambiguity).  

The number of matching entries is not supported if FIND_LESS_THAN, FIND_LESS_THAN | FIND_EQUAL, FIND_GREATER_THAN, or FIND_GREATER_THAN | FIND_EQUAL is specified in the FindFlags argument.  In this case, you may specify NULL for the retNumMatches argument.  If you do not specify NULL, then 1 is returned as the number of matching notes.


**See Also :**
[NIFOpenCollection](/domino-c-api-docs/reference/Func/NIFOpenCollection)
[NIFReadEntries](/domino-c-api-docs/reference/Func/NIFReadEntries)
[ITEM_TABLE](/domino-c-api-docs/reference/Data/ITEM_TABLE)
---
