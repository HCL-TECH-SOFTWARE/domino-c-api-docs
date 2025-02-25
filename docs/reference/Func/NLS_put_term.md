##### Function : Character Manipulation
##### NLS_put_term - Copy a character from one buffer to another, then NULL-terminate the output buffer.
---
```
#include <nls.h>
NLS_STATUS LNPUBLIC NLS_put_term(

	BYTE far * far *ppString,
	const BYTE far *pCharacter,
	NLS_PINFO  pInfo);
```
**Description :**

Copy a character from one buffer to another, and append a NULL character to the 
output buffer after the copied character. After the function completes, the 
pointer to the input/output string will be incremented to point to the NULL 
character.

**Parameters :**
Input :
ppString  -   A pointer to a pointer to the location at which to write the character referenced by the pCharacter argument.

pCharacter  -  A pointer to the character that is to be copied to the location referenced by the ppString argument.

pInfo  -  A pointer to an NLS_INFO struct, which contains all of the tables and attributes of the current character set. The NLS_INFO struct should have been initialized by a previous call to OSGetLMBCSCLS().

Output :
(routine)  -  NLS_SUCCESS - the operation completed successfully.


ppString  -  A pointer to a pointer to the character following the one that was written.


**See Also :**
[NLS_INFO](/domino-c-api-docs/reference/Data/NLS_INFO)
[NLS_PINFO](/domino-c-api-docs/reference/Data/NLS_PINFO)
[NLS_put](/domino-c-api-docs/reference/Func/NLS_put)
[OSGetLMBCSCLS](/domino-c-api-docs/reference/Func/OSGetLMBCSCLS)
---
