##### Function : Character Manipulation
##### NLS_goto_next_word_start - Advances a pointer to the start of the next word in a string.
---
##### #include <nls.h>
WORD LNPUBLIC **NLS_goto_next_word_start(**

	BYTE far * far *ppString,
	WORD  Len,
	NLS_PINFO  pInfo);
**Description :**
Advances a pointer to the start of the next word in a string, skipping over the 
rest of the current word (if any) as well as any whitespace that precedes the 
next word.

Note: Kanji, Katakana and Hiragana characters are treated like words.
**Parameters :**
Input :
ppString  -  A pointer to a pointer to a byte within a string.


Len  -  The length in bytes of the string. If the string is null terminated, you may set this to NLS_NULLTERM.

pInfo  -  A pointer to an NLS_INFO struct, which contains all of the tables and attributes of the current character set. The NLS_INFO struct should have been initialized by a previous call to OSGetLMBCSCLS().


Output :
(routine)  -  The  number of bytes that were skipped to get to the start of the next word. This routine will return 0 (zero) when one of the following occurs:
     - ppString or pInfo are invalid pointers;
     - pInfo->PropertyTable is NULL;
     - the string pointed to by ppString is empty.


ppString  -  A  pointer to a pointer to the first character in the next word.

**See Also :**
[NLS_goto_next_word_end](D:/md_files/NLS_goto_next_word_end.md)
[NLS_INFO](D:/md_files/NLS_INFO.md)
[NLS_PINFO](D:/md_files/NLS_PINFO.md)
[OSGetLMBCSCLS](D:/md_files/OSGetLMBCSCLS.md)
---
