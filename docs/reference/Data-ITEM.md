##### Data Type : Item (Field) Information
##### ITEM - Item (Field) structure.
---
##### #include <nsfdata.h>
**Description :**
Used to define the length of an item name and the length of an item value when 
this data resides in a summary buffer.
**Sample Usage :**
```

char       *pSummaryPos;        /* current position in summary */
ITEM_TABLE  ItemTable;          /* header at start of summary */
USHORT      ItemCount;          /* number of items in summary */
USHORT      NameLength;         /* length of item name w/out terminator*/
USHORT      ValueLength;        /* length of item value, incl. type */
WORD        DataType;           /* item data type word */
char       *szDataType;         /* printable data type name */
USHORT      TextLen;            /* length of printable item text */
USHORT      i;                  /* counter for loop over items */
ITEM    Items[MAX_ITEMS];       /* Stores the array of ITEMs */
char    ItemText[MAX_ITEM_LEN]; /* Text rendering of item value */
char    ItemName[MAX_ITEM_NAME_LEN];/* Zero terminated item name */

/* pSummaryPos points to the beginning of the summary buffer. Copy 
  the ITEM_TABLE header at the beginning of the summary buffer 
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

/* pSummaryPos now points to the first item name. Loop over each
  item, copying the item name into the ItemName variable and 
  converting the item value to printable text in ItemText.
*/

for (i=0; i < ItemCount; i++)
{
    NameLength = Items[i].NameLength; 
    memcpy (ItemName, pSummaryPos, NameLength);
    ItemName[NameLength] = '\0';
    pSummaryPos += NameLength;

 /* pSummaryPos now points to the item value. First get the
    data type. Then step over the data type word to the data 
    value and convert the value to printable text. Store the 
    text in ItemText.
  */

    memcpy ((char*)(&DataType), pSummaryPos, sizeof(WORD));
    pSummaryPos += sizeof(WORD);

    ValueLength = Items[i].ValueLength - sizeof(WORD);

 /* If the item data type is text, copy into ItemText[]. */       

    if (DataType == TYPE_TEXT)
    {
        memcpy (ItemText, pSummaryPos, ValueLength);
        ItemText[ValueLength] = '\0';
        pSummaryPos += ValueLength;
    }
```
**See Also :**
[ITEM_TABLE](D:/md_files/ITEM_TABLE.md)
[NSFSearch](D:/md_files/NSFSearch.md)
[NSFItemScan](D:/md_files/NSFItemScan.md)
[NIFReadEntries](D:/md_files/NIFReadEntries.md)
---
