##### Function : Item (Field)
##### NSFLocateSummaryValue - Get any item value in a Summary Buffer.
---
```
#include <nsfnote.h>
BOOL LNPUBLIC NSFLocateSummaryValue(

	const void far *summary_buffer_ptr,
	const char far *item_name,
	void far * far *item_value_ptr_ptr,
	WORD far *item_len_ptr,
	WORD far *item_type_ptr);
```
**Description :**

This routine locates item values in the Summary Buffer of a note.  A Summary 
Buffer is an ITEM_TABLE containing an array of some of the items associated 
with that note. Only items that have the ITEM_SUMMARY flag set can reside in 
the summary buffer. Obtain summary buffers by calling functions 
NIFReadEntries() or NSFSearch().

Use NSFLocateSummaryValue to obtain item values when you know the item names 
and would like to avoid opening the note. NSFLocateSummaryValue is particularly 
valuable when performance is a concern because it does not require that you 
open the note before reading item values.

Items have the ITEM_SUMMARY flag set if the ItemFlags argument of NSFItemAppend 
specified ITEM_SUMMARY when the item was added to the note. Note that functions 
such as NSFItemSetText and NSFItemSetNumber will set the ITEM_SUMMARY flag.

Summary items can be used in formulas, view columns, and view selection 
criteria. If an item is not marked ITEM_SUMMARY, it cannot be used in a view, 
nor will it be returned in the Summary Buffer obtained via  NIFReadEntries() or 
NSFSearch().

**Parameters :**
Input :
summary_buffer_ptr  -  A pointer to a buffer containing a summary buffer (ITEM_TABLE).

item_name  -  The null-terminated item name whose value you want to obtain.

Output :
(routine)  -  Returned from this call-

TRUE - Item was found.
FALSE - Item was NOT found.


item_value_ptr_ptr  -  The address of a void pointer in which the address of the item's value (within the Summary Buffer) will be returned.

item_len_ptr  -  The address of a WORD in which the total length of the item's value will be returned.

item_type_ptr  -  The address of a WORD in which the Domino data type of the requested item will be returned.


**Sample Usage :**
```

HANDLE buffer_handle;
BYTE     *summary;
char     *szItemName;
BOOL      Found;
char     *item_value_ptr;
WORD      Length, Type;

NIFReadEntries(coll_handle, &coll_pos, NAVIGATE_CURRENT, 0,
              NAVIGATE_NEXT, 0xFFFF, READ_MASK_SUMMARY,
              &buffer_handle, NULL, NULL, &entries_found, NULL);

summary = (BYTE *) OSLockObject (buffer_handle);

szItemName = "Subject";

Found = NSFLocateSummaryValue(summary, 
                szItemName, &item_value_ptr, &Length, &Type);

if (Found)
{
    printf ("Found field '%s'\n", szItemName);
}            

OSUnlockObject (buffer_handle);
OSMemFree (buffer_handle)
```
**See Also :**
[NSFGetSummaryValue](/domino-c-api-docs/reference/Func/NSFGetSummaryValue)
[NSFItemAppend](/domino-c-api-docs/reference/Func/NSFItemAppend)
[NSFSearch](/domino-c-api-docs/reference/Func/NSFSearch)
[NIFReadEntries](/domino-c-api-docs/reference/Func/NIFReadEntries)
---
