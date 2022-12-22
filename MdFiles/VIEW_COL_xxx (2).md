




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




**Initial Release 5.0**



**Symbolic Value : Views**



**VIEW\_COL\_xxx (2)** **-** View column
display reading order and header reading order.


**----------------------------------------------------------------------------------------------------------**



**#include <viewfmt.h>**


 **Symbolic Values :**      VIEW\_COL\_LTR       -  Left to Right reading order  

  

      VIEW\_COL\_RTL       -  Right to left reading order  

  




**Description :**



View column
display reading order and header reading order.


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


  
ViewColumnFormat.Flags2 = VIEW\_COL\_ALIGN\_RIGHT << VCF2\_S\_HeaderAlignment
| VCF2\_M\_DisplayAlignment & VIEW\_COL\_ALIGN\_RIGHT| VIEW\_COL\_RTL <<
VCF2\_S\_DisplayReadingOrder | VIEW\_COL\_RTL << VCF2\_S\_HeaderReadingOrder;


  

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


**[VCF2\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/C5237445E8E3F894852564C3006F7A60)**


**[VIEW\_COLUMN\_FORMAT](VIEW_COLUMN_FORMAT.md)**



----------------------------------------------------------------------------------------------------------


 





