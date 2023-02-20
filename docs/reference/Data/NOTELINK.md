##### Data Type : IDs
##### NOTELINK - The structure that uniquely describes a note in a document link.
---
```
#include <nsfdata.h>
```
**Description :**

This structure uniquely describes a particular instance of a note.  It is a 
component of a CDLINKEXPORT2 record, which constitutes a document link in a 
rich text field.  The members of this structure 
specify the target ("linked-to") document.

**Sample Usage :**
```
    /*
     * Create the IDs for both of the Notes (view and data)
     */

    NoteUNID.File = NoteOID.File;
    NoteUNID.Note = NoteOID.Note;

    ViewUNID.File = ViewOID.File;
    ViewUNID.Note = ViewOID.Note;

    /*
     * Fill in the CDLINKEXPORT2 structure
     */

    /* 1. File's replica ID */
    
    pCDLink->NoteLink.File = DBReplica.ID;

    /* 2. View Note's UNID (contains the Creation TIMEDATE) */

    memmove(&pCDLink->NoteLink.View, &ViewUNID, sizeof(UNID));
    
    /* 3. Note's UNID (contains the Creation TIMEDATE) */

    memmove(&pCDLink->NoteLink.Note, &NoteUNID, sizeof(UNID));
```
**See Also :**
[CompoundTextAddDocLink](/reference/Func/CompoundTextAddDocLink)
[CDLINKEXPORT2](/reference/Data/CDLINKEXPORT2)
[TIMEDATE](/reference/Data/TIMEDATE)
[UNID](/reference/Data/UNID)
[UNIVERSALNOTEID](/reference/Data/UNIVERSALNOTEID)
---
