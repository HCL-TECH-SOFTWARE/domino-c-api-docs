##### Function : Item (Field)
##### NSFItemSetTime - Append an Item of TYPE_TIME to a note.
---
```
#include <nsfnote.h>
STATUS LNPUBLIC NSFItemSetTime(

	NOTEHANDLE  note_handle,
	const char far *td_item_name,
	const TIMEDATE far *td_item_ptr);
```
**Description :**

This function takes a handle to an open note, the name for the Item you wish to 
append and the TIMEDATE  you wish to have stored in that Item.  It an Item of 
that name already exists, it is first deleted and then the new value is 
appended with the same Item name. 

Note: NSFItemSetTime sets the ITEM_SUMMARY flag in the item. Items with the 
ITEM_SUMMARY flag set are stored in the note's summary buffer. These items may 
be used in view columns,  selection formulas, and @functions. The maximum size 
of the summary buffer is 32K per note. If you append more than 32K bytes of 
data in items that have the ITEM_SUMMARY flag set, NSFItemSetTime will succeed, 
but NSFNoteUpdate will return ERR_SUMMARY_TOO_BIG. To avoid this, decide which 
fields are not used in view columns, selection formulas, or @ functions. For 
these "non-computed" fields, do not use the higher-level API functions such as 
NSFItemSetText and NSFItemSetTime. Instead, use NSFItemAppend to append these 
items to the document without setting the ITEM_SUMMARY flag in the item_flags 
argument.  

API program may read, modify, and write items that do not have the summary flag 
set, but they must open the note first. Items that do not have the summary flag 
set can not be accessed in the summary buffer.

**Parameters :**
Input :
note_handle  -  A handle to an open note in memory.

td_item_name  -  A pointer to a null-terminated Item name.  

td_item_ptr  -  A pointer to the TIMEDATE structure you wish to append to the open note.
The TIMEDATE structure is a binary representation of a time/date.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - Successfully added TIMEDATE Item to the note.

ERR_xxx - Errors returned by lower level functions: (memory management, file operations, etc.).  There are so many possible causes, that It is best to use the code in a call to OSLoadString and display/log the error for the user as your default error handling.



**Sample Usage :**
```


   /* Store Item of TYPE_TIME in in-memory copy of Note */

   OSGetIntlSettings(&intl_format);
   OSCurrentTIMEDATE(&original_td);
   if (error_status = NSFItemSetTime(note1_handle, TIME_ITEM,
                                     &original_td))
       goto Exit;

```
**See Also :**
[NSFItemGetTime](/reference/Func/NSFItemGetTime)
[NSFItemTimeCompare](/reference/Func/NSFItemTimeCompare)
[NSFNoteClose](/reference/Func/NSFNoteClose)
[NSFNoteOpen](/reference/Func/NSFNoteOpen)
[NSFItemAppend](/reference/Func/NSFItemAppend)
---
