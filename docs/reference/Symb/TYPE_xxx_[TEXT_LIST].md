##### Symbolic Value : Item (Field) Information
##### TYPE_xxx [TEXT_LIST] - Item Data Type - Text List
---
```
#include <nsfdata.h>
```

**Symbolic Values :**



**Description :**

Text List fields contain one or more text strings. They are stored in notes as items of TYPE_TEXT_LIST.  An item of TYPE_TEXT_LIST consists of a list header, an array of text string lengths, and a packed series of text strings, as follows:<br>
LIST         list header<br>
USHORT       length of string 0<br>
USHORT       length of string 1<br>
...          <br>
USHORT       length of string N<br>
text         text of string 0<br>
text         text of string 1<br>
...<br>
text         text of string N<br>
Create a Text List field by calling the function NSFItemCreateTextList. Append additional text strings by calling the function NSFItemAppendTextList. Read a single text string in a Text List by calling the function NSFItemGetTextListEntry. Determine the number of strings in the list by calling NSFItemGetTextListEntries.<br>
<br>
The list header is a LIST data structure. The ListEntries member of the header contains the number of strings in the list. After the header comes an array of lengths. There are ListEntries lengths in this array. Each length in the array contains the text length of the corresponding string. After the lengths array comes the packed text for all the strings. There are ListEntries strings. There are no separators between the strings, and the strings may contain embedded NULL characters. <br>
<br>
 In the Notes user interface, create a Text List field by composing a document using a form with a Text field. Enter two or more strings, separated by multi-value separators, into the text field. The multi-value separators for a given field are defined in the design of that field in the form. The default multi-value separator is a comma but others, such as semicolon, may be used. The multi-value separator character is not stored in the text list field.<br>
<br>
The total length of a Text List field must not exceed 15 kilobytes. By default, the SUMMARY flag is set for Text List fields.


**Sample Usage :**
```
NSFItemCreateTextList ( note_handle,
                        "Categories",
                        "Manufacturing",
                         MAXWORD);

NSFItemAppendTextList ( note_handle, 
                       "Categories",
                       "Operations", 
                        MAXWORD, TRUE);
```

**See Also :**
[LIST](/domino-c-api-docs/reference/Data/LIST)
[ListAddEntry](/domino-c-api-docs/reference/Func/ListAddEntry)
[ListAddText](/domino-c-api-docs/reference/Func/ListAddText)
[ListAllocate](/domino-c-api-docs/reference/Func/ListAllocate)
[ListGetNumEntries](/domino-c-api-docs/reference/Func/ListGetNumEntries)
[ListGetSize](/domino-c-api-docs/reference/Func/ListGetSize)
[ListGetText](/domino-c-api-docs/reference/Func/ListGetText)
[ListRemoveEntry](/domino-c-api-docs/reference/Func/ListRemoveEntry)
[NSFItemAppendTextList](/domino-c-api-docs/reference/Func/NSFItemAppendTextList)
[NSFItemCreateTextList](/domino-c-api-docs/reference/Func/NSFItemCreateTextList)
[NSFItemGetTextListEntries](/domino-c-api-docs/reference/Func/NSFItemGetTextListEntries)
[NSFItemGetTextListEntry](/domino-c-api-docs/reference/Func/NSFItemGetTextListEntry)
[TYPE_xxx](/domino-c-api-docs/reference/Symb/TYPE_xxx)
---
