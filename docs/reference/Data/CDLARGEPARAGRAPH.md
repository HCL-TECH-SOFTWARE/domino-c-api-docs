##### Data Type : Composite Data
##### CDLARGEPARAGRAPH - Contains large paragraph information for Notes/Domino 6.
---
```
#include <editods.h>
```

**Definition :**

typedef struct {
	WSIG Header;  /* Signature and length of this record */
	WORD Version;
	WORD Flags;  
#define CDLARGEPARAGRAPH_BEGIN 0x0001
#define CDLARGEPARAGRAPH_END 0x0002
	DWORD Spare[2];
} CDLARGEPARAGRAPH;

**Description :**

The 64K limit on paragraphs has been removed in Notes/Domino 6.  To ensure backward compatibility, &quot;large&quot; paragraphs are broken into smaller paragraphs which are bracketed by a CDLARGEPARAGRAPH record with its Flags member set to CDLARGEPARAGRAPH_BEGIN and a CDLARGEPARAGRAPH record with its Flags member set to CDLARGEPARAGRAPH_END. 
<ul><br>
<br>
R5 will ignore the two CDLARGEPARAGRAPH records and load the small paragraphs. Notes/Domino 6 will combine the small paragraphs between these two CD records along with the paragraph which precedes them into one single paragraph at run-time and split them again when the document is saved.<br>
<br>
The fields in this structure are:<br>
<br>
    Header - Signature and length of this record.<br>
    <br>
    Version -  See LARGEPARAGRAPH_xxx.<br>
<br>
    Flags -  See CDLARGEPARAGRAPH_xxx.<br>
<br>
    Spare - Future use.<br>
<br>
Note that CDLARGEPARAGRAPH records reside in items of type TYPE_COMPOSITE. Therefore, API programs that run on non-Intel architecture platforms must perform host/canonical conversion on structures of this type when accessing these records in an item in a note.</ul>



**See Also :**
[CDLARGEPARAGRAPH_xxx](/domino-c-api-docs/reference/Symb/CDLARGEPARAGRAPH_xxx)
[LARGEPARAGRAPH_xxx](/domino-c-api-docs/reference/Symb/LARGEPARAGRAPH_xxx)
---
