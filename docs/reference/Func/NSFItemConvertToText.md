##### Function : Item (Field)
##### NSFItemConvertToText - Given an item name, convert its value to text.
---
```
#include <nsfnote.h>
WORD LNPUBLIC NSFItemConvertToText(

	NOTEHANDLE  note_handle,
	const char far *item_name_ptr,
	char far *text_buf_ptr,
	WORD  text_buf_len,
	char  separator);
```
**Description :**

This is a very powerful function that converts many kinds of Domino fields 
(items) into text strings. The function takes a handle to an open note, the 
name of an item,  the address of the text buffer that will receive the text, 
the length of that buffer, and the character that will be used to separate 
multiple values in a field.

If there is more than one item with the same name, this function will always 
return the first of these. This function, therefore, is not useful if you want 
to retrieve multiple instances of the same field name. For these situations, 
use NSFItemConvertValueToText.

The item value may be any one of these supported Domino data types: 

TYPE_TEXT - Text is returned unmodified.

TYPE_TEXT_LIST - A text list items will merged into a single text string, with 
the separator between them.

TYPE_NUMBER - the FLOAT number will be converted to text.

TYPE_NUMBER_RANGE -- the FLOAT numbers will be converted to text, with the 
separator between them.

TYPE_TIME - the binary Time/Date will be converted to text.

TYPE_TIME_RANGE -- the binary Time/Date values will be converted to text, with 
the separator between them.

TYPE_COMPOSITE - The text portion of the rich text field will be returned.

TYPE_USERID - The user name portion will be converted to text.

TYPE_ERROR - the binary Error value will be converted to "ERROR: ".

TYPE_UNAVAILABLE - the binary Unavailable value will be converted to 
"UNAVAILABLE: ".


**Parameters :**
Input :
note_handle  -  A NOTEHANDLE to the open note containing item you wish to convert.

item_name_ptr  -  The address of a null-terminated LMBCS string containing the name of the item you wish to convert.

text_buf_len  -  A WORD containing the length of the text buffer. The maximum buffer size allowed is 60K. 

separator  -  A char value used to separate multiple values in the converted text.  When converting a data type such as TYPE_TEXT_LIST, any character of your choosing may be used.  If 0 is specified, then the default character value ';' (semicolon) will be used.

Output :
(routine)  -  Returns length of the converted text or zero if item was not found.


text_buf_ptr  -  The address of a text buffer in which the converted text and the terminating '\0' (NULL) character are returned. The maximum buffer size allowed is 60K.


**Sample Usage :**
```

   /* Convert TIMEDATE in Note1 to text and add it to Note2 */

    NSFItemConvertToText(note1_handle, TIME_ITEM, text_buf2,
                         sizeof(text_buf2), ';');

   /* Save coverted time in Note2 as TEXT */

   if (error_status = NSFItemSetText(note2_handle,
                          CONV_TIME_ITEM, text_buf2,
                          (WORD) strlen(text_buf2)))
       goto Exit;

```
**See Also :**
[ConvertItemToText](/reference/Func/ConvertItemToText)
[ConvertTIMEDATEPAIRToText](/reference/Func/ConvertTIMEDATEPAIRToText)
[ConvertTIMEDATEToText](/reference/Func/ConvertTIMEDATEToText)
[NSFItemConvertToText](/reference/Func/NSFItemConvertToText)
[NSFItemInfo](/reference/Func/NSFItemInfo)
[NSFItemInfoNext](/reference/Func/NSFItemInfoNext)
[NSFNoteClose](/reference/Func/NSFNoteClose)
[NSFNoteOpen](/reference/Func/NSFNoteOpen)
---
