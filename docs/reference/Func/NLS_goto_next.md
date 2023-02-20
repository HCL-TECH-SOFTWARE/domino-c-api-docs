##### Function : Character Manipulation
##### NLS_goto_next - Advances a string pointer past one character unless it's the termination character.
---
```
#include <nls.h>
WORD LNPUBLIC NLS_goto_next(

	BYTE far * far *ppString,
	WORD  Len,
	NLS_PINFO  pInfo);
```
**Description :**

Advances a string pointer past one character unless it's the termination 
character.

**Parameters :**
Input :
ppString  -  A pointer to a pointer to a character in a string.

Len  -  The number of bytes in the string. If the string is null terminated, you may set this to NLS_NULLTERM.

pInfo  -  A pointer to an NLS_INFO struct, which contains all of the tables and attributes of the current character set. The NLS_INFO struct should have been initialized by a previous call to OSGetLMBCSCLS().

Output :
(routine)  -  The size (in bytes) of the character that we advanced past. If either of the input pointers are invalid, or if Len  is 0, this function will return 0.


ppString  -  A pointer to a pointer to the next character in the string.


**See Also :**
[NLS_INFO](/reference/Data/NLS_INFO)
[NLS_PINFO](/reference/Data/NLS_PINFO)
[OSGetLMBCSCLS](/reference/Func/OSGetLMBCSCLS)
---
