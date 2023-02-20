##### Function : Character Manipulation
##### NLS_string_bytes - Returns the number of bytes in a string.
---
```
#include <nls.h>
NLS_STATUS LNPUBLIC NLS_string_bytes(

	const BYTE far *pString,
	WORD  NumChars,
	WORD far *pNumBytes,
	NLS_PINFO  pInfo);
```
**Description :**

Returns the number of bytes in a string. If a multibyte character set is in 
use, the number of bytes in a string will likely be larger than the number of 
characters in a string.

**Parameters :**
Input :
pString  -  A pointer to a string in which the bytes are to be counted.

NumChars  -  The number of characters in a string. If the string is null-terminated, specifying NLS_NULLTERM for this argument will make the function work more efficiently. Note: if you pass in NLS_NULLTERM for this argument, the function returns a byte count that includes the NULL terminator.     

pNumBytes  -  A pointer to a WORD to receive the byte count.

pInfo  -  A pointer to an NLS_INFO struct, which contains all of the tables and attributes of the current character set. The NLS_INFO struct should have been initialized by a previous call to OSGetLMBCSCLS().

Output :
(routine)  -  NLS_SUCCESS - the operation completed successfully.


pNumBytes  -  A pointer to a WORD containing the number of bytes in the string.


**See Also :**
[NLS_INFO](/reference/Data/NLS_INFO)
[NLS_PINFO](/reference/Data/NLS_PINFO)
[NLS_string_chars](/reference/Func/NLS_string_chars)
[OSGetLMBCSCLS](/reference/Func/OSGetLMBCSCLS)
---
