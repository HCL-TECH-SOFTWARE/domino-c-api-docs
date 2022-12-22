




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Courier;
 panose-1:2 7 4 9 2 2 5 2 4 4;}
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




**Initial Release 4.0**



**Data Type : Views**



**VIEW\_COLUMN\_FORMAT2** **-** Extended
View column format descriptor.


**----------------------------------------------------------------------------------------------------------**



**#include
<viewfmt.h>**



**Definition :**



typedef struct  

{  

   WORD   Signature;                  /\* VIEW\_COLUMN\_FORMAT\_SIGNATURE2 \*/  

   FONTID HeaderFontID;               /\* FontID of column header. \*/  

   UNID   ResortToViewUNID;           /\* UNID of view to switch to. \*/  

   WORD   wSecondResortColumnIndex;   /\* 0 based index of secondary resort
column. \*/  

   WORD   Flags3;                                         

   WORD   wHideWhenFormulaSize;  

   WORD   wTwistieResourceSize;  

   WORD   wCustomOrder;               /\* V6 View Customization support \*/  

   WORD   wCustomHiddenFlags;         /\* V6 View Customization support \*/


        COLOR\_VALUE    ColumnColor;       
/\* V6 - Column Text Color \*/


        COLOR\_VALUE
HeaderFontColor;       /\* V6 - column header color \*/  

} VIEW\_COLUMN\_FORMAT2;


 


**Description :**



This
structure describes the format of one column in a view as of Notes Release 4.
This structure is one of the components of a $VIEWFORMAT item in a view note. A
$VIEWFORMAT item contains one extended view column format descriptor per
column. Note: If you add variable data to this structure, store the packed,
variable data AFTER the array of structures.  All view notes contain a
$VIEWFORMAT item (also known as a "View Table Format" item).  A
$VIEWFORMAT item is an item of TYPE\_VIEW\_FORMAT with item name VIEW\_VIEW\_FORMAT\_ITEM.
The item value of a $VIEWFORMAT item consists of a single VIEW\_TABLE\_FORMAT
structure, followed by one VIEW\_COLUMN\_FORMAT structure for each column,
followed by an item name/formula/column title set for each column, followed by
a  VIEW\_TABLE\_FORMAT2 structure, followed by one VIEW\_COLUMN\_FORMAT2 structure
for each column, followed by a VIEW\_TABLE\_FORMAT3 structure.


 **See Also :**


**[VCF3\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/4A08216DABAD00BC852566780074867A)**


**[VIEW\_COLUMN\_FORMAT](VIEW_COLUMN_FORMAT.md)**


**[VIEW\_TABLE\_FORMAT](VIEW_TABLE_FORMAT.md)**


**[VIEW\_TABLE\_FORMAT2](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/004C005400E90078852564C3006285BD)**



----------------------------------------------------------------------------------------------------------


 





