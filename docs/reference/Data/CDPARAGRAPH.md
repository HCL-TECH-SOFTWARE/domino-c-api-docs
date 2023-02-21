##### Data Type : Composite Data
##### CDPARAGRAPH - Starts a new paragraph.
---
```
#include <editods.h>
```
**Description :**

This structure defines the start of a new paragraph within a rich-text field.  
Each paragraph in a rich text field may have different style attributes, such 
as indentation and interline spacing. Use this structure when accessing a rich 
text field at the level of the CD records.

Note that rich text fields are items of type TYPE_COMPOSITE. Therefore, API 
programs that run on non-Intel architecture platforms must perform 
host/canonical conversion on CD record structures such as this when accessing 
rich text item data in a note.

Rich text fields consist of a series of CD records. A typical rich text field 
may have a series of CD records such as this:

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
    /* Put a paragraph header in the field. */
    
    para.Header.Signature = SIG_CD_PARAGRAPH;
    para.Header.Length = (BYTE) ODSLength( _CDPARAGRAPH );

    ODSWriteMemory( &buff_ptr, _CDPARAGRAPH, &para, 1 );
    
```
**See Also :**
[CDPABDEFINITION](/domino-c-api-docs/reference/Data/CDPABDEFINITION)
[CDPABREFERENCE](/domino-c-api-docs/reference/Data/CDPABREFERENCE)
[CDTEXT](/domino-c-api-docs/reference/Data/CDTEXT)
[SIG_CD_xxx](/domino-c-api-docs/reference/Symb/SIG_CD_xxx)
---
