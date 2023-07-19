##### Data Type : Composite Data
##### CDPABDEFINITION - Defines a format for rich-text paragraphs.
---
```
#include <editods.h>
```

**Definition :**

typedef struct {
   WSIG Header;        /* Used to quickly recognize structure type */
   WORD PABID;         /* ID of this PAB */
   WORD JustifyMode;   /* paragraph justification type */
   WORD LineSpacing;   /* (2*(Line Spacing-1)) (0:1,1:1.5,2:2,etc) */
   WORD ParagraphSpacingBefore; /* # LineSpacing units above para */
   WORD ParagraphSpacingAfter;  /* # LineSpacing units below para */
   WORD LeftMargin;    /* leftmost margin, twips rel to abs left */
                       /* (16 bits = about 44") */
   WORD RightMargin;   /* rightmost margin, twips rel to abs right */
                       /* (16 bits = about 44") */
                       /* Special value "0" means right margin */
                       /* will be placed 1" from right edge of */
                       /* paper, regardless of paper size. */
   WORD FirstLineLeftMargin; /* leftmost margin on first line */
                       /* (16 bits = about 44") */
   WORD Tabs;          /* number of tab stops in table */
   SWORD Tab[MAXTABS]; /* table of tab stop positions, negative */
                       /* value means decimal tab */
                       /* (15 bits = about 22") */
   WORD Flags;         /* paragraph attribute flags - PABFLAG_xxx */
   DWORD TabTypes;     /* 2 bits per tab */
   WORD Flags2;        /* extra paragraph attribute flags - PABFLAG2_xxx */
} CDPABDEFINITION;

**Description :**

This structure specifies a format for paragraphs in a rich-text field. There may be more than one paragraph using the same paragraph format, but there may be no more than one CDPABDEFINITION with the same ID in a rich-text field.  <br>
<br>
Note: All units in the fields of this structure are in TWIPS (1/20 of a point).  There are 72 points to an inch and 20 TWIPS to a point, and therefore there are 72 * 20 TWIPS to an inch.  Use the  #define ONEINCH to represent the number of TWIPS to an inch.  For example:<br>
<br>
.LeftMargin = ONEINCH/2, .RightMargin = ONEINCH,  .FirstLineLeftMargin = (ONEINCH + ONEINCH/2), .TAB[0] = ONEINCH, .TAB[1] = 2*ONEINCH, etc.<br>

<ul>As of R5, a CDPABDEFINITION structure can be followed by an array of six WORDs of margin values:
<ul>Margin [0]	- Left margin offset in twips<br>
Margin [1]	- Left margin offset in percent (0 - 100)<br>
Margin [2]	- First line left margin offset in twips<br>
Margin [3]	- First line left margin offset in percent (0 - 100)<br>
Margin [4]	- Right margin offset in twips<br>
Margin [5]	- Right margin offset in percent (0 - 100)<br>
</ul>
If these &quot;extension&quot; words are present after a CDPABDEFINITION structure in an R5 database, then you should get the margin information from them.  If they are not present, then your code should get its margin values from the LeftMargin, FirstLineLeftMargin, and RightMargin elements of the CDPABDEFINITION structures, as was done in R4.<br>
<br>
If R5 margin extension WORDs are present, then you can also use PABFLAG2_xxx masks defined in editdflt.h to tell which of the values to use:</ul>

