##### Data Type : Views
##### VIEW_TABLE_FORMAT3 - Contains additional view format information for Domino R5 and Notes/Domino 6.
---
```
#include <viewfmt.h>
```

**Definition :**

typedef struct
 {
 WORD Length;     /* Length of this structure */
 DWORD Flags;     /* Reserved for future use */
 COLOR_VALUE BackgroundColor;  /* V5 background color */
 COLOR_VALUE AlternateBackgroundColor;  /* V5 alternate row color */
 COLOR_VALUE GridColorValue;   /*  V6 View's grid color (3 words)*/
 WORD wViewMarginTop;    /*  V6 View Margin top */
 WORD wViewMarginLeft;   /*  V6 View Margin left */
 WORD wViewMarginRight;   /*  V6 View Margin right */
 WORD wViewMarginBottom;   /*  V6 View Margin bottom */
 COLOR_VALUE MarginBackgroundColor;  /*  V6 View Margin Background Color */
 COLOR_VALUE HeaderBackgroundColor;  /*  V6 View column header background color 
*/
 WORD wViewMarginTopUnder;   /*  V6 View Margin top -- under header */
	COLOR_VALUE UnreadColor;   /*  V6 unread row color */
 COLOR_VALUE TotalsColor;   /*  V6 Column Total Color */
 WORD  wMaxRows;    /*  V7 Query View Max Row Limit */
 WORD  wReserved;    /* Reserved for future use */  
 DWORD dwReserved[1];    /* Reserved for future use */ 
 } VIEW_TABLE_FORMAT3;

**Description :**

This structure contains view format information for views saved in Domino Release 5 and later. This structure is one of the components of a $VIEWFORMAT item in a view note. <br>
<br>
	All view notes contain a $VIEWFORMAT item (also known as a &quot;View Table Format&quot; item).  A $VIEWFORMAT item is an item of TYPE_VIEW_FORMAT with item name VIEW_VIEW_FORMAT_ITEM. The item value of a $VIEWFORMAT item consists of a single VIEW_TABLE_FORMAT structure, followed by one VIEW_COLUMN_FORMAT structure for each column, followed by an item name/formula/column title set for each column, followed by a VIEW_TABLE_FORMAT2 structure, followed by one VIEW_COLUMN_FORMAT2 structure for each column, followed by a VIEW_TABLE_FORMAT3 structure.<br>

<ul>The fields in this record are:<br>
<br>
Length - Length of this record</ul>
   	Flags - See VTF3_xxx                 <br>
BackgroundColor - R5 background color<br>
AlternateBackgroundColor - R5 alternate row color<br>
GridColorValue - Notes/Domino 6 grid color<br>
	wViewMarginTop - Notes/Domino 6 view margin top<br>
wViewMarginLeft - Notes/Domino 6 view margin left<br>
wViewMarginRight - Notes/Domino 6 view margin right<br>
wViewMarginBottom - Notes/Domino 6 view margin bottom<br>
MarginBackgroundColor - Notes/Domino 6 view margin background color <br>
HeaderBackgroundColor - Notes/Domino 6 view column HeaderBackgroundColor <br>
wViewMarginTopUnder - View Margin top -- under header <br>
UnreadColor -  Notes/Domino 6 unread row color <br>
TotalsColor - Notes/Domino 6 Column Total Color <br>
        wMaxRows - Notes/Domino 7 Query view maximum row limit.<br>
dwReserved[2] - Reserved for future use 


**See Also :**
[VTF3_xxx](/domino-c-api-docs/reference/Symb/VTF3_xxx)
---
