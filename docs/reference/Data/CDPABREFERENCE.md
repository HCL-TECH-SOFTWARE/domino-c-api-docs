##### Data Type : Composite Data
##### CDPABREFERENCE - Which CDPABDEFINITION is used by paragraph.
---
```
#include <editods.h>
```

**Definition :**

typedef struct {
   BSIG Header;
   WORD PABID; /* ID number of the CDPABDEFINITION */
               /* used by this paragraph */
} CDPABREFERENCE;



**Description :**

This structure is placed at the start of each paragraph in a rich-text field, and specifies which CDPABDEFINITION is used as the format for the paragraph.<br>
<br>
Note that rich text fields are items of type TYPE_COMPOSITE. Therefore, API programs that run on non-Intel architecture platforms must perform host/canonical conversion on CD record structures such as this when accessing rich text item data in a note.<br>
<br>
Rich text fields consist of a series of CD records. A typical rich text field may have a series of CD records such as this:<br>
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
...<br>



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
[CDPABDEFINITION](/domino-c-api-docs/reference/Data/CDPABDEFINITION)
[CDPABFORMULAREF](/domino-c-api-docs/reference/Data/CDPABFORMULAREF)
[CDPARAGRAPH](/domino-c-api-docs/reference/Data/CDPARAGRAPH)
[CDTEXT](/domino-c-api-docs/reference/Data/CDTEXT)
[SIG_CD_xxx](/domino-c-api-docs/reference/Symb/SIG_CD_xxx)
---