<ul>
<ul>PABFLAG2_LM_OFFSET<br>
PABFLAG2_LM_PERCENT<br>
PABFLAG2_FLLM_OFFSET<br>
PABFLAG2_FLLM_PERCENT<br>
PABFLAG2_RM_OFFSET<br>
PABFLAG2_RM_PERCENT</ul>
<br>
If the Flags2 member of CDPABDEFINITION is set to PABFLAG2_MORE_FLAGS, the CDPABDEFINITION may be followed by a DWORD extension. If the value of this DWORD extension is EXTENDEDPABFLAGS3 (introduced in Notes/Domino 6), then a second DWORD extension may be present with a value of PABFLAG3_HIDE_EE. These DWORD extensions follow the six R5 margin extension WORDs, if they are present.<br>
<br>
Note that rich text fields are items of type TYPE_COMPOSITE.  Therefore, API programs that run on non-Intel architecture platforms must perform host/canonical conversion on CD record structures such as this when accessing rich text item data in a note.<br>
<br>
A rich text field consists of a series of CD records.  A paragraph in a rich text field normally starts with a CDPARAGRAPH record, followed by a CDPABREFERENCE record, followed by zero or more CDTEXT records.  The CDPABREFERENCE record specifies which of the CDPABDEFINITION records that appeared previously in the field define the paragraph style to use when displaying this paragraph. <br>
<br>
The sequence of CD records in a typical rich-text field might be:<br>
<br>
CDPABDEFINITION    <br>
CDPABDEFINITION    <br>
CDPABDEFINITION    <br>
...<br>
CDPARAGRAPH	  <br>
CDPABREFERENCE<br>
CDTEXT<br>
text	<br>
CDTEXT	<br>
text<br>
CDTEXT	<br>
text<br>
...<br>
CDPARAGRAPH	  <br>
CDPABREFERENCE<br>
CDTEXT<br>
text	<br>
CDTEXT	<br>
text<br>
...</ul>



**Sample Usage :**
```
/* Initialize a CDPABDEFINITION structure.  We use all defaults, 
   except for centered justification. 
 */

pabdef.Header.Signature = SIG_CD_PABDEFINITION;
pabdef.Header.Length = ODSLength( _CDPABDEFINITION );
pabdef.PABID = PARA_STYLE_ID;
pabdef.JustifyMode = JUSTIFY_CENTER;
pabdef.LineSpacing = DEFAULT_LINE_SPACING;
pabdef.ParagraphSpacingBefore = DEFAULT_ABOVE_PAR_SPACING;
pabdef.ParagraphSpacingAfter = DEFAULT_BELOW_PAR_SPACING;
pabdef.LeftMargin = DEFAULT_LEFT_MARGIN;
pabdef.RightMargin = DEFAULT_RIGHT_MARGIN;
pabdef.FirstLineLeftMargin = DEFAULT_FIRST_LEFT_MARGIN;
pabdef.Tabs = DEFAULT_TABS;
pabdef.Tab[0] = DEFAULT_TAB_INTERVAL;
pabdef.Flags = 0;
	pabdef.TabTypes = TAB_DEFAULT;
pabdef.Flags2 = DEFAULT_FLAGS2;

/* Call ODSWriteMemory to convert the CDPABDEFINITION structure to 
   Domino canonical format and write the converted structure into
   the buffer at location buff_ptr. This advances buff_ptr to the
   next byte in the buffer after the canonical format strucure.
 */
    
ODSWriteMemory( &buff_ptr, _CDPABDEFINITION, &pabdef, 1 );
```

**See Also :**
[CDPABREFERENCE](/domino-c-api-docs/reference/Data/CDPABREFERENCE)
[CDPARAGRAPH](/domino-c-api-docs/reference/Data/CDPARAGRAPH)
[CDTEXT](/domino-c-api-docs/reference/Data/CDTEXT)
[EXTENDEDPABFLAGS3](/domino-c-api-docs/reference/Symb/EXTENDEDPABFLAGS3)
[PABFLAG2_xxx](/domino-c-api-docs/reference/Symb/PABFLAG2_xxx)
[PABFLAG3_xxx](/domino-c-api-docs/reference/Symb/PABFLAG3_xxx)
[PABFLAG_xxx](/domino-c-api-docs/reference/Symb/PABFLAG_xxx)
[SIG_CD_xxx](/domino-c-api-docs/reference/Symb/SIG_CD_xxx)
---
