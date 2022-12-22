




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




 


**Data Type : Composite Data; Rich
Text**



**CDTABLEBEGIN** **-** Specifies
the beginning of a table.


**----------------------------------------------------------------------------------------------------------**



**#include
<editods.h>**



**Definition :**



typedef struct {  

   BSIG Header;  

   WORD LeftMargin;            /\* TWIPS \*/  

   WORD HorizInterCellSpace;   /\* TWIPS \*/  

   WORD VertInterCellSpace;    /\* TWIPS \*/  

   WORD V4HorizInterCellSpace; /\* TWIPS -- field was spare in V3 \*/  

   WORD V4VertInterCellSpace;  /\* TWIPS -- field was spare in V3 \*/  

   WORD Flags;                 /\* Flags (CDTABLE\_xxx) \*/  

} CDTABLEBEGIN;


 


**Description :**



This
structure specifies the beginning of a table.  It contains information about
the format and size of the table.    Use this structure when accessing a table
in a rich text field.  As of R5, this structure is preceded by a CDPRETABLEBEGIN
structure.  The CDPRETABLEBEGIN structure specifies additional table
properties.  

  

Note that rich text fields are items of type TYPE\_COMPOSITE. Therefore, API
programs that run on non-Intel architecture platforms must perform
host/canonical conversion on CD record structures such as this when accessing
rich text item data in a note.


 **See Also :**


**[CDTABLEEND](CDTABLEEND.md)**


**[CDTABLECELL](CDTABLECELL.md)**


**[CDTABLE\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/493D6766D913CEA28525667800467FEB)**


**[CDPRETABLEBEGIN](CDPRETABLEBEGIN.md)**



----------------------------------------------------------------------------------------------------------


 





