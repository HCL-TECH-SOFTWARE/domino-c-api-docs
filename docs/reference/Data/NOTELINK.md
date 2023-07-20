##### Data Type : IDs
##### NOTELINK - The structure that uniquely describes a note in a document link.
---
```
#include <nsfdata.h>
```

**Definition :**
```
typedef struct {
   TIMEDATE File;  /* File's replica ID */
   UNID     View;  /* View's Note Creation TIMEDATE */
   UNID     Note;  /* Note's Creation TIMEDATE */
} NOTELINK;
```

**Description :**

This structure uniquely describes a particular instance of a note.  It is a component of a CDLINKEXPORT2 record, which constitutes a document link in a rich text field.  The members of this structure <br>
specify the target (&quot;linked-to&quot;) document.


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
[CompoundTextAddDocLink](/domino-c-api-docs/reference/Func/CompoundTextAddDocLink)
[CDLINKEXPORT2](/domino-c-api-docs/reference/Data/CDLINKEXPORT2)
[TIMEDATE](/domino-c-api-docs/reference/Data/TIMEDATE)
[UNID](/domino-c-api-docs/reference/Data/UNID)
[UNIVERSALNOTEID](/domino-c-api-docs/reference/Data/UNIVERSALNOTEID)
---
