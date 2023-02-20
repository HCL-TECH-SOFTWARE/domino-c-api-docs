##### Data Type : Composite Data
##### CDLARGEPARAGRAPH - Contains large paragraph information for Notes/Domino 6.
---
```
#include <editods.h>
```
**Description :**

The 64K limit on paragraphs has been removed in Notes/Domino 6.  To ensure 
backward compatibility, "large" paragraphs are broken into smaller paragraphs 
which are bracketed by a CDLARGEPARAGRAPH record with its Flags member set to 
CDLARGEPARAGRAPH_BEGIN and a CDLARGEPARAGRAPH record with its Flags member set 
to CDLARGEPARAGRAPH_END. 

R5 will ignore the two CDLARGEPARAGRAPH records and load the small paragraphs. 
Notes/Domino 6 will combine the small paragraphs between these two CD records 
along with the paragraph which precedes them into one single paragraph at 
run-time and split them again when the document is saved.

The fields in this structure are:

    Header - Signature and length of this record.
    
    Version -  See LARGEPARAGRAPH_xxx.

    Flags -  See CDLARGEPARAGRAPH_xxx.

    Spare - Future use.

Note that CDLARGEPARAGRAPH records reside in items of type TYPE_COMPOSITE. 
Therefore, API programs that run on non-Intel architecture platforms must 
perform host/canonical conversion on structures of this type when accessing 
these records in an item in a note.

**See Also :**
[CDLARGEPARAGRAPH_xxx](/reference/Symb/CDLARGEPARAGRAPH_xxx)
[LARGEPARAGRAPH_xxx](/reference/Symb/LARGEPARAGRAPH_xxx)
---
