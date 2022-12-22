




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



**ITEM\_TABLE** **-** Item summary
structure.


**----------------------------------------------------------------------------------------------------------**



**#include
<nsfdata.h>**



**Definition :**



typedef struct {  

   USHORT Length; /\*  total length of this buffer \*/  

   USHORT Items;  /\* number of items in the table \*/  

/\* now come an array of ITEMs \*/  

/\* now comes the packed text containing the item names. \*/  

} ITEM\_TABLE;


 


**Description :**



This is the
structure used for item (field) summary buffers.  If you specify the
SEARCH\_SUMMARY flag in NSFSearch, then your action routine receives a pointer
to a summary buffer in the third (ITEM\_TABLE far \*summary\_info)   parameter.
You will also receive a pointer to a summary buffer if you specifiy
READ\_MASK\_SUMMARY in NIFReadEntries. The information in this summary buffer
consists of an ITEM\_TABLE structure, followed by an array of ITEM structures,
followed by a packed sequence of item names followed by a packed sequence of
item values.  Each item value includes the item's datatype. The item's datatype
is stored in the first USHORT of each item value.


 **Sample Usage :**


STATUS PrintSummary
(char \*pSummary)  

{  

    char       \*pSummaryPos;        /\* current position in pSummary \*/  

    ITEM\_TABLE  ItemTable;          /\* header at start of pSummary \*/  

    USHORT      ItemCount;          /\* number of items in pSummary \*/  

    USHORT      i;                  /\* counter for loop over items \*/  

  

   /\* pSummary points to a summary buffer that starts with an ITEM\_TABLE.  

      Initialize pSummaryPos to the position of the beginning of  

      the summary buffer. Keep pSummary unmodified. Modify pSummaryPos.  

    \*/  

  

    pSummaryPos = pSummary;  

  

   /\* Copy the ITEM\_TABLE header at the beginning of the summary buffer   

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


 **See Also :**


**[ITEM](ITEM.md)**


**[NIFFindByKey](NIFFindByKey.md)**


**[NIFReadEntries](NIFReadEntries.md)**


**[NSFSearch](NSFSearch.md)**


**[SEARCH\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/85255D56004D3F6385255B4B004EBF15)**



----------------------------------------------------------------------------------------------------------


 





