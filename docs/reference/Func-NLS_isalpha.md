##### Function : Character Manipulation
##### NLS_isalpha - Tests if a character is an uppercase or lowercase alphabetic character.
---
##### #include <nls.h>
NLS_STATUS LNPUBLIC **NLS_isalpha(**

	const BYTE far *pCharacter,
	NLS_PINFO  pInfo);
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
[NLS_INFO](D:/md_files/NLS_INFO.md)
[NLS_isalnum](D:/md_files/NLS_isalnum.md)
[NLS_isarith](D:/md_files/NLS_isarith.md)
[NLS_iscntrl](D:/md_files/NLS_iscntrl.md)
[NLS_isdigit](D:/md_files/NLS_isdigit.md)
[NLS_isleadbyte](D:/md_files/NLS_isleadbyte.md)
[NLS_islower](D:/md_files/NLS_islower.md)
[NLS_ispunct](D:/md_files/NLS_ispunct.md)
[NLS_isspace](D:/md_files/NLS_isspace.md)
[NLS_isupper](D:/md_files/NLS_isupper.md)
[NLS_PINFO](D:/md_files/NLS_PINFO.md)
[OSGetLMBCSCLS](D:/md_files/OSGetLMBCSCLS.md)
---
