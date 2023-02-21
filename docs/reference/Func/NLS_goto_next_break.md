##### Function : Character Manipulation
##### NLS_goto_next_break - Advance a pointer to the byte following the next word break in a string.
---
```
#include <nls.h>
WORD LNPUBLIC NLS_goto_next_break(

	BYTE far * far *ppString,
	WORD  Len,
	NLS_PINFO  pInfo);
```
**Description :**

Advance a pointer to the byte following the next word break in a string.

Note: Kanji, Katakana and Hiragana characters are treated like words.

**Parameters :**
Input :
ppString  -  A pointer to a pointer to a character in a string.

Len  -  The number of bytes in the string. If the string is null terminated, you may set this to NLS_NULLTERM.

pInfo  -  A pointer to an NLS_INFO struct, which contains all of the tables and attributes of the current character set. The NLS_INFO struct should have been initialized by a previous call to OSGetLMBCSCLS().

Output :
(routine)  -  The number of bytes that were skipped to find the next word break.


ppString  -  A pointer to a pointer to the character following the next word break.


**See Also :**
[NLS_goto_next](/domino-c-api-docs/reference/Func/NLS_goto_next)
[NLS_goto_next_break](/domino-c-api-docs/reference/Func/NLS_goto_next_break)
[NLS_goto_next_word_end](/domino-c-api-docs/reference/Func/NLS_goto_next_word_end)
[NLS_goto_next_word_start](/domino-c-api-docs/reference/Func/NLS_goto_next_word_start)
[NLS_INFO](/domino-c-api-docs/reference/Data/NLS_INFO)
[NLS_PINFO](/domino-c-api-docs/reference/Data/NLS_PINFO)
[OSGetLMBCSCLS](/domino-c-api-docs/reference/Func/OSGetLMBCSCLS)
---
