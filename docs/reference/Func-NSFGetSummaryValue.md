##### Function : Item (Field)
##### NSFGetSummaryValue - Get a text item value from a Summary Buffer.
---
##### #include <nsfnote.h>
BOOL LNPUBLIC **NSFGetSummaryValue(**

	const void far *summary_buffer_ptr,
	const char far *text_item_name,
	char far *text_item_value,
	WORD  max_buffer_len);
**Description :**
This function obtains a text item's value from a Summary Buffer and as such, is 
a simplified form of NSFLocateSummaryValue().  A Summary Buffer is an 
ITEM_TABLE containing some of the items associated with a note and this 
function allows you to easily access TYPE_TEXT items.

If an item was added to the note with the ITEM_SUMMARY bit set in the ItemFlags 
argument of NSFItemAppend, then it is an item which can be returned in a 
Summary Buffer.  Summary Buffers are returned by functions such as 
NIFReadEntries() and NSFSearch().

Note:  the names and values of all items that have their ITEM_SUMMARY item flag 
set can be used in formulas and can therefore be displayed in a View.  If an 
item is not marked with the ITEM_SUMMARY flag, it cannot be used in a view, nor 
will be returned in the Summary Buffer that is returned by NSFSearch().
**Parameters :**
Input :
summary_buffer_ptr  -  A pointer to a summary buffer (ITEM_TABLE).

text_item_name  -  A pointer to a null-terminated item name whose value you want to obtain.

max_buffer_len  -  A WORD containing the total length of the buffer provided for this call.

Output :
(routine)  -  On Return from this call -

TRUE - Item was found.
FALSE - Item was NOT found.


text_item_value  -  The address of text buffer in which the null-terminated string value obtained from the summary buffer is returned.

**See Also :**
[NSFItemAppend](D:/md_files/NSFItemAppend.md)
[NSFLocateSummaryValue](D:/md_files/NSFLocateSummaryValue.md)
[NSFSearch](D:/md_files/NSFSearch.md)
[NIFReadEntries](D:/md_files/NIFReadEntries.md)
---
