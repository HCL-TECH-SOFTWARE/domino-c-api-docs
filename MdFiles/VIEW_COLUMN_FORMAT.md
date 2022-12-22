




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




 


**Data Type : Views**



**VIEW\_COLUMN\_FORMAT** **-** View column
format descriptor.


**----------------------------------------------------------------------------------------------------------**



**#include
<viewfmt.h>**



**Definition :**



typedef struct
tagVIEW\_COLUMN\_FORMAT {  

   WORD Signature;         /\* VIEW\_COLUMN\_FORMAT\_SIGNATURE \*/  

   WORD Flags1;            /\* see VCF1\_xxx \*/  

   WORD ItemNameSize;      /\* Item name string size \*/  

   WORD TitleSize;         /\* Title string size \*/  

   WORD FormulaSize;       /\* Compiled formula size \*/  

   WORD ConstantValueSize; /\* Constant value size \*/  

   WORD DisplayWidth;      /\* Display width - 1/8 ave. char   

                              width units \*/  

   FONTID FontID;          /\* Display font ID \*/  

   WORD Flags2;            /\* see VCF2\_xxx \*/  

   NFMT NumberFormat;      /\* Number format specification \*/  

   TFMT TimeFormat;        /\* Time format specification \*/  

   WORD FormatDataType;    /\* See VIEW\_COL\_xxx \*/  

   WORD ListSep;           /\* List Separator \*/  

} VIEW\_COLUMN\_FORMAT;


 


**Description :**




This
structure describes the format of one column in a view. This structure is one
of the components of a $VIEWFORMAT item in a view note. A $VIEWFORMAT item
contains one view column format descriptor per column.


 


All
view notes contain a $VIEWFORMAT item (also known as a "View Table
Format" item). A $VIEWFORMAT item is an item of TYPE\_VIEW\_FORMAT with item
name VIEW\_VIEW\_FORMAT\_ITEM. The item value of a $VIEWFORMAT item consists of a
single VIEW\_TABLE\_FORMAT structure, followed by one VIEW\_COLUMN\_FORMAT
structure for each column, followed by an  item name/formula/column title set
for each column, followed by a VIEW\_TABLE\_FORMAT2 structure, followed by one
VIEW\_COLUMN\_FORMAT2 structure for each column, followed by a VIEW\_TABLE\_FORMAT3
structure.


 **Sample Usage :**


VIEW\_COLUMN\_FORMAT
ViewColumnFormat;  

  

/\*  

 Create the VIEW\_COLUMN\_FORMAT item for column 1. Since this column  

 is neither a TIME field or a NUMBER field, we don't need to set the  

 TimeFormat or the NumberFormat fields.  

 \*/  

  

ViewColumnFormat.Signature = VIEW\_COLUMN\_FORMAT\_SIGNATURE;  

ViewColumnFormat.Flags1 = (VCF1\_M\_Sort | VCF1\_M\_SortCategorize);  

  

ViewColumnFormat.DisplayWidth = 8;  

ViewColumnFormat.FontID = DEFAULT\_BOLD\_FONT\_ID;  

ViewColumnFormat.Flags2 = 0;  

  

ViewColumnFormat.FormatDataType = VIEW\_COL\_TEXT;  

ViewColumnFormat.ListSep = LDDELIM\_COMMA;  

  

ViewColumnFormat.FormulaSize = wFormula\_1\_Len;  

ViewColumnFormat.ItemNameSize = wItemName\_1\_Len;  

ViewColumnFormat.TitleSize = 0;   /\* No column title for categories \*/  

ViewColumnFormat.ConstantValueSize = 0; /\* RESERVED \_ SHOULD BE 0 \*/  

  

/\*  

 Convert the View Column Format structure for Col 1 to Domino canonical  

 format and append it to the buffer. This increments pVFBuf to point  

 to the next byte in the buffer after the View Column Format.  

 \*/  

  

ODSWriteMemory( &pVFBuf, \_VIEW\_COLUMN\_FORMAT, &ViewColumnFormat, 1 );


 **See Also :**


**[VIEW\_COLUMN\_FORMAT2](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/868D1214A6E2E199852561C000516B12)**


**[VIEW\_TABLE\_FORMAT](VIEW_TABLE_FORMAT.md)**


**[VIEW\_TABLE\_FORMAT2](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/004C005400E90078852564C3006285BD)**



----------------------------------------------------------------------------------------------------------


 





