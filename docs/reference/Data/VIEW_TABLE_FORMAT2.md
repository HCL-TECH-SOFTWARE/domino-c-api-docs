##### Data Type : Views
##### VIEW_TABLE_FORMAT2 - Contains additional view format information.
---
```
#include <viewfmt.h>
```

**Definition :**

typedef struct {
   WORD Length;             /* Length of this structure */
   WORD BackgroundColor;    /* Color of view's background */
   WORD V2BorderColor;      /* Color of view's border lines */
   FONTID TitleFont;        /* Title and borders */
   FONTID UnreadFont;       /* Unread lines */
   FONTID TotalsFont;       /* Totals/Statistics */
   WORD AutoUpdateSeconds;  /* Interval b/w auto updates 
                               (zero for no autoupdate) */
   WORD AlternateBackgroundColor; /* Color of view's background for
                                     alternate rows. */
   WORD wSig;               /* see VALID_VIEW_FORMAT_SIG */

   BYTE LineCount;          /* Number of lines per row.  1, 2, etc.
                               see VIEW_TABLE_MAX_LINE_COUNT */
   BYTE Spacing;            /* Spacing. see VIEW_TABLE_xxx_SPACE */
   WORD BackgroundColorExt; /* Palette Color of view's background. */
   BYTE HeaderLineCount;    /* Lines per header. */
   BYTE Flags1;         /* see VIEW_TABLE_xxx */
   WORD Spare[4];           /* Spares.  Will be zero when
                                  wSig == VALID_VIEW_FORMAT_SIG. */
} VIEW_TABLE_FORMAT2;

**Description :**

This structure contains view format information for views saved in Notes 2.0 and later. This structure is one of the components of a $VIEWFORMAT item in a view note.  All view notes contain a $VIEWFORMAT item (also known as a &quot;View Table Format&quot; item). A $VIEWFORMAT item is an item of TYPE_VIEW_FORMAT with item name VIEW_VIEW_FORMAT_ITEM. The item value of a $VIEWFORMAT item consists of a single VIEW_TABLE_FORMAT structure, followed by one VIEW_COLUMN_FORMAT structure for each column, followed by an  item name/formula/column title set for each column, followed by a VIEW_TABLE_FORMAT2 structure, followed by one VIEW_COLUMN_FORMAT2 structure for each column, followed by a VIEW_TABLE_FORMAT3 structure.


**Sample Usage :**
```

VIEW_TABLE_FORMAT2     ViewTableFormat2;

/*
 * Initialize the VIEW_TABLE_FORMAT2 structure.
 */
memset (&ViewTableFormat2, 0, sizeof(VIEW_TABLE_FORMAT2));

ViewTableFormat2.Length = sizeof(VIEW_TABLE_FORMAT2);
ViewTableFormat2.BackgroundColor = NOTES_COLOR_WHITE;
ViewTableFormat2.V2BorderColor = 0;
ViewTableFormat2.TitleFont = DEFAULT_BOLD_FONT_ID;
ViewTableFormat2.UnreadFont = DEFAULT_FONT_ID;
ViewTableFormat2.TotalsFont = DEFAULT_FONT_ID;
ViewTableFormat2.AutoUpdateSeconds = 0;

/*
 * Convert the View Table Format2 structure to Domino canonical
 * format and append it to the buffer. This increments pVFBuf to 
 * point to the next byte after the View Table Format2 structure.
 */

ODSWriteMemory( &pVFBuf, _VIEW_TABLE_FORMAT2, &ViewTableFormat2, 1 );

/*
 * Now append the View Table Format item to the note.
 */

sError = NSFItemAppend( hNote,
                        ITEM_SUMMARY,
                        VIEW_VIEW_FORMAT_ITEM,
                        sizeof(VIEW_VIEW_FORMAT_ITEM) - 1,
                        TYPE_VIEW_FORMAT,
                        pViewFormatBuffer,
                        (DWORD)wViewFormatBufLen );
```

**See Also :**
[TYPE_xxx](/domino-c-api-docs/reference/Symb/TYPE_xxx)
[VIEW_COLUMN_FORMAT](/domino-c-api-docs/reference/Data/VIEW_COLUMN_FORMAT)
[VIEW_TABLE_FORMAT](/domino-c-api-docs/reference/Data/VIEW_TABLE_FORMAT)
---
