##### Function : Item (Field)
##### NSFItemCreateTextList - Append a TYPE_TEXT_LIST item to a note.
---
##### #include <nsfnote.h>
STATUS LNPUBLIC **NSFItemCreateTextList(**

	NOTEHANDLE  note_handle,
	const char far *item_name,
	const char far *item_text,
	WORD  text_len);
**Description :**
This function takes a handle to an open note, the name for the text list item 
you wish to append , the text you wish to have stored as the FIRST entry in the 
list and the length of that text string.  If an Item of that name already 
exists, it is first deleted and then the new value is appended with the same 
item name.

Note: NSFItemAppendTextList sets the ITEM_SUMMARY flag in the item. Items with 
the ITEM_SUMMARY flag set are stored in the note's summary buffer. These items 
may be used in view columns,  selection formulas, and @functions. API program 
may read the summary buffer without opening the note. The maximum size of the 
summary buffer is 32K per note. If you append more than 32K bytes of data in 
items that have the ITEM_SUMMARY flag set, NSFItemAppendTextList will succeed, 
but NSFNoteUpdate will return ERR_SUMMARY_TOO_BIG. To avoid this, decide which 
fields are not used in view columns, selection formulas, or @ functions. Append 
these "non-computed" fields to the document using NSFItemAppend without setting 
the ITEM_SUMMARY flag in the item_flags argument.
**Parameters :**
Input :
note_handle  -  A handle to an open note in memory.

item_name  -  A pointer to a null-terminated Item name.

item_text  -  A pointer a null-terminated LMBCS string containing the text you wish to add as the first entry in the text list being appended to the open note.  It can be no longer than 60K.

text_len  -  A WORD containing the length of the null-terminated LMBCS string text list entry.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - Successfully added Text List Item to note.

ERR_MEMORY - Not enough global memory available for allocation

ERR_SEGMENT_TOO_BIG - Requested size is greater than the maximum supported (60K).

ERR_xxx - Errors returned by lower level functions: (memory management, file operations, etc.).  There are so many possible causes, that It is best to use the code in a call to OSLoadString and display/log the error for the user as your default error handling.


**Sample Usage :**
```

   /* Create, populate, and store Item of TYPE_TEXT_LIST in  */
   /* in-memory copy of Note.                                */
 
  if (error_status = NSFItemCreateTextList(note1_handle,
                                          TEXT_LIST_ITEM,
                                          SOME_TEXT1,
                                          strlen(SOME_TEXT1)))
       goto Exit;
```
**See Also :**
[NSFItemAppendTextList](D:/md_files/NSFItemAppendTextList.md)
[NSFItemGetTextListEntries](D:/md_files/NSFItemGetTextListEntries.md)
[NSFItemGetTextListEntry](D:/md_files/NSFItemGetTextListEntry.md)
[NSFNoteClose](D:/md_files/NSFNoteClose.md)
[NSFNoteOpen](D:/md_files/NSFNoteOpen.md)
[NSFItemAppend](D:/md_files/NSFItemAppend.md)
---
