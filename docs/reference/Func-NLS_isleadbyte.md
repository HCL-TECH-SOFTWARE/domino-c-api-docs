##### Function : Character Manipulation
##### NLS_isleadbyte - Tests if a byte is the leading byte in a multibyte character.
---
##### #include <nls.h>
NLS_STATUS LNPUBLIC **NLS_isleadbyte(**

	BYTE  Character,
	NLS_PINFO  pInfo);
**Description :**
This function tests if a byte is the leading byte in a multibyte character.
**Parameters :**
Input :
Character  -  The character to be tested.

pInfo  -  A pointer to an NLS_INFO struct, which contains all of the tables and attributes of the current character set. The NLS_INFO struct should have been initialized by a previous call to OSGetLMBCSCLS().

Output :
(routine)  -  NLS_SUCCESS - The specified character is the lead byte in a multibyte character.
NLS_PROPNOTFOUND - The specified character is NOT the lead byte in a multibyte character or Info->LeadByteTable is NULL.
NLS_INVALIDTABLE - pInfo->PropertyTable is NULL. or pInfo->LeadByteTable is NULL.


**See Also :**
[NLS_INFO](D:/md_files/NLS_INFO.md)
[NLS_isalnum](D:/md_files/NLS_isalnum.md)
[NLS_isalpha](D:/md_files/NLS_isalpha.md)
[NLS_isarith](D:/md_files/NLS_isarith.md)
[NLS_iscntrl](D:/md_files/NLS_iscntrl.md)
[NLS_isdigit](D:/md_files/NLS_isdigit.md)
[NLS_islower](D:/md_files/NLS_islower.md)
[NLS_ispunct](D:/md_files/NLS_ispunct.md)
[NLS_isspace](D:/md_files/NLS_isspace.md)
[NLS_isupper](D:/md_files/NLS_isupper.md)
[NLS_PINFO](D:/md_files/NLS_PINFO.md)
[OSGetLMBCSCLS](D:/md_files/OSGetLMBCSCLS.md)
---
