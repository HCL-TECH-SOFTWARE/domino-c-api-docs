##### Symbolic Value : Item (Field) Information
##### ITEM_xxx [READERS] - Item Data Type - Reader Names
---
```
#include <nsfnote.h>
```
**Description :**

Reader Names fields have external data type "Reader Names".  Domino grants 
reader access to any entity named in a Reader Names field.

At the API level, a Reader Names field is an item of TYPE_TEXT or 
TYPE_TEXT_LIST with both the NAMES flag set and the READ-ACCESS flag set.  The 
NAMES flag corresponds to the ITEM_NAMES bit in the item flags.  The 
READ-ACCESS flag corresponds to the ITEM_READERS bit in the item flags.

Since the API function NSFItemSetText does not set the ITEM_READERS flag, use 
NSFItemAppend to append Reader Names fields to documents.

**Sample Usage :**
```
STATUS  LNPUBLIC  AppendReadersItem (NOTEHANDLE  hNote)
{
    STATUS      error = NOERROR;
    DWORD       dwValueLen;
    void far   *pvoidItemValue;
    LIST       *pList;
    USHORT     *pusLength;
    USHORT      usLen1, usLen2;
    char       *pchStr;

    usLen1 = strlen(READERS1);
    usLen2 = strlen(READERS2);

    dwValueLen = sizeof(LIST) + (READERS_COUNT * sizeof(USHORT)) +
                 usLen1 + usLen2 ;

    pvoidItemValue = (void far *) malloc ((size_t)dwValueLen);
    if (pvoidItemValue == NULL)
    {
        printf ("Error: unable to allocate %lu bytes memory.\n", dwValueLen);
        return(ERR_V3AUTHOR_MALLOC);
    }

    pList = (LIST*)pvoidItemValue;
    pList->ListEntries = READERS_COUNT;
    pList++;
    pusLength = (USHORT*)pList;
    *pusLength = usLen1;
    pusLength++;
    *pusLength = usLen2;
    pusLength++;
    pchStr = (char*)pusLength;
    memcpy (pchStr, READERS1, usLen1);
    pchStr += usLen1;
    memcpy (pchStr, READERS2, usLen2);

    if (error = NSFItemAppend ( hNote, 
                                ITEM_SUMMARY | ITEM_READERS | ITEM_NAMES,
                                DISCUSS_ITEM_READERS,  /* "Readers" */
                                strlen(DISCUSS_ITEM_READERS),
                                TYPE_TEXT_LIST,
                                pvoidItemValue,
                                dwValueLen))
    {
        printf ("Error: unable to append Readers field.\n");
    }
    free (pvoidItemValue);
    return (error);
}
```
**See Also :**
[ITEM_xxx](/reference/Symb/ITEM_xxx)
[ITEM_xxx [NAMES]](/reference/Symb/ITEM_xxx [NAMES])
[ITEM_xxx [READWRITERS]](/reference/Symb/ITEM_xxx [READWRITERS])
---
