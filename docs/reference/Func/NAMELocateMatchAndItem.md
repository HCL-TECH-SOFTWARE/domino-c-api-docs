##### Function : Address Book
##### NAMELocateMatchAndItem - Locate an item in a look up buffer by buffer-wide match number
---
```
#include <lookup.h>
STATUS LNPUBLIC NAMELocateMatchAndItem(

	void far *pLookup,
	WORD  MatchNum,
	WORD  Item,
	WORD far *retDataType,
	void far *retpMatch,
	void far *retpItem,
	WORD far *retSiz);
```
**Description :**

Note:  Address books refer to both Notes Client Address books, and Domino 
Server Address books know as Domino Directories.
   
       This routine gets information about an item in a look up buffer. Use 
this routine to obtain information about an item when it is more convenient to 
specify the match number than the location of the match, where the match 
numbers start with the first record in the buffer and continue across all 
records in the buffer.

NAMELookup creates a look up buffer containing information from the Address 
books about a series of names. The look up buffer consists of a series of 
records, one record per name. A record may contain multiple matches. A match 
may contain multiple item values. 

Use NAMELocateMatchAndItem to get information from the buffer on a match - by - 
match basis rather than on a record - and - match basis.

Like NAMELocateItem, this routine gets the location of the item value, the data 
type word, and value length. Unlike NAMELocateItem, this routine requires, as 
input, a match number. It returns, as output, the location of the match.

This routine allows the caller to specify the match by number, where the first 
match in the first record is number 0, and subsequent matches are numbered 
sequentially across the buffer. In other words, this routine hides the fact 
that the matches are being returned from different records.

For example, suppose you call NAMELookup to get the value of the item "Domain" 
for the 3 names "Hyder," "Nielsen," and "Socinus".  NAMELookup creates a lookup 
buffer with 3 records.  Suppose the Address books contained 2 person documents 
for "Nielsen". Then the second record in the buffer would contain 2 matches 
corresponding to the 2 Nielsens. Altogether, then, the buffer would contain 4 
matches.  Each match contains (possibly different) values for the item 
"Domain". Use NAMELocateMatchAndItem if you need information about, for 
example, the third match for the item "Domain" and you are not concerned with 
what record contains the third match.

NOTE: a loop calling this routine is not as efficient as a double loop using 
NAMELocateNextName and  NAMELocateNextMatch. The latter approach traverses the 
NAMELookup buffer once.  Calling this routine in a loop re-parses the 
NAMELookup buffer many times.  This is inefficient if the buffer contains many 
matches.

After locating the match and item using this routine, if the item is of 
TYPE_TEXT or TYPE_TEXT_LIST, use NAMEGetTextItem to retrieve the item value 
from the buffer.

**Parameters :**
Input :
pLookup  -  pointer to look up buffer. Call NAMELookup to create this buffer. Call OSLockObject to obtain this pointer.

MatchNum  -  Match number from which to retrieve the item information. Match number 0 is the first match in the first record. If the first record contains 3 matches, then the first match in the second record is match number 3.

Item  -  Item number = index of the item name in the set specified by the "Items" argument to NAMELookup. Zero specifies the first item. Note: this item number must not be greater than the number of items specified by the "NumItems" argument to NAMELookup.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - Successfully located item in buffer.

ERR_NO_MORE_MATCH - No more matches.

ERR_xxx - Errors returned by lower level functions. Call OSLoadString to obtain the error string.


retDataType  -  receives the data type word of the requested item (e.g. TYPE_TEXT).

retpMatch  -  receives the locaton of the specified match in the look up buffer

retpItem  -  receives the location of the item value in the look up buffer. Item value begins with the data type word. However, caller can not directly de-reference this pointer to retrieve the data type word as it may be odd aligned. Use retDataType to retrieve the data type word.

retSiz  -  receives the value length, in bytes, of the requested item value. Length includes the data type word.


**See Also :**
[NAMELookup](/domino-c-api-docs/reference/Func/NAMELookup)
[NAMELocateNextName](/domino-c-api-docs/reference/Func/NAMELocateNextName)
[NAMELocateNextMatch](/domino-c-api-docs/reference/Func/NAMELocateNextMatch)
[NAMELocateItem](/domino-c-api-docs/reference/Func/NAMELocateItem)
[OSLockObject](/domino-c-api-docs/reference/Func/OSLockObject)
---
