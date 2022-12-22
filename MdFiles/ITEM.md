




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Courier;
 panose-1:2 7 4 9 2 2 5 2 4 4;}
@font-face
 {font-family:"Tms Rmn";
 panose-1:2 2 6 3 4 5 5 2 3 4;}
@font-face
 {font-family:Helv;
 panose-1:2 11 6 4 2 2 2 3 2 4;}
@font-face
 {font-family:"Cambria Math";
 panose-1:2 4 5 3 5 4 6 3 2 4;}
 /\* Style Definitions \*/
 p.MsoNormal, li.MsoNormal, div.MsoNormal
 {margin-top:0cm;
 margin-right:0cm;
 margin-bottom:8.0pt;
 margin-left:0cm;
 line-height:107%;
 font-size:11.0pt;
 font-family:"Calibri",sans-serif;}
.MsoChpDefault
 {font-size:11.0pt;}
.MsoPapDefault
 {margin-bottom:8.0pt;
 line-height:107%;}
 /\* Page Definitions \*/
 @page WordSection1
 {size:612.0pt 792.0pt;
 margin:72.0pt 72.0pt 72.0pt 72.0pt;}
div.WordSection1
 {page:WordSection1;}
-->




 


**Data Type : Item (Field) Information**



**ITEM** **-** Item (Field)
structure.


**----------------------------------------------------------------------------------------------------------**



**#include
<nsfdata.h>**



**Definition :**



typedef struct {  

   USHORT NameLength;  /\* Length of Item Name following this struct.\*/  

                       /\* may be zero (0) if not required by func(s)\*/  

                       /\* manipulating this ITEM.                   \*/  

   USHORT ValueLength; /\* Length of Item Value following this   \*/  

                       /\* struct, incl. Notes data type.        \*/  

} ITEM;


 


**Description :**



Used to
define the length of an item name and the length of an item value when this
data resides in a summary buffer.


 **Sample Usage :**


  

char       \*pSummaryPos;        /\* current position in summary \*/  

ITEM\_TABLE  ItemTable;          /\* header at start of summary \*/  

USHORT      ItemCount;          /\* number of items in summary \*/  

USHORT      NameLength;         /\* length of item name w/out terminator\*/  

USHORT      ValueLength;        /\* length of item value, incl. type \*/  

WORD        DataType;           /\* item data type word \*/  

char       \*szDataType;         /\* printable data type name \*/  

USHORT      TextLen;            /\* length of printable item text \*/  

USHORT      i;                  /\* counter for loop over items \*/  

ITEM    Items[MAX\_ITEMS];       /\* Stores the array of ITEMs \*/  

char    ItemText[MAX\_ITEM\_LEN]; /\* Text rendering of item value \*/  

char    ItemName[MAX\_ITEM\_NAME\_LEN];/\* Zero terminated item name \*/  

  

/\* pSummaryPos points to the beginning of the summary buffer. Copy   

  the ITEM\_TABLE header at the beginning of the summary buffer   

  to a local variable. Advance pSummaryPos to point to the next   

  byte in the summary buffer after the ITEM\_TABLE.  

\*/  

memcpy ((char\*)(&ItemTable), pSummaryPos, sizeof(ITEM\_TABLE));  

pSummaryPos += sizeof(ItemTable);  

  

/\* pSummaryPos now points to the first ITEM in an array of ITEM   

  structures. Copy this array of ITEM structures into the global   

  Items[] array.  

\*/  

  

ItemCount = ItemTable.Items;  

for (i=0; i < ItemCount; i++)  

{  

    memcpy((char\*)(&Items[i]), pSummaryPos, sizeof(ITEM));  

    pSummaryPos += sizeof(ITEM);  

}  

  

/\* pSummaryPos now points to the first item name. Loop over each  

  item, copying the item name into the ItemName variable and   

  converting the item value to printable text in ItemText.  

\*/  

  

for (i=0; i < ItemCount; i++)  

{  

    NameLength = Items[i].NameLength;   

    memcpy (ItemName, pSummaryPos, NameLength);  

    ItemName[NameLength] = '\0';  

    pSummaryPos += NameLength;  

  

 /\* pSummaryPos now points to the item value. First get the  

    data type. Then step over the data type word to the data   

    value and convert the value to printable text. Store the   

    text in ItemText.  

  \*/  

  

    memcpy ((char\*)(&DataType), pSummaryPos, sizeof(WORD));  

    pSummaryPos += sizeof(WORD);  

  

    ValueLength = Items[i].ValueLength - sizeof(WORD);  

  

 /\* If the item data type is text, copy into ItemText[]. \*/         

  

    if (DataType == TYPE\_TEXT)  

    {  

        memcpy (ItemText, pSummaryPos, ValueLength);  

        ItemText[ValueLength] = '\0';  

        pSummaryPos += ValueLength;  

    }


 **See Also :**


**[ITEM\_TABLE](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/85255D56004D3F6385255B43006B5125)**


**[NSFSearch](NSFSearch.md)**


**[NSFItemScan](NSFItemScan.md)**


**[NIFReadEntries](NIFReadEntries.md)**



----------------------------------------------------------------------------------------------------------


 





