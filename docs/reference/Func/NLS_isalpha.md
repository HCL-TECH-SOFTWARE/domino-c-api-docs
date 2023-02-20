##### Function : Character Manipulation
##### NLS_isalpha - Tests if a character is an uppercase or lowercase alphabetic character.
---
```
#include <nls.h>
NLS_STATUS LNPUBLIC NLS_isalpha(

	const BYTE far *pCharacter,
	NLS_PINFO  pInfo);
```
**Description :**

This function tests if a character is an uppercase or lowercase alphabetic 
character.

**Parameters :**
Input :
pCharacter  -  Pointer to the character to be tested.

pInfo  -  A pointer to an NLS_INFO struct, which contains all of the tables and attributes of the current character set. The NLS_INFO struct should have been initialized by a previous call to OSGetLMBCSCLS().

Output :
(routine)  -  NLS_SUCCESS - The specified character is an uppercase or lowercase alphabetic character.
NLS_PROPNOTFOUND - The specified character is NOT an uppercase or lowercase alphabetic character.
NLS_INVALIDTABLE - pInfo->PropertyTable is NULL;



**See Also :**
[NLS_INFO](/reference/Data/NLS_INFO)
[NLS_isalnum](/reference/Func/NLS_isalnum)
[NLS_isarith](/reference/Func/NLS_isarith)
[NLS_iscntrl](/reference/Func/NLS_iscntrl)
[NLS_isdigit](/reference/Func/NLS_isdigit)
[NLS_isleadbyte](/reference/Func/NLS_isleadbyte)
[NLS_islower](/reference/Func/NLS_islower)
[NLS_ispunct](/reference/Func/NLS_ispunct)
[NLS_isspace](/reference/Func/NLS_isspace)
[NLS_isupper](/reference/Func/NLS_isupper)
[NLS_PINFO](/reference/Data/NLS_PINFO)
[OSGetLMBCSCLS](/reference/Func/OSGetLMBCSCLS)
---
