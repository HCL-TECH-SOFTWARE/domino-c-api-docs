##### Symbolic Value : Field
##### ITEM_xxx - Flags attached to an item in a note.
---
```
#include <nsfnote.h>
```

**Symbolic Values :**

	ITEM_SIGN	  -  This item is signed.

	ITEM_SEAL	  -  This item is sealed. When used in NSFItemAppend, the item is encryption enabled; it can later be encrypted if edited from the Notes UI and saved in a form that specifies Encryption.

	ITEM_SUMMARY	  -  This item is stored in the note's summary buffer. Summary items may be used in view columns, selection formulas, and @functions. Summary items may be accessed via the SEARCH_MATCH structure provided by NSFSearch or in the buffer returned by NIFReadEntries. API program may read, modify, and write items in the summary buffer without opening the note first. The maximum size of the summary buffer is 32K. Items of TYPE_COMPOSITE may not have the ITEM_SUMMARY flag set.

	ITEM_READWRITERS	  -  This item is an Author Names field as indicated by the READ/WRITE-ACCESS flag. Item is TYPE_TEXT or TYPE_TEXT_LIST. Author Names fields have the ITEM_READWRITERS flag or'd with the ITEM_NAMES flag.

	ITEM_NAMES	  -  This item is a Names field. Indicated by the NAMES (distinguished names) flag. Item is TYPE_TEXT or TYPE_TEXT_LIST.

	ITEM_PLACEHOLDER	  -  This item is a placeholder field in a form note. Item is TYPE_INVALID_OR_UNKNOWN.

	ITEM_PROTECTED	  -  A user requires editor access to change this field.

	ITEM_READERS	  -  This is a Reader Names field. Indicated by the READER-ACCESS flag. Item is TYPE_TEXT or TYPE_TEXT_LIST.

	ITEM_UNCHANGED	  -  Item is same as on-disk.


**Description :**

These flags define the characteristics of an item (field) in a note.  The flags may be bitwise or'ed together for combined functionality.


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
[ITEM_xxx [NAMES]](/domino-c-api-docs/reference/Symb/ITEM_xxx [NAMES])
[ITEM_xxx [READERS]](/domino-c-api-docs/reference/Symb/ITEM_xxx [READERS])
[ITEM_xxx [READWRITERS]](/domino-c-api-docs/reference/Symb/ITEM_xxx [READWRITERS])
[NSFItemAppend](/domino-c-api-docs/reference/Func/NSFItemAppend)
[TYPE_xxx](/domino-c-api-docs/reference/Symb/TYPE_xxx)
---
