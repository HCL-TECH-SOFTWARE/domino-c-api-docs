##### Symbolic Value : Note
##### NOTE_CLASS_xxx - Types of notes.
---
```
#include <nsfnote.h>
```
**Description :**

These bit masks define the types of notes in a database. The bit masks may be 
or'ed together to specify more than one type of note.

NOTE_CLASS_DESIGN may be bitwise - ORed with NOTE_ID_SPECIAL to yield the note 
ID of the design collection of the database. This value (NOTE_CLASS_DESIGN | 
NOTE_ID_SPECIAL) may be specified in the ViewNoteID parameter of 
NIFOpenCollection to open the design collection. NOTE_CLASS_DESIGN may also be 
specified in the Index parameter of NSFDbGetSpecialNoteID to get the note ID of 
the design collection.

**Sample Usage :**
```
    /*  Open the special "design" collection, which contains an index of
        all nondata notes. */

    if (error = NIFOpenCollection(hDB, 
                            hDB, 
                            NOTE_ID_SPECIAL+NOTE_CLASS_DESIGN,
                            OPEN_DO_NOT_CREATE,
                            NULLHANDLE,
                            &hCollection,
                            NULL, NULL, NULL, NULL))
   {    /* Collection may not have been setup yet by the first user to 
        open the file.*/
        printf("Unable to open the design collection for '%s'.\n",
                                         szDBTitle);
        NSFDbClose (hDB);
        return(ERR(error));
    }

```
**See Also :**
[NSFDbCopy](/reference/Func/NSFDbCopy)
[NSFSearch](/reference/Func/NSFSearch)
[NIFOpenCollection](/reference/Func/NIFOpenCollection)
[NSFDbGetSpecialNoteID](/reference/Func/NSFDbGetSpecialNoteID)
---
