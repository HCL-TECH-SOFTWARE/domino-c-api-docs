##### Symbolic Value : Note
##### NOTE_CLASS_xxx - Types of notes.
---
```
#include <nsfnote.h>
```

**Symbolic Values :**

	NOTE_CLASS_DOCUMENT	  -  Document (data) note.

	NOTE_CLASS_DATA	  -  Same as NOTE_CLASS_DOCUMENT - used prior to version 3.0 of the API.

	NOTE_CLASS_INFO	  -  Database Policy note also known as Help-About Database document.

	NOTE_CLASS_FORM	  -  Form note.

	NOTE_CLASS_VIEW	  -  View or folder note.

	NOTE_CLASS_ICON	  -  Icon note.

	NOTE_CLASS_DESIGN	  -  A special view note that is a collection of all forms, views, macros, and replicaton formulas.

	NOTE_CLASS_ACL	  -  Access control list note. (This note contains some information about the access control list. The note does not contain the access control list itself.)

	NOTE_CLASS_HELP_INDEX	  -  Domino built-in help index.

	NOTE_CLASS_HELP	  -  Database Help note also known as Help-Using Database document.

	NOTE_CLASS_FILTER	  -  Macro (filter) note.

	NOTE_CLASS_FIELD	  -  Shared field note.

	NOTE_CLASS_REPLFORMULA	  -  Replication formula note.

	NOTE_CLASS_PRIVATE	  -  Private design note, use $PrivateDesign view to locate/classify.

	NOTE_CLASS_DEFAULT	  -  Default note for the class. One note in each class may be marked with this flag, which indicates that this note is the default note for that class in this database (for example, a default form note or a default view note). The Note ID for each default note is stored in a table in the database. Document notes do not have a default. This flag cannot be used with NSFSearch; to locate the default form or view note, use NSFDbGetSpecialNoteID.

	NOTE_CLASS_NOTIFYDELETION	  -  Set by NSFSearch for deleted note. See SEARCH_xxx, SEARCH_NOTIFYDELETIONS.

	NOTE_CLASS_ALL	  -  All note types.

	NOTE_CLASS_ALLNONDATA	  -  All types of notes except data notes.

	NOTE_CLASS_NONE	  -  No notes.

	NOTE_CLASS_SINGLE_INSTANCE	  -  Symbol for those note classes that allow only one such note in a database: NOTE_CLASS_DESIGN | NOTE_CLASS_ACL | NOTE_CLASS_INFO | NOTE_CLASS_ICON | NOTE_CLASS_HELP_INDEX.

	NOTE_CLASS_NONPRIV    -  turn off the unthinkable bits and NOTE_CLASS_PRIVATE.


**Description :**

These bit masks define the types of notes in a database. The bit masks may be or'ed together to specify more than one type of note.<br>
<br>
NOTE_CLASS_DESIGN may be bitwise - ORed with NOTE_ID_SPECIAL to yield the note ID of the design collection of the database. This value (NOTE_CLASS_DESIGN | NOTE_ID_SPECIAL) may be specified in the ViewNoteID parameter of NIFOpenCollection to open the design collection. NOTE_CLASS_DESIGN may also be specified in the Index parameter of NSFDbGetSpecialNoteID to get the note ID of the design collection.


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
[NSFDbCopy](/domino-c-api-docs/reference/Func/NSFDbCopy)
[NSFSearch](/domino-c-api-docs/reference/Func/NSFSearch)
[NIFOpenCollection](/domino-c-api-docs/reference/Func/NIFOpenCollection)
[NSFDbGetSpecialNoteID](/domino-c-api-docs/reference/Func/NSFDbGetSpecialNoteID)
---
