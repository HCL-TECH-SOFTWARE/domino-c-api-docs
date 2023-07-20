##### Data Type : Item (Field) Information
##### SEARCH_MATCH - Information about each note found by NSFSearch.
---
```
#include <nsfsearc.h>
```

**Definition :**
```
typedef struct {
   GLOBALINSTANCEID ID; /* identity of the note within the file */
   ORIGINATORID OriginatorID; /* identity of the note in the
                           universe */
   WORD NoteClass;      /* class of the note */
   BYTE SERetFlags;     /* match indicator */
   BYTE Privileges;     /* note privileges */
   WORD SummaryLength;  /* summary information length */
/* now comes an ITEM_TABLE with summary info... */
} SEARCH_MATCH;
```

**Description :**

NSFSearch fills this structure with information about each note that it finds, and passes it as input to the user-supplied action routine.<br>
<br>
The second parameter to the NSFSearch action routine is a pointer to this structure.<br>
<br>
Note 1: before accessing members of the SEARCH_MATCH data structure, your action routine should use memcpy to copy the structure from the address specified by the pointer to a variable of type SEARCH_MATCH. The reason is that Domino data resides in packed memory buffers. On non-Intel architecture platforms, the SEARCH_MATCH pointer provided by Domino may not be aligned properly for the SEARCH_MATCH data type. In this case, directly accessing the members of the SEARCH_MATCH structure via the pointer may cause a bus error trap.<br>
<br>
Note 2: your action routine should check that the SE_FMATCH bit is set in the &quot;SERetFlags&quot; member of the SEARCH_MATCH structure to ensure that the note is valid and really matches the search criteria. Non-matching notes (including deletion stubs) are passed to the action routine when using either a formula or a search by time/date (or both).  The SE_FTRUNCATED bit will be set if the document has been truncated.<br>
<br>
Note 3:  The use of the &quot;match&quot; bits has changed from Release 3 to Release 4 of Notes.  In Release 3, only the values SE_FNOMATCH or SE_FMATCH would be returned in the field &quot;MatchesFormula&quot;.  In Release 4, another bit has been defined, SE_FTRUNCATED.  Applications which have not been recompiled will continue to work as they have before;  documents that have been truncated will not match either SE_FNOMATCH or SE_FMATCH.  When applications are recompiled, the new field name must be used.  The application should now check for the SE_FMATCH bit.


**Sample Usage :**
```
STATUS LNPUBLIC ReadSummaryData
            (VOID far *optional_param,
            SEARCH_MATCH far *search_info,
            ITEM_TABLE far *summary_info)
{
    SEARCH_MATCH  SearchMatch;
    STATUS        error;

    memcpy ((char*)(&SearchMatch), (char *)search_info,
        sizeof(SEARCH_MATCH));

    if (!(SearchMatch.SERetFlags & SE_FMATCH))
        return (NOERROR);

    /* Print the note ID. */

    printf ("\nNote ID is: %#010lx.\n", SearchMatch.ID.NoteID);
```

**See Also :**
[NSFSearch](/domino-c-api-docs/reference/Func/NSFSearch)
[SEARCH_xxx](/domino-c-api-docs/reference/Symb/SEARCH_xxx)
---
