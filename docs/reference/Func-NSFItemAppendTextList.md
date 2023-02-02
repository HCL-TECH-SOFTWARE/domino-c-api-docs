##### Function : Item (Field)
##### NSFItemAppendTextList - Add an entry to a TYPE_TEXT_LIST item in a note.
---
##### #include <nsfnote.h>
STATUS LNPUBLIC **NSFItemAppendTextList(**

	NOTEHANDLE  note_handle,
	const char far *item_name,
	const char far *entry_text,
	WORD  text_len,
	BOOL  duplicate_flag);
**Description :**
This function takes a handle to an open note, the name for the text list Item 
you wish to add to , the text you wish to have added as the NEXT entry in the 
list and the length of that text string.  The last argument is a BOOL 
indicating whether or not you wish to allow the creation of duplicate strings 
in the list.  

If the text list Item does not already exist, one will be created using the 
name provided and the text provided as the FIRST entry.  The Item Flags are set 
to ITEM_SUMMARY.
**Parameters :**
Input :
note_handle  -  A handle to an open note (NOTEHANDLE).

item_name  -  A pointer to a null-terminated item name.

entry_text  -  A pointer to a string containing the text you wish to add as the NEXT entry in the existing text list in the open note.

text_len  -  A WORD containing the length of the string to be added.  If MAXWORD is specified, then the string is treated as a null-terminated string, and the length of the string is used instead.

duplicate_flag  -  A BOOL containing a flag indicating whether or not to allow duplicate entries in the text list.  TRUE - If you wish to allow them and FALSE - If you do not.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - Successfully added Text Entry to Text List Item in note.

ERR_MEMORY - Not enough global memory available for allocation

ERR_SEGMENT_TOO_BIG - Requested size is greater than the maximum supported (MAXWORD -  (2*sizeof(WORD)))

ERR_xxx - Errors returned by lower level functions: (memory management, file operations, etc.).  There are so many possible causes, that It is best to use the code in a call to OSLoadString and display/log the error for the user as your default error handling.


**Sample Usage :**
```

   if (error_status = NSFItemAppendTextList(note1_handle,
                                          TEXT_LIST_ITEM, SOME_TEXT2,
                                          MAXWORD,
                                          FALSE))
       goto Exit;


```
**See Also :**
[NSFItemCreateTextList](D:/md_files/NSFItemCreateTextList.md)
[NSFItemGetTextListEntries](D:/md_files/NSFItemGetTextListEntries.md)
[NSFItemGetTextListEntry](D:/md_files/NSFItemGetTextListEntry.md)
[NSFNoteClose](D:/md_files/NSFNoteClose.md)
[NSFNoteOpen](D:/md_files/NSFNoteOpen.md)
---
