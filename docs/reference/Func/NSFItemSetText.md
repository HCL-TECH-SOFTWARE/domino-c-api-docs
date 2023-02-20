##### Function : Item (Field)
##### NSFItemSetText - Append an item of TYPE_TEXT to a note.
---
```
#include <nsfnote.h>
STATUS LNPUBLIC NSFItemSetText(

	NOTEHANDLE  hNote,
	const char far *ItemName,
	const char far *ItemText,
	WORD  TextLength);
```
**Description :**

This function takes a handle to an open note, the name of the item to append, 
and the text to store in the item.  It appends a TYPE_TEXT item to the open 
note. If an item of that name already exists, it deletes the existing item 
first, then appends the new item. 

Note 1:  Use a null character ('\0') to force Notes to display a line break in 
a text field.  Insert null characters in the text where you need line breaks, 
and specify, in argument #4, the length of the string including all null 
characters. Do not use MAXWORD for this argument unless ItemText contains a 
null-terminated string. Do not place carriage return or line feed characters in 
the text buffer.  

Note 2: NSFItemSetText sets the ITEM_SUMMARY flag in the item. Items with the 
ITEM_SUMMARY flag set are stored in the note's summary buffer. These items may 
be used in view columns,  selection formulas, and @functions. The maximum size 
of the summary buffer is 32K per note. If you append more than 32K bytes of 
data in items that have the ITEM_SUMMARY flag set, NSFItemSetText will succeed, 
but NSFNoteUpdate will return ERR_SUMMARY_TOO_BIG. To avoid this, decide which 
fields are not used in view columns, selection formulas, or @ functions. For 
these "non-computed" fields, use NSFItemSetTextSummary with the Summary 
parameter set to FALSE.  Alternatively the lower level API function, 
NSFItemAppend, can also be used to append these items to the document without 
setting the ITEM_SUMMARY flag in the item_flags argument.  

API program may read, modify, and write items that do not have the summary flag 
set, but they must open the note first. Items that do not have the summary flag 
set can not be accessed in the summary buffer.

NSFItemSetText is similar to NSFItemSetTextSummary.  However, NSFItemSetText 
automatically sets the ITEM_SUMMARY flag in the item.  With 
NSFItemSetTextSummary, you specify whether to set this flag.

**Parameters :**
Input :
hNote  -  A handle to an open note.

ItemName  -  A pointer to a null-terminated Item name.

ItemText  -  A pointer a buffer containing the text you wish to store with the item.

TextLength  -  A WORD containing the length of the ItemText.  If MAXWORD is given, then the ItemText buffer must be null-terminated and NSFItemSetText will determine its length.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - Successfully added Text Item to note.

ERR_xxx - Errors returned by lower level functions: (memory management, file operations, etc.).  There are so many possible causes, that it is best to use the code in a call to OSLoadString and display/log the error for the user as your default error handling.



**Sample Usage :**
```


   /* Save Form name in the Note */

   if (error_status = NSFItemSetText(note1_handle, FIELD_FORM,
                          form_name, MAXWORD))
       goto Exit;

```
**See Also :**
[NSFItemSetTextSummary](/reference/Func/NSFItemSetTextSummary)
[NSFItemGetText](/reference/Func/NSFItemGetText)
[NSFItemTextEqual](/reference/Func/NSFItemTextEqual)
[NSFNoteClose](/reference/Func/NSFNoteClose)
[NSFNoteOpen](/reference/Func/NSFNoteOpen)
---
