##### Function : Item (Field)
##### NSFItemSetNumber - Append an Item of TYPE_NUMBER to a note.
---
```
#include <nsfnote.h>
STATUS LNPUBLIC NSFItemSetNumber(

	NOTEHANDLE  hNote,
	const char far *ItemName,
	const NUMBER far *Number);
```
**Description :**

This function takes a handle to an open note, the name for the Item you wish to 
append and the NUMBER you wish to have stored in that Item.  It an Item of that 
name already exists, it is first deleted and then the new value is appended 
with the same Item name. 

Note: NSFItemSetNumber sets the ITEM_SUMMARY flag in the item.  Items with the 
ITEM_SUMMARY flag set are stored in the note's summary buffer.  These items may 
be used in view columns,  selection formulas, and @functions.  The maximum size 
of the summary buffer is 32K per note.  If you append more than 32K bytes of 
data in items that have the ITEM_SUMMARY flag set, NSFItemSetNumber will 
succeed, but NSFNoteUpdate will return ERR_SUMMARY_TOO_BIG. To avoid this, 
decide which fields are not used in view columns, selection formulas, or @ 
functions.  For these "non-computed" fields, do not use the higher-level API 
functions such as NSFItemSetText and NSFItemSetNumber. Instead, use 
NSFItemAppend to append these items to the document without setting the 
ITEM_SUMMARY flag in the item_flags argument.  

API programs may read, modify, and write items that do not have the summary 
flag set, but they must open the note first. Items that do not have the summary 
flag set can not be accessed in the summary buffer.

**Parameters :**
Input :
hNote  -  A handle to an open note in memory.

ItemName  -  A pointer to a null-terminated item name.

Number  -  A pointer to a NUMBER (or equivalent 'double') variable containing the value to which the named item should be set.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - Successfully added NUMBER Item to note.

ERR_xxx - Errors returned by lower level functions: (memory management, file operations, etc.).  There are so many possible causes, that It is best to use the code in a call to OSLoadString and display/log the error for the user as your default error handling.



**Sample Usage :**
```
/* Store Item of TYPE_NUMBER in in-memory copy of note */
 
num = 3.43343343E6;
if (error_status = NSFItemSetNumber(note1_handle, FLOAT_ITEM, &num))
  goto Exit;
```
**See Also :**
[NSFItemGetLong](/reference/Func/NSFItemGetLong)
[NSFItemGetNumber](/reference/Func/NSFItemGetNumber)
[NSFItemLongCompare](/reference/Func/NSFItemLongCompare)
[NSFNoteClose](/reference/Func/NSFNoteClose)
[NSFNoteOpen](/reference/Func/NSFNoteOpen)
[NSFItemAppend](/reference/Func/NSFItemAppend)
---
