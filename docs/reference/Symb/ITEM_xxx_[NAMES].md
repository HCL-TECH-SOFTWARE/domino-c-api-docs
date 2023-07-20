##### Symbolic Value : Item (Field) Information
##### ITEM_xxx [NAMES] - Item Data Type - Names
---
```
#include <nsfnote.h>
```

**Symbolic Values :**



**Description :**

Use Names fields to store distinguished (hierarchical) names.  Domino application developers specify data type Names in the field definition of fields that will store one or several distinguished names. The Names data type causes the Notes workstation to display the fields in abbreviated format.<br>
<br>
Internally (at the API level) Names fields are stored as items of TYPE_TEXT or TYPE_TEXT_LIST marked with the distinguished names flag, ITEM_NAMES. <br>
<br>
Since the API function NSFItemSetText does not set the ITEM_NAMES flag, use NSFItemAppend to append Names fields to documents.


**Sample Usage :**
```
STATUS LNPUBLIC AppendUpdatedByItem (NOTEHANDLE hNote, char * szAuthor)
{
    STATUS  error;

    if (error = NSFItemAppend ( hNote, 
                                ITEM_SUMMARY | ITEM_NAMES,
                                DISCUSS_ITEM_$UPDATEDBY,  /* "$UpdatedBy" */
                                strlen(DISCUSS_ITEM_$UPDATEDBY),
                                TYPE_TEXT,
                                szAuthor,
                                strlen(szAuthor)))
    {
        printf ("Error: unable to append $UpdatedBy field.\n");
    }
    return (error);
}
```

**See Also :**
[ITEM_xxx](/domino-c-api-docs/reference/Symb/ITEM_xxx)
[ITEM_xxx [READERS]](/domino-c-api-docs/reference/Symb/ITEM_xxx [READERS])
[ITEM_xxx [READWRITERS]](/domino-c-api-docs/reference/Symb/ITEM_xxx [READWRITERS])
---
