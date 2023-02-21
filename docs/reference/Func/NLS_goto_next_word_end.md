##### Function : Character Manipulation
##### NLS_goto_next_word_end - Advances a pointer to the first character following the current word in a string.
---
```
#include <nls.h>
WORD LNPUBLIC NLS_goto_next_word_end(

	BYTE far * far *ppString,
	WORD  Len,
	NLS_PINFO  pInfo);
```
**Description :**

Advances a pointer to the first character following the current word in a 
string, skipping over the rest of the current word (if any).

Note: Kanji, Katakana and Hiragana characters are treated like words.

**Parameters :**
Input :
ppString  -  A pointer to a pointer to a byte within a string.

Len  -  The length in bytes of the string. If the string is null terminated, you may set this to NLS_NULLTERM.

pInfo  -  A pointer to an NLS_INFO struct, which contains all of the tables and attributes of the current character set. The NLS_INFO struct should have been initialized by a previous call to OSGetLMBCSCLS().

Output :
(routine)  -  The  number of bytes that were skipped to get to the end of the next word. This routine will return 0 (zero) when one of the following occurs:
     - ppString or pInfo are invalid pointers;
     - pInfo->PropertyTable is NULL;
     - the string pointed to by ppString is empty.


ppString  -  A  pointer to a pointer to the first character following the current word in a string.


**See Also :**
[NLS_goto_next](/domino-c-api-docs/reference/Func/NLS_goto_next)
[NLS_INFO](/domino-c-api-docs/reference/Data/NLS_INFO)
[NLS_PINFO](/domino-c-api-docs/reference/Data/NLS_PINFO)
[OSGetLMBCSCLS](/domino-c-api-docs/reference/Func/OSGetLMBCSCLS)
---
