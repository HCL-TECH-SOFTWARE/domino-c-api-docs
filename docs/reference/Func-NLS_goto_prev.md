##### Function : Character Manipulation
##### NLS_goto_prev - Moves a pointer back one character in a string.
---
##### #include <nls.h>
WORD LNPUBLIC **NLS_goto_prev(**

	BYTE far * far *ppString,
	const BYTE far *pStrStart,
	NLS_PINFO  pInfo);
**Description :**
Moves a pointer back one character, given pointers to the start of a string and 
a character in the string.
**Parameters :**
Input :
ppString  -  A pointer to a pointer to a character in a string.

pStrStart  -  A pointer to the start of the string.

pInfo  -  A pointer to an NLS_INFO struct, which contains all of the tables and attributes of the current character set. The NLS_INFO struct should have been initialized by a previous call to OSGetLMBCSCLS().

Output :
(routine)  -  The length (in bytes) of the character that we just backed up over. If any of the input pointers are invalid, this function will return 0.


ppString  -  A pointer to a pointer to the previous character in the string.

**See Also :**
[NLS_INFO](D:/md_files/NLS_INFO.md)
[NLS_PINFO](D:/md_files/NLS_PINFO.md)
[OSGetLMBCSCLS](D:/md_files/OSGetLMBCSCLS.md)
---
