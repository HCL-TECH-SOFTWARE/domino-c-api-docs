##### Data Type : Composite Data
##### CDPABREFERENCE - Which CDPABDEFINITION is used by paragraph.
---
##### #include <editods.h>
**Description :**
This structure is placed at the start of each paragraph in a rich-text field, 
and specifies which CDPABDEFINITION is used as the format for the paragraph.

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

/* Put a paragraph reference block in the field. Specify 
   PARA_STYLE_ID so that this paragraph uses the style 
   defined above.
*/

ref.Header.Signature = SIG_CD_PABREFERENCE;
ref.Header.Length = (BYTE) ODSLength( _CDPABREFERENCE );
ref.PABID = PARA_STYLE_ID;

/* Convert the structure to Domino canonical format and store
   the converted structure in the buffer.
*/
    
ODSWriteMemory( &buff_ptr, _CDPABREFERENCE, &ref, 1 );

```
**See Also :**
[CDPABDEFINITION](D:/md_files/CDPABDEFINITION.md)
[CDPABFORMULAREF](D:/md_files/CDPABFORMULAREF.md)
[CDPARAGRAPH](D:/md_files/CDPARAGRAPH.md)
[CDTEXT](D:/md_files/CDTEXT.md)
[SIG_CD_xxx](D:/md_files/SIG_CD_xxx.md)
---
