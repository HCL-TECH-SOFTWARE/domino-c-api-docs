##### Function : Item (Field)
##### NSFItemConvertValueToText - Given its BLOCKID, convert item value to text.
---
```
#include <nsfnote.h>
WORD LNPUBLIC NSFItemConvertValueToText(

	WORD  value_type,
	BLOCKID  value_bid,
	DWORD  value_len,
	char far *text_buf_ptr,
	WORD  text_buf_len,
	char  separator);
```
**Description :**

This function converts the value of an item to text where the item may be any 
one of a variety of Domino data types. This function takes, as input, the data 
type word, the BLOCKID of an item value, the length of that value (including 
the WORD of Domino data type),  the address of the text buffer that will 
receive the converted text, the length of that buffer,  and the single 
character that will be used to separate multi-value items. This writes a 
zero-terminated character text string to the specified text buffer and returns 
the length of the text.

Use this function to render an item value as printable text when you do not 
have the handle to the open note that contains the item.  If the desired item 
is already associated with a note, use the function NSFItemConvertToText, which 
has a simpler argument list.

The item value may be any one of the following Domino data types: 

TYPE_TEXT - Text will be returned unmodified.
TYPE_TEXT_LIST - A text list will be converted to text.
TYPE_USERID - The user name portion will be converted to text.
TYPE_NUMBER - the FLOAT/NUMBER type number will be converted to text.
TYPE_TIME - the binary time/date will be converted to text.
	TYPE_COMPOSITE - the composite item will be converted to text.
TYPE_ERROR - the binary Error value will be converted to "ERROR: ".
TYPE_UNAVAILABLE - the binary Unavailable value will be converted to 
"UNAVAILABLE: ".

The maximim size of the returned buffer is 60K.

**Parameters :**
Input :
value_type  -  A WORD containing the Domino data type of the item value.

value_bid  -  The BLOCKID of the item value you wish to convert into text.

value_len  -  A DWORD containing the length of the item value, including the WORD of Domino data type.

text_buf_len  -  A WORD containing the length of the text buffer.

separator  -  A char value used to separate multiple values in the converted text.  When converting a data type such as TYPE_TEXT_LIST, any character of your choosing may be used.  If 0 is specified, then the default character value ';' (semicolon) will be used.

Output :
(routine)  -  Returns length of the converted text or zero if item was not found.


text_buf_ptr  -  The address of a text buffer in which the converted text and the terminating '\0' (NULL) character are returned. The maximum size of the buffer is 60K.


**Sample Usage :**
```

   /* Get TEXT_LIST_ITEM from Note1, convert it to text and then */
   /*  add it to Note2  as TYPE_TEXT                             */

   if ( error_status = NSFItemInfo(note1_handle, TEXT_LIST_ITEM,
                           strlen(TEXT_LIST_ITEM), &item_bid,
                           &value_type, &value_bid, &value_len))
       goto Exit;

   NSFItemConvertValueToText(value_type, value_bid, value_len,
                           text_buf1, LINEOTEXT-1, ',');

   /* Save Coverted Text List in Note2 as TEXT */

   if (error_status = NSFItemSetText(note2_handle, CONV_LIST_ITEM,
                          text_buf1, (WORD) strlen(text_buf1)))
       goto Exit;
```
**See Also :**
[ConvertItemToText](/reference/Func/ConvertItemToText)
[ConvertTIMEDATEToText](/reference/Func/ConvertTIMEDATEToText)
[ConvertTIMEDATEPAIRToText](/reference/Func/ConvertTIMEDATEPAIRToText)
[NSFItemConvertToText](/reference/Func/NSFItemConvertToText)
[NSFItemInfo](/reference/Func/NSFItemInfo)
[NSFItemInfoNext](/reference/Func/NSFItemInfoNext)
[NSFNoteClose](/reference/Func/NSFNoteClose)
[NSFNoteOpen](/reference/Func/NSFNoteOpen)
---
