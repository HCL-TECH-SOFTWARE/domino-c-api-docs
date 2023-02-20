##### Function : Character Manipulation
##### NLS_find - Finds the first instance of a character in a string, given a set of search characters.
---
```
#include <nls.h>
NLS_STATUS LNPUBLIC NLS_find(

	BYTE far * far *ppString,
	WORD  Len,
	const BYTE far *pSetOfChars,
	WORD  ControlFlags,
	NLS_PINFO  pInfo);
```
**Description :**

Finds the first instance of a character in a string, given a set of search 
characters. Depending on the value of the ControlFlags argument, you can search 
for the first character in the string that IS in the set of search characters, 
or the first character in the string that IS NOT in the set.

**Parameters :**
Input :
ppString  -  A pointer to a pointer to the string in which to search for the characters.

Len  -  The number of bytes in the string to be searched. If the string is null terminated, you may set this to NLS_NULLTERM.

pSetOfChars  -  A pointer to an array of characters for which to search.

ControlFlags  -  Search criteria flags. See the symbolic definitions for NLS_FIND_xxx for more details.

pInfo  -   pointer to an NLS_INFO struct, which contains all of the tables and attributes of the current character set. The NLS_INFO struct should  have been initialized by a previous call to OSGetLMBCSCLS().

Output :
(routine)  -  NLS_SUCCESS - A character meeting the search criteria was found in the string.
NLS_FINDFAILED - No character meeting the search criteria was found in the string.


ppString  -  A pointer to a pointer to the character that met the search criteria.


**See Also :**
[NLS_find_substr](/reference/Func/NLS_find_substr)
[NLS_FIND_xxx](/reference/Symb/NLS_FIND_xxx)
[NLS_INFO](/reference/Data/NLS_INFO)
[NLS_PINFO](/reference/Data/NLS_PINFO)
[OSGetLMBCSCLS](/reference/Func/OSGetLMBCSCLS)
---
