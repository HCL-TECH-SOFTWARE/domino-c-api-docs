##### Data Type : Views
##### VIEW_TABLE_FORMAT3 - Contains additional view format information for Domino R5 and Notes/Domino 6.
---
```
#include <viewfmt.h>
```
**Description :**

This structure contains view format information for views saved in Domino 
Release 5 and later. This structure is one of the components of a $VIEWFORMAT 
item in a view note. 

	All view notes contain a $VIEWFORMAT item (also known as a "View Table 
Format" item).  A $VIEWFORMAT item is an item of TYPE_VIEW_FORMAT with item 
name VIEW_VIEW_FORMAT_ITEM. The item value of a $VIEWFORMAT item consists of a 
single VIEW_TABLE_FORMAT structure, followed by one VIEW_COLUMN_FORMAT 
structure for each column, followed by an item name/formula/column title set 
for each column, followed by a VIEW_TABLE_FORMAT2 structure, followed by one 
VIEW_COLUMN_FORMAT2 structure for each column, followed by a VIEW_TABLE_FORMAT3 
structure.

The fields in this record are:

Length - Length of this record
    Flags - See VTF3_xxx                 
BackgroundColor - R5 background color
AlternateBackgroundColor - R5 alternate row color
GridColorValue - Notes/Domino 6 grid color
	wViewMarginTop - Notes/Domino 6 view margin top
wViewMarginLeft - Notes/Domino 6 view margin left
wViewMarginRight - Notes/Domino 6 view margin right
wViewMarginBottom - Notes/Domino 6 view margin bottom
MarginBackgroundColor - Notes/Domino 6 view margin background color 
HeaderBackgroundColor - Notes/Domino 6 view column HeaderBackgroundColor 
wViewMarginTopUnder - View Margin top -- under header 
UnreadColor -  Notes/Domino 6 unread row color 
TotalsColor - Notes/Domino 6 Column Total Color 
        wMaxRows - Notes/Domino 7 Query view maximum row limit.
dwReserved[2] - Reserved for future use 

**See Also :**
[VTF3_xxx](/reference/Symb/VTF3_xxx)
---
