##### Symbolic Value : Item (Field) Information
##### TYPE_xxx [TEXT_LIST] - Item Data Type - Text List
---
##### #include <nsfdata.h>
**Description :**
Text List fields contain one or more text strings. They are stored in notes as 
items of TYPE_TEXT_LIST.  An item of TYPE_TEXT_LIST consists of a list header, 
an array of text string lengths, and a packed series of text strings, as 
follows:
LIST         list header
USHORT       length of string 0
USHORT       length of string 1
...          
USHORT       length of string N
text         text of string 0
text         text of string 1
...
text         text of string N
Create a Text List field by calling the function NSFItemCreateTextList. Append 
additional text strings by calling the function NSFItemAppendTextList. Read a 
single text string in a Text List by calling the function 
NSFItemGetTextListEntry. Determine the number of strings in the list by calling 
NSFItemGetTextListEntries.

The list header is a LIST data structure. The ListEntries member of the header 
contains the number of strings in the list. After the header comes an array of 
lengths. There are ListEntries lengths in this array. Each length in the array 
contains the text length of the corresponding string. After the lengths array 
comes the packed text for all the strings. There are ListEntries strings. There 
are no separators between the strings, and the strings may contain embedded 
NULL characters. 

 In the Notes user interface, create a Text List field by composing a document 
using a form with a Text field. Enter two or more strings, separated by 
multi-value separators, into the text field. The multi-value separators for a 
given field are defined in the design of that field in the form. The default 
multi-value separator is a comma but others, such as semicolon, may be used. 
The multi-value separator character is not stored in the text list field.

The total length of a Text List field must not exceed 15 kilobytes. By default, 
the SUMMARY flag is set for Text List fields.
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
[LIST](D:/md_files/LIST.md)
[ListAddEntry](D:/md_files/ListAddEntry.md)
[ListAddText](D:/md_files/ListAddText.md)
[ListAllocate](D:/md_files/ListAllocate.md)
[ListGetNumEntries](D:/md_files/ListGetNumEntries.md)
[ListGetSize](D:/md_files/ListGetSize.md)
[ListGetText](D:/md_files/ListGetText.md)
[ListRemoveEntry](D:/md_files/ListRemoveEntry.md)
[NSFItemAppendTextList](D:/md_files/NSFItemAppendTextList.md)
[NSFItemCreateTextList](D:/md_files/NSFItemCreateTextList.md)
[NSFItemGetTextListEntries](D:/md_files/NSFItemGetTextListEntries.md)
[NSFItemGetTextListEntry](D:/md_files/NSFItemGetTextListEntry.md)
[TYPE_xxx](D:/md_files/TYPE_xxx.md)
---
