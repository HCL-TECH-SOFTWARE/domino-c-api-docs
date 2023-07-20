##### Data Type : Item (Field) Information
##### ITEM_TABLE - Item summary structure.
---
```
#include <nsfdata.h>
```

**Definition :**
```
typedef struct {
   USHORT Length; /*  total length of this buffer */
   USHORT Items;  /* number of items in the table */
/* now come an array of ITEMs */
/* now comes the packed text containing the item names. */
} ITEM_TABLE;
```

**Description :**

This is the structure used for item (field) summary buffers.  If you specify the SEARCH_SUMMARY flag in NSFSearch, then your action routine receives a pointer to a summary buffer in the third (ITEM_TABLE far *summary_info)   parameter. You will also receive a pointer to a summary buffer if you specifiy READ_MASK_SUMMARY in NIFReadEntries. The information in this summary buffer consists of an ITEM_TABLE structure, followed by an array of ITEM structures, followed by a packed sequence of item names followed by a packed sequence of item values.  Each item value includes the item's datatype. The item's datatype is stored in the first USHORT of each item value.


**Sample Usage :**
```
STATUS PrintSummary (char *pSummary)
{
    char       *pSummaryPos;        /* current position in pSummary */
    ITEM_TABLE  ItemTable;          /* header at start of pSummary */
    USHORT      ItemCount;          /* number of items in pSummary */
    USHORT      i;                  /* counter for loop over items */

   /* pSummary points to a summary buffer that starts with an ITEM_TABLE.
      Initialize pSummaryPos to the position of the beginning of
      the summary buffer. Keep pSummary unmodified. Modify pSummaryPos.
    */

    pSummaryPos = pSummary;

   /* Copy the ITEM_TABLE header at the beginning of the summary buffer 
      to a local variable. Advance pSummaryPos to point to the next 
      byte in the summary buffer after the ITEM_TABLE.
    */
    memcpy ((char*)(&ItemTable), pSummaryPos, sizeof(ITEM_TABLE));
    pSummaryPos += sizeof(ItemTable);

   /* pSummaryPos now points to the first ITEM in an array of ITEM 
      structures. Copy this array of ITEM structures into the global 
      Items[] array.
    */

    ItemCount = ItemTable.Items;

    for (i=0; i < ItemCount; i++)
    {
        memcpy((char*)(&Items[i]), pSummaryPos, sizeof(ITEM));
        pSummaryPos += sizeof(ITEM);
    }
```

**See Also :**
[ITEM](/domino-c-api-docs/reference/Data/ITEM)
[NIFFindByKey](/domino-c-api-docs/reference/Func/NIFFindByKey)
[NIFReadEntries](/domino-c-api-docs/reference/Func/NIFReadEntries)
[NSFSearch](/domino-c-api-docs/reference/Func/NSFSearch)
[SEARCH_xxx](/domino-c-api-docs/reference/Symb/SEARCH_xxx)
---
