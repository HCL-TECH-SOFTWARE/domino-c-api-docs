##### Function : Character Manipulation
##### NLS_goto_prev_word_end - Moves a pointer to the first character following the end of the previous word.
---
```
#include <nls.h>
WORD LNPUBLIC NLS_goto_prev_word_end(

	BYTE far * far *ppString,
	const BYTE far *pStrStart,
	NLS_PINFO  pInfo);
```
**Description :**

Given pointers to a string and a character in it, move the pointer to point to 
the first character after the end of the previous word.

Note: Kanji, Katakana and Hiragana characters are treated like words.

**Parameters :**
Input :
ppString  -  A pointer to a pointer to a byte within a string.

pStrStart  -  A pointer to the beginning of the string.

pInfo  -  A pointer to an NLS_INFO struct, which contains all of the tables and attributes of the current character set. The NLS_INFO struct should have been initialized by a previous call to OSGetLMBCSCLS().

Output :
(routine)  -  The  number of bytes that were skipped to get to the end of the previous word. This routine will return 0 (zero) when one of the following occurs:
     - ppString, pStrStart, or pInfo are invalid pointers;
     - pInfo->PropertyTable is NULL;
     - the string pointed to by ppString is empty;
     - there is no previous word.


ppString  -  A pointer to a pointer to the first byte after the end of the previous word.


**See Also :**
[NLS_goto_next_word_end](/reference/Func/NLS_goto_next_word_end)
[NLS_INFO](/reference/Data/NLS_INFO)
[NLS_PINFO](/reference/Data/NLS_PINFO)
[OSGetLMBCSCLS](/reference/Func/OSGetLMBCSCLS)
---
