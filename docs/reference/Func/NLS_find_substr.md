##### Function : Character Manipulation
##### NLS_find_substr - Search a string for a given substring.
---
```
#include <nls.h>
NLS_STATUS LNPUBLIC NLS_find_substr(

	BYTE far * far *ppString,
	WORD  Len1,
	const BYTE far *pSubString,
	WORD  Len2,
	NLS_PINFO  pInfo);
```
**Description :**

This function searches a string for a given substring, returning a pointer to 
the start of the substring within the original string. The search is case 
sensitive and pitch sensitive.

**Parameters :**
Input :
ppString  -  A pointer to a pointer to the string to be searched.

Len1  -  The number of characters in the string to be searched.

pSubString  -  The substring for which to search.

Len2  -  The number of characters in the substring for which to search.

pInfo  -  A pointer to an NLS_INFO struct, which contains all of the tables and attributes of the current character set.  The NLS_INFO struct should have been initialized by a previous call to OSGetLMBCSCLS().

Output :
(routine)  -  NLS_SUCCESS - The substring was found in the string, or the substring was empty.
NLS_BADPARM - The string, the substring, or the NLS_INFO structure specified in the function call was invalid.
NLS_FINDFAILED - The string was empty, or the substring was not found in the string.
NLS_INVALIDTABLE - One of the tables in the specified NLS_INFO structure is invalid.


ppString  -  A pointer to a pointer to the substring within the original string.


**See Also :**
[NLS_find](/reference/Func/NLS_find)
[NLS_INFO](/reference/Data/NLS_INFO)
[OSGetLMBCSCLS](/reference/Func/OSGetLMBCSCLS)
---
