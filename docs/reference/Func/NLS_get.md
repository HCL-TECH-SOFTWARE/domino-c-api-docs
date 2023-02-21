##### Function : Character Manipulation
##### NLS_get - Retrieves a character given a pointer to it, and also advances the pointer
---
```
#include <nls.h>
NLS_STATUS LNPUBLIC NLS_get(

	BYTE far * far *ppString,
	WORD  Len,
	BYTE far *pCharacter,
	NLS_PINFO  pInfo);
```
**Description :**

Given a pointer to a character in a string, this function retrieves the 
character, advancing the pointer to the next character in the string.

**Parameters :**
Input :
ppString  -  A pointer to a pointer to a character in a string.

Len  -  The number of characters in the ppString.

pInfo  -  A pointer to an NLS_INFO struct, which contains all of the tables and attributes of the current character set. The NLS_INFO struct should have been initialized by a previous call to OSGetLMBCSCLS().

Output :
(routine)  -  NLS_SUCCESS
NLS_BADPARM - The string, the character, or the NLS_INFO structure specified in the function call was invalid.
NLS_ENDOFSTRING - the string was empty.


ppString  -  A pointer to a pointer to the next character in the string.

pCharacter  -  The character that was read from the string.


**See Also :**
[NLS_INFO](/domino-c-api-docs/reference/Data/NLS_INFO)
[OSGetLMBCSCLS](/domino-c-api-docs/reference/Func/OSGetLMBCSCLS)
---
