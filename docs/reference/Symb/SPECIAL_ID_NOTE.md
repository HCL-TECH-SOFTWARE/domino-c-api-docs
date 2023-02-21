##### Symbolic Value : IDs
##### SPECIAL_ID_NOTE - Used in combination with NOTE_CLASS_xxx when calling NSFDbGetSpecialNoteID.
---
```
#include <nsfdb.h>
```
**Description :**

Define NSF Special Note ID Indices. The first 16 of these are reserved for 
"default notes" in each of the 16 note classes. In order to access these, use 
SPECIAL_ID_NOTE+NOTE_CLASS_xxx.  This is generally used when calling 
NSFDbGetSpecialNoteID.  Note: NSFNoteOpen, NSFDbReadObject and NSFDbWriteObject 
support reading special notes or objects directly (without calling 
NSFDbGetSpecialNoteID). They use a DIFFERENT flag with a similar name: 
NOTE_ID_SPECIAL (see nsfnote.h).  Remember this rule:

 SPECIAL_ID_NOTE is a 16 bit mask and is used as a NoteClass argument.
 NOTE_ID_SPECIAL is a 32 bit mask and is used as a NoteID or RRV argument.

 Note: Whenever a new SPECIAL_ID is added, the table in \nsf\dbio\dbfhinfo.c 
must be updated. This table specifies which note class each SPECIAL_ID is 
treated as for access checking purposes.

**See Also :**
[NOTE_CLASS_xxx](/domino-c-api-docs/reference/Symb/NOTE_CLASS_xxx)
[NSFDbGetSpecialNoteID](/domino-c-api-docs/reference/Func/NSFDbGetSpecialNoteID)
---
