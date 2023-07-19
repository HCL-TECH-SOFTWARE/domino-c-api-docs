##### Symbolic Value : Item (Field) Information
##### ITEM_xxx [READWRITERS] - Item Data Type - Author Names
---
```
#include <nsfnote.h>
```

**Symbolic Values :**



**Description :**

Author Names fields have external (field definition) data type &quot;Author Names&quot;.  Domino grants author access to any entity named in an Author Names field.<br>
<br>
At the API level, an Author Names field is an item of TYPE_TEXT or TYPE_TEXT_LIST with both the NAMES flag set and the READ/WRITE-ACCESS flag set.  The NAMES flag corresponds to the ITEM_NAMES bit in the item flags.  The READ/WRITE-ACCESS flag corresponds to the ITEM_READWRITERS bit in the item flags.<br>
<br>
Since the API function NSFItemSetText does not set the ITEM_READWRITERS flag, use NSFItemAppend to append Author Names fields to documents.


**Sample Usage :**
```
STATUS  LNPUBLIC  AppendEditorsItem (NOTEHANDLE  hNote)
{
    STATUS      error = NOERROR;
    DWORD       dwValueLen;
    void far   *pvoidItemValue;
    LIST       *pList;
    USHORT     *pusLength;
    USHORT      usLen1, usLen2;
    char       *pchStr;

#define EDITORS1        "NADC Executives"
#define EDITORS2        "NADC Marketing"
#define EDITORS_COUNT   2

    usLen1 = strlen(EDITORS1);
    usLen2 = strlen(EDITORS2);

    dwValueLen = sizeof(LIST) + (EDITORS_COUNT * sizeof(USHORT)) +
                 usLen1 + usLen2 ;

    pvoidItemValue = (void far *) malloc ((size_t)dwValueLen);

    pList = (LIST*)pvoidItemValue;
    pList->ListEntries = EDITORS_COUNT;
    pList++;
    pusLength = (USHORT*)pList;
    *pusLength = usLen1;
    pusLength++;
    *pusLength = usLen2;
    pusLength++;
    pchStr = (char*)pusLength;
    memcpy (pchStr, EDITORS1, usLen1);
    pchStr += usLen1;
    memcpy (pchStr, EDITORS2, usLen2);

    if (error = NSFItemAppend ( hNote, 
                                ITEM_SUMMARY | ITEM_READWRITERS | ITEM_NAMES,
                                DISCUSS_ITEM_EDITORS,  /* "Editors" */
                                strlen(DISCUSS_ITEM_EDITORS),
                                TYPE_TEXT_LIST,
                                pvoidItemValue,
                                dwValueLen))
    {
        printf ("Error: unable to append Editors field.\n");
    }
    free (pvoidItemValue);
    return (error);
}
```

**See Also :**
[ITEM_xxx](/domino-c-api-docs/reference/Symb/ITEM_xxx)
[ITEM_xxx [NAMES]](/domino-c-api-docs/reference/Symb/ITEM_xxx [NAMES])
[ITEM_xxx [READERS]](/domino-c-api-docs/reference/Symb/ITEM_xxx [READERS])
---
