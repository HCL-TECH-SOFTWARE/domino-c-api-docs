##### Function : Character Manipulation
##### NLS_translate - Character encoding translation routine.
---
```
#include <nls.h>
NLS_STATUS LNPUBLIC NLS_translate(

	BYTE far *pString,
	WORD  Len,
	BYTE far *pStringTarget,
	WORD far *pSize,
	WORD  ControlFlags,
	NLS_PINFO  pInfo);
```
**Description :**

NLS_translate translates the SOURCE input string and puts the resulting 
translation into the TARGET output string.  ControlFlags control how the 
translation is performed (e.g. LMBCS to UNICODE).  See the symbolic value 
NLS_xxx (TRANSLATE) for a complete list of control flags.

The Len argument is either the actual byte-count length of the SOURCE input 
string or, NLS_NULLTERM.  NLS_NULLTERM means that the input string IS NULL 
terminated and thus, the string's length can be calculated via some flavor of 
strlen().  Otherwise the Len value is used as the SOURCE input string's actual 
length.

**Parameters :**
Input :
pString  -  The SOURCE input string.

Len  -  Length in bytes of input string. If the string is null terminated, you may set this to NLS_NULLTERM.

pSize  -  Size in bytes of output buffer.

ControlFlags  -  Flags to govern how translation is performed.

pInfo  -  Pointer to a populated NLS_INFO structure.

Output :
(routine)  -  NLS_SUCCESS
NLS_BADPARM


pStringTarget  -  Pointer to the TARGET output buffer containing resultant data.

pSize  -  The actual number of bytes written to the output buffer.


**See Also :**
[NLS_load_charset](/domino-c-api-docs/reference/Func/NLS_load_charset)
[NLS_xxx (TRANSLATE)](/domino-c-api-docs/reference/Symb/NLS_xxx (TRANSLATE))
---
