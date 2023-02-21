##### Function : Item (Field)
##### NSFItemScan - Calls action routine for each item found in a note.
---
```
#include <nsfnote.h>
STATUS NSFItemScan(

	NOTEHANDLE  note_handle,
	NSFITEMSCANPROC  ActionRoutine,
	void far *func_param);
```
**Description :**

This function finds all the fields in a note. As it does so, NSFItemScan calls 
a user-supplied action routine for each field (item) in the note. The action 
routine can read the contents of the field, then returns control to NSFItemScan 
so the next field can be found.

This function, and your action routine, enables your program to open a note and 
determine which items (if any) are present. Then for each field, your program 
can find the field's data type, item flags, name, and contents -- all without 
knowing the form that was used to create the note.

The action routine can read the contents and properties of each field, but may 
not modify a field. This is because the action routine is passed the actual 
memory pointers of the field contents, and these should not be modified. If you 
want to modify a field, do so with the NSFItemSet* functions or with 
NSFItemDelete/NSFItemAppend. Modify fields only after NSFItemScan has completed 
-- not while it is still finding fields.

**Parameters :**
Input :
note_handle  -  handle to open note, whose items you wish to scan/enumerate in the action routine.

ActionRoutine  -  Pointer to the routine, that you write, which is called for each item in a note.  The pointer is of type NSFITEMSCANPROC.  NSFItemScan calls this routine for every item in the note before returning.  . The routine has the following prototype:  

STATUS LNCALLBACK ActionRoutine(WORD Spare, WORD ItemFlags, char far *Name, WORD NameLength,
						void far *Value, DWORD ValueLength, void far *RoutineParameter);

func_param  -  An optional void pointer to additional data that can be used by the action routine.

Output :
(routine)  -  Return status from the action routine -- indicates either success or what the error is. The action routine should be coded to at least return the following codes:

NOERROR - no error occurred in action routine.

ERR_xxx - Errors returned by lower level functions, including the action routine itself. 



**Sample Usage :**
```

/* Scan all the fields in the note, calling an action routine for each. */

 if (error = NSFItemScan (
   note_handle, /* note handle */
   field_action, /* action routine for fields */
   &note_handle)) /* argument to action routine */
  {
  NSFNoteClose (note_handle);
  return (ERR(error));
  }

.
.
.


/*
This is the action routine that is called by NSFItemScan for each field in
the note.
*/

STATUS LNCALLOBACK field_action
   (WORD unused,
   WORD item_flags,
   char far *name_ptr,
   WORD name_len,
   void far *item_value,
   DWORD item_value_len,
   void far *note_handle)
{
}


```
**See Also :**
[NSFItemAppend](/domino-c-api-docs/reference/Func/NSFItemAppend)
[NSFItemInfo](/domino-c-api-docs/reference/Func/NSFItemInfo)
[NSFItemQuery](/domino-c-api-docs/reference/Func/NSFItemQuery)
[NSFITEMSCANPROC](/domino-c-api-docs/reference/Data/NSFITEMSCANPROC)
[NSFNoteClose](/domino-c-api-docs/reference/Func/NSFNoteClose)
[NSFNoteOpen](/domino-c-api-docs/reference/Func/NSFNoteOpen)
---
