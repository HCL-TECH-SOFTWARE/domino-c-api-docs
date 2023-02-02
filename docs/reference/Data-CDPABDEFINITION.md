##### Data Type : Composite Data
##### CDPABDEFINITION - Defines a format for rich-text paragraphs.
---
##### #include <editods.h>
**Description :**
This structure specifies a format for paragraphs in a rich-text field. There 
may be more than one paragraph using the same paragraph format, but there may 
be no more than one CDPABDEFINITION with the same ID in a rich-text field.  

Note: All units in the fields of this structure are in TWIPS (1/20 of a 
point).  There are 72 points to an inch and 20 TWIPS to a point, and therefore 
there are 72 * 20 TWIPS to an inch.  Use the  #define ONEINCH to represent the 
number of TWIPS to an inch.  For example:

.LeftMargin = ONEINCH/2, .RightMargin = ONEINCH,  .FirstLineLeftMargin = 
(ONEINCH + ONEINCH/2), .TAB[0] = ONEINCH, .TAB[1] = 2*ONEINCH, etc.

As of R5, a CDPABDEFINITION structure can be followed by an array of six WORDs 
of margin values:
Margin [0] - Left margin offset in twips
Margin [1] - Left margin offset in percent (0 - 100)
Margin [2] - First line left margin offset in twips
Margin [3] - First line left margin offset in percent (0 - 100)
Margin [4] - Right margin offset in twips
Margin [5] - Right margin offset in percent (0 - 100)

If these "extension" words are present after a CDPABDEFINITION structure in an 
R5 database, then you should get the margin information from them.  If they are 
not present, then your code should get its margin values from the LeftMargin, 
FirstLineLeftMargin, and RightMargin elements of the CDPABDEFINITION 
structures, as was done in R4.

If R5 margin extension WORDs are present, then you can also use PABFLAG2_xxx 
masks defined in editdflt.h to tell which of the values to use:

PABFLAG2_LM_OFFSET
PABFLAG2_LM_PERCENT
PABFLAG2_FLLM_OFFSET
PABFLAG2_FLLM_PERCENT
PABFLAG2_RM_OFFSET
PABFLAG2_RM_PERCENT

If the Flags2 member of CDPABDEFINITION is set to PABFLAG2_MORE_FLAGS, the 
CDPABDEFINITION may be followed by a DWORD extension. If the value of this 
DWORD extension is EXTENDEDPABFLAGS3 (introduced in Notes/Domino 6), then a 
second DWORD extension may be present with a value of PABFLAG3_HIDE_EE. These 
DWORD extensions follow the six R5 margin extension WORDs, if they are present.

Note that rich text fields are items of type TYPE_COMPOSITE.  Therefore, API 
programs that run on non-Intel architecture platforms must perform 
host/canonical conversion on CD record structures such as this when accessing 
rich text item data in a note.

A rich text field consists of a series of CD records.  A paragraph in a rich 
text field normally starts with a CDPARAGRAPH record, followed by a 
CDPABREFERENCE record, followed by zero or more CDTEXT records.  The 
CDPABREFERENCE record specifies which of the CDPABDEFINITION records that 
appeared previously in the field define the paragraph style to use when 
displaying this paragraph. 

The sequence of CD records in a typical rich-text field might be:

CDPABDEFINITION    
CDPABDEFINITION    
CDPABDEFINITION    
...
CDPARAGRAPH   
CDPABREFERENCE
CDTEXT
text 
CDTEXT 
text
CDTEXT 
text
...
CDPARAGRAPH   
CDPABREFERENCE
CDTEXT
text 
CDTEXT 
text
...
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
[CDPABREFERENCE](D:/md_files/CDPABREFERENCE.md)
[CDPARAGRAPH](D:/md_files/CDPARAGRAPH.md)
[CDTEXT](D:/md_files/CDTEXT.md)
[EXTENDEDPABFLAGS3](D:/md_files/EXTENDEDPABFLAGS3.md)
[PABFLAG2_xxx](D:/md_files/PABFLAG2_xxx.md)
[PABFLAG3_xxx](D:/md_files/PABFLAG3_xxx.md)
[PABFLAG_xxx](D:/md_files/PABFLAG_xxx.md)
[SIG_CD_xxx](D:/md_files/SIG_CD_xxx.md)
---
