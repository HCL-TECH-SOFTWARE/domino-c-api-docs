##### Function : Character Manipulation
##### NLS_string_chars - Returns the number of characters in a string.
---
```
#include <nls.h>
NLS_STATUS LNPUBLIC NLS_string_chars(

	const BYTE far *pString,
	WORD  NumBytes,
	WORD far *pNumChars,
	NLS_PINFO  pInfo);
```
**Description :**

Returns the number of characters in a string, given the string's length in 
bytes. If a multibyte character set is in use, the number of characters in a 
string will likely be smaller than the number of bytes in the string.

**Parameters :**
Input :
pString  -  A pointer to a string in which the characters are to be counted.

NumBytes  -  The number of bytes in a string. If the string is null-terminated, specifying NLS_NULLTERM for this argument will make this operation more efficient.

pNumChars  -  A pointer to a WORD to receive the character count.

pInfo  -  A pointer to an NLS_INFO struct, which contains all of the tables and attributes of the current character set. The NLS_INFO struct should have been initialized by a previous call to OSGetLMBCSCLS().

Output :
(routine)  -  NLS_SUCCESS - the operation completed successfully.


pNumChars  -  A pointer to a WORD containing the number of characters in the string.


**See Also :**
[NLS_INFO](/reference/Data/NLS_INFO)
[NLS_PINFO](/reference/Data/NLS_PINFO)
[NLS_string_bytes](/reference/Func/NLS_string_bytes)
[OSGetLMBCSCLS](/reference/Func/OSGetLMBCSCLS)
---
