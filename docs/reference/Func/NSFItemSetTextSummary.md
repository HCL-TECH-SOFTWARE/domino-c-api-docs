##### Function : Item (Field)
##### NSFItemSetTextSummary - Append an item of TYPE_TEXT to a note.
---
```
#include <nsfnote.h>
STATUS LNPUBLIC NSFItemSetTextSummary(

	NOTEHANDLE  hNote,
	const char far *ItemName,
	const char far *ItemText,
	WORD  TextLength,
	BOOL  Summary);
```
**Description :**

This function takes a handle to an open note, the name of the item to append, 
the text to store in the item and whether to set the ITEM_SUMMARY flag in the 
item.  It appends a TYPE_TEXT item to the open note. If an item of that name 
already exists, it deletes the existing item first, then appends the new item.

Note 1:  Use a null character ('\0') to force Notes to display a line break in 
a text field.  Insert null characters in the text where you need line breaks, 
and specify, in argument #4, the length of the string including all null 
characters. Do not use MAXWORD for this argument unless ItemText contains a 
null-terminated string. Do not place carriage return or line feed characters in 
the text buffer.  

Note 2: If the Summary parameter of NSFItemSetTextSummary is set to TRUE, the 
ITEM_SUMMARY flag in the item will be set. Items with the ITEM_SUMMARY flag set 
are stored in the note's summary buffer. These items may be used in view 
columns,  selection formulas, and @functions. The maximum size of the summary 
buffer is 32K per note. If you append more than 32K bytes of data in items that 
have the ITEM_SUMMARY flag set, NSFItemSetTextSummary (with the Summary 
parameter set to TRUE) will succeed, but NSFNoteUpdate will return 
ERR_SUMMARY_TOO_BIG. To avoid this, decide which fields are not used in view 
columns, selection formulas, or @ functions. For these "non-computed" fields, 
use NSFItemSetTextSummary with the Summary parameter set to FALSE.

API program may read, modify, and write items that do not have the summary flag 
set, but they must open the note first. Items that do not have the summary flag 
set can not be accessed in the summary buffer.

NSFItemSetTextSummary is similar to NSFItemSetText.  However, NSFItemSetText 
automatically sets the ITEM_SUMMARY flag in the item.  With 
NSFItemSetTextSummary, you specify whether to set this flag.

**Parameters :**
Input :
hNote  -  A handle to an open note.

ItemName  -  A pointer to a null-terminated Item name.

ItemText  -  A pointer a buffer containing the text you wish to store with the item.

TextLength  -  A WORD containing the length of the ItemText.  If MAXWORD is given, then the ItemText buffer must be null-terminated and NSFItemSetTextSummary will determine its length.  However, the length of the ItemText buffer cannot exceed MAXONESEGSIZE.

Summary  -  Use TRUE to set the ITEM_SUMMARY flag for this item, otherwise use FALSE (no ITEM flags will be set).

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - Successfully added Text Item to note.

ERR_xxx - Errors returned by lower level functions: (memory management, file operations, etc.).  There are so many possible causes, that it is best to use the code in a call to OSLoadString and display/log the error for the user as your default error handling.



**See Also :**
[NSFItemSetText](/reference/Func/NSFItemSetText)
[NSFItemGetText](/reference/Func/NSFItemGetText)
[NSFItemTextEqual](/reference/Func/NSFItemTextEqual)
[NSFNoteClose](/reference/Func/NSFNoteClose)
[NSFNoteOpen](/reference/Func/NSFNoteOpen)
---
