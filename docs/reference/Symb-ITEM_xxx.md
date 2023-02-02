##### Symbolic Value : Field
##### ITEM_xxx - Flags attached to an item in a note.
---
##### #include <nsfnote.h>
**Description :**
These flags define the characteristics of an item (field) in a note.  The flags 
may be bitwise or'ed together for combined functionality.
**Sample Usage :**
```
    if (error = NSFItemAppend ( hNote, 
                                ITEM_SUMMARY | ITEM_READWRITERS | ITEM_NAMES,
                                DISCUSS_ITEM_AUTHOR,  /* "Author" */
                                strlen(DISCUSS_ITEM_AUTHOR),
                                TYPE_TEXT,
                                szAuthor,
                                strlen(szAuthor)))
    {
        printf ("Error: unable to append Author field.\n");
    }
```
**See Also :**
[ITEM_xxx [NAMES]](D:/md_files/ITEM_xxx [NAMES].md)
[ITEM_xxx [READERS]](D:/md_files/ITEM_xxx [READERS].md)
[ITEM_xxx [READWRITERS]](D:/md_files/ITEM_xxx [READWRITERS].md)
[NSFItemAppend](D:/md_files/NSFItemAppend.md)
[TYPE_xxx](D:/md_files/TYPE_xxx.md)
---
