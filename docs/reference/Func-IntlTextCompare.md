##### Function : International Character Manipulation
##### IntlTextCompare - Compare strings using international collation rules.
---
##### #include <misc.h>
int LNPUBLIC **IntlTextCompare(**

	const void far *Str1,
	WORD  Str1Len,
	const void far *Str2,
	WORD  Str2Len,
	DWORD  Flags);
**Description :**
The two strings are compared using the international collation rules in the 
current system collation table.  Collation options may be specified to for 
comparing characters;  the options that may be specified are described in the 
entry INTL_xxx_SENSITIVE.
**Parameters :**
Input :
Str1  -  Pointer to first string to compare.

Str1Len  -  Length of the first string, in bytes.

Str2  -  Pointer to the second string to compare.

Str2Len  -  Length of the second string, in bytes.

Flags  -  Collation options.  The options that may be specified are described in the entry INTL_xxx_SENSITIVE.

Output :
(routine)  -  0 if the strings are equal
1 if Str1 follows Str2 in sorted order
-1 if Str1 precedes Str2 in sorted order


**See Also :**
[INTL_xxx_SENSITIVE](D:/md_files/INTL_xxx_SENSITIVE.md)
---
