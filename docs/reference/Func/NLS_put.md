##### Function : Character Manipulation
##### NLS_put - Copy a character from one buffer to another.
---
```
#include <nls.h>
NLS_STATUS LNPUBLIC NLS_put(

	BYTE far * far *ppString,
	const BYTE far *pCharacter,
	NLS_PINFO  pInfo);
```
**Description :**

Copy a character from one buffer to another. After the function completes, the 
pointer to the input\output string will be incremented to point to the next 
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
[NLS_put_term](/domino-c-api-docs/reference/Func/NLS_put_term)
[OSGetLMBCSCLS](/domino-c-api-docs/reference/Func/OSGetLMBCSCLS)
---
