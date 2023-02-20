##### Symbolic Value : IDs
##### NOTE_ID_SPECIAL - Used in combination with NOTE_CLASS_xxx when calling NSFNoteOpen or NIFOpenCollection.
---
```
#include <nsfnote.h>
```
**Description :**

If NOTE_ID_SPECIAL is OR'ed in with a note class (NOTE_CLASS_xxx), the 
resulting note ID may be passed into NSFNoteOpen and may be treated as though 
you first did an NSFDbGetSpecialNoteID followed by an NSFNoteOpen, all in a 
single transaction.

If NOTE_ID_SPECIAL is OR'ed with NOTE_CLASS_DESIGN, the resulting note ID may 
be specified in the ViewNoteID parameter of NIFOpenCollection to open the 
design collection.

**See Also :**
[NOTE_CLASS_xxx](/reference/Symb/NOTE_CLASS_xxx)
[NSFDbOpen](/reference/Func/NSFDbOpen)
[NIFOpenCollection](/reference/Func/NIFOpenCollection)
[NSFDbGetSpecialNoteID](/reference/Func/NSFDbGetSpecialNoteID)
---
