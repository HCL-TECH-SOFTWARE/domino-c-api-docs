##### Function : Character Manipulation
##### NLS_goto_next_break - Advance a pointer to the byte following the next word break in a string.
---
##### #include <nls.h>
WORD LNPUBLIC **NLS_goto_next_break(**

	BYTE far * far *ppString,
	WORD  Len,
	NLS_PINFO  pInfo);
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
[NLS_goto_next](D:/md_files/NLS_goto_next.md)
[NLS_goto_next_break](D:/md_files/NLS_goto_next_break.md)
[NLS_goto_next_word_end](D:/md_files/NLS_goto_next_word_end.md)
[NLS_goto_next_word_start](D:/md_files/NLS_goto_next_word_start.md)
[NLS_INFO](D:/md_files/NLS_INFO.md)
[NLS_PINFO](D:/md_files/NLS_PINFO.md)
[OSGetLMBCSCLS](D:/md_files/OSGetLMBCSCLS.md)
---
