##### Function : Item (Field)
##### NSFItemTextEqual - Test if item text is equal to a given text string.
---
```
#include <nsfnote.h>
BOOL LNPUBLIC NSFItemTextEqual(

	NOTEHANDLE  note_handle,
	const char far *item_name,
	const char far *item_text,
	WORD  text_len,
	BOOL  case_sensitive_flag);
```
**Description :**

This function takes a handle to an open note, the name for the TYPE_TEXT Item 
whose value you wish to test,  the test text, the length of that text, and a 
boolean value indicating whether or not to ignore case during the comparison..  
It returns TRUE if the text is equal or FALSE if it is not.

**Parameters :**
Input :
note_handle  -  A handle to an open note in memory.

item_name  -  The address of a null-terminated string containing the Item name.

item_text  -  The address of the text buffer containing the test text.

text_len  -  A WORD containing the length of the test text buffer.  If the length MAXWORD is used, then the string is assumed to be null-terminated, and the length of the null-terminated string is used instead.

case_sensitive_flag  -  A BOOL containing:  TRUE to consider case or FALSE to ignore case during the comparison.

Output :
(routine)  -  Returns: TRUE if text strings are equal.  FALSE if they are NOT equal.



**Sample Usage :**
```
/* Compare text to text item ignoring case! */

printf("Does %s: %s\nEqual %s: %s if case is ignored ?\n",
           TEXT_ITEM, text_buf1,
           TEXT_ITEM, SOME_TEXT3);
printf("Answer: %s\n", (NSFItemTextEqual(note1_handle, TEXT_ITEM,
                              SOME_TEXT3, strlen(SOME_TEXT3),FALSE))
                              ? "YES YES YES!" : "Nooooooooo!");
```
**See Also :**
[NSFItemLongCompare](/reference/Func/NSFItemLongCompare)
[NSFItemSetText](/reference/Func/NSFItemSetText)
[NSFItemTimeCompare](/reference/Func/NSFItemTimeCompare)
[NSFNoteClose](/reference/Func/NSFNoteClose)
[NSFNoteOpen](/reference/Func/NSFNoteOpen)
---
