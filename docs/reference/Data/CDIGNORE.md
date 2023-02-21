##### Data Type : Composite Data
##### CDIGNORE - Used to ignore a block of CD records for a particular version of Notes.
---
```
#include <editods.h>
```
**Description :**

Used to ignore a block of CD records for a particular version of Notes.  The 
block starts with a CDIGNORE with its dwFlags member set to FLAG_CDIGNORE_BEGIN 
and ends with another CDIGNORE record with its dwFlags member set to 
FLAG_CDIGNORE_END.  The CD records in between a CDIGNORE "begin" and a CDINGORE 
"end" should be ignored when the wNotesVersion is less than or equal to 
CDIGNORE_NOTES_VERSION_CURRENT. CDIGNORE records may be nested. 

The fields in this structure are:

Header - Signature and length of this record.
    
wNotesVersion - See CDIGNORE_NOTES_VERSION_xxx.

dwFlags -   See FLAG_CDIGNORE_xxx.

dwUnused - Reserved for future use. Should be zeroed out.

Note that CDIGNORE records reside in items of type TYPE_COMPOSITE. Therefore, 
API programs that run on non-Intel architecture platforms must perform 
host/canonical conversion on structures of this type when accessing these 
records in an item in a note.

**See Also :**
[ACTION_IGNORE_SYSTEM_ACTIONS_VERSION1](/domino-c-api-docs/reference/Symb/ACTION_IGNORE_SYSTEM_ACTIONS_VERSION1)
[CDIGNORE_NOTES_VERSION_xxx](/domino-c-api-docs/reference/Symb/CDIGNORE_NOTES_VERSION_xxx)
[FLAG_CDIGNORE_xxx](/domino-c-api-docs/reference/Symb/FLAG_CDIGNORE_xxx)
---
