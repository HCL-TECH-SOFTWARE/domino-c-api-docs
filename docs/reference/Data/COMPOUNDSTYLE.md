##### Data Type : Rich Text
##### COMPOUNDSTYLE - Defines a format for CompoundText
---
```
#include <easycd.h>
```

**Definition :**

typedef struct {
    WORD  JustifyMode;            /* paragraph justification type */
    WORD  LineSpacing;            /* Line spacing */
    WORD  ParagraphSpacingBefore; /* # units above paragraph */
    WORD  ParagraphSpacingAfter;  /* # units below paragraph */
    WORD  LeftMargin;             /* leftmost margin in twips */
    WORD  RightMargin;            /* rightmost margin in twips */
    WORD  FirstLineLeftMargin;    /* leftmost margin on first line */
    WORD  Tabs;                   /* # tab stops in table */
    SWORD Tab[MAXTABS];           /* table of tab stops */
    WORD  Flags;                  /* paragraph attribute flags */
} COMPOUNDSTYLE;

**Description :**

This structure specifies paragraph attributes for a style.  It is used  for CompoundText paragraphs and text.  It is similar to the CDPABDEFINITION structure.


**See Also :**
[CDPABDEFINITION](/domino-c-api-docs/reference/Data/CDPABDEFINITION)
---
