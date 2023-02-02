##### Function : Character Manipulation
##### NLS_load_charset - Loads a given character set.
---
##### #include <nls.h>
NLS_STATUS LNPUBLIC **NLS_load_charset(**

	WORD  CSID,
	NLS_PINFO FAR *ppInfo);
**Description :**
This function will load a character set and return  a pointer to a pointer to 
an NLS_INFO structure.  The calling application is responsible for unloading 
the character set using NLS_unload_charset.
**Parameters :**
Input :
CSID  -  A character set ID.  For information regarding valid character set IDs, please see symbolic value NLS_CS_xxx. 

Output :
(routine)  -  NLS_SUCCESS
NLS_INVALIDTABLE - A table contained in the NLS_INFO structure of the specified character set is invalid.


ppInfo  -  A pointer to a pointer to a populated NLS_INFO structure.

**See Also :**
[NLS_CS_xxx](D:/md_files/NLS_CS_xxx.md)
[NLS_PINFO](D:/md_files/NLS_PINFO.md)
[NLS_translate](D:/md_files/NLS_translate.md)
[NLS_unload_charset](D:/md_files/NLS_unload_charset.md)
---
