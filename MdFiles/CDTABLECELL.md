




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



**CDTABLECELL** **-** Specifies
the cell of a table.


**----------------------------------------------------------------------------------------------------------**



**#include
<editods.h>**



**Definition :**



typedef struct {  

   BSIG Header;  

   BYTE Row;             /\* Row number (0 based) \*/  

   BYTE Column;          /\* Column number (0 based) \*/  

   WORD LeftMargin;      /\* Twips \*/  

   WORD RightMargin;     /\* Twips \*/  

   WORD FractionalWidth; /\* 20" (in twips) \* CellWidth / TableWidth  

                            Used only if AutoCellWidth is  

                            specified in the TABLEBEGIN. \*/  

   BYTE Border;          /\* 4 cell borders, each 2 bits wide  

                            (see shift and mask CDTC\_xxx values)  

                            Value of each cell border is one of  

                            TABLE\_BORDER\_xxx. \*/  

   BYTE Flags;           /\* see CDTABLECELL\_xxx \*/  

   WORD v42Border;       /\* wider borders, see CDTC\_xxx\_V42\_xxx \*/  

   BYTE RowSpan;  

   BYTE ColumnSpan;  

   WORD BackgroundColor; /\* Color of background of cell \*/  

} CDTABLECELL;


 


**Description :**



This
structure specifies the cell of a table.  Use this structure when accessing a
table in a rich text field.


 


If the
CDTABLECELL\_USE\_V42BORDERS is set in the Flags member of this structure, then
the table was created with Domino or Notes Release 4.5 or later and contains
border width information that is not available in previous releases of Notes. 
In this case, the Border member should contain the equivalent of the v42Border
member value, so that the table can be read by earlier releases of Notes.    For
example, a v42Border value which translates to a bottom cell border width of 4,
a top cell border width of 0,  a right cell border width of 1 and a left cell
border width of 10, will map to a Border value that translates to a bottom cell
border of TABLE\_BORDER\_DOUBLE, a top cell border width of TABLE\_BORDER\_NONE, a
right cell border width of TABLE\_BORDER\_SINGLE, and a left cell border width of
TABLE\_BORDER\_DOUBLE.  See the CDTC\_xxx and CDTC\_xxx\_V42\_xxx entries for
details.


 


The RowSpan
member and the ColumnSpan member of this structure are used to merge or span a
group of contiguous cells into one cell.  If the cell is not involved in a
merger, each of these structure members should be set to 1.


 


In order to
specify a group of spanned cells, you specify the RowSpan and ColumnSpan
members of this structure for the most bottom-right cell in the group.  This is
the cell that is doing the spanning.  RowSpan specifies the number of rows
spanned by the cell; use 1 for the cell itself and add 1 for every cell above
it.  ColumnSpan specifies the number of columns spanned by the cell; use 1 for
the cell itself and add 1 for every cell to the left of it.  For all other
cells in this group, specify 1 for RowSpan and 1 for ColumnSpan.  Also, for all
cells that are not in the same row as the cell doing the spanning, specify
CDTABLECELL\_INVISIBLEV for the Flags member of this structure.  Specify
CDTABLECELL\_INVISIBLEH for the Flags member of this structure for those cells
in the group that are in the same row as the cell doing the spanning.  These
flags indicate that these cells are invisible.  Do not set the Flags member to
CDTABLECELL\_INVISIBLEH or to CDTABLECELL\_INVISIBLEV for the cell that is doing
the spanning.  The cell that is doing the spanning will have a RowSpan and/or a
ColumnSpan that is greater than one and will be the size of all the cells it
spans.


 


For example,



CDTABLECELL
cell1\_1,cell2\_1,cell3\_1, cell4\_1;


For the
following table:  




|  |  |  |
| --- | --- | --- |
|   |   |   |
|   |   |
|   |   |
|   |   |


 


Use:




|  |  |  |
| --- | --- | --- |
| cell1\_1.Flag
 |= INVISIBLEV
cell1\_1.RowSpan
 = 1
cell1\_1.ColumnSpan
 = 1 |   |   |
| cell2\_1.Flag
 |= INVISIBLEV
cell2\_1.RowSpan
 = 1
cell2\_1.ColumnSpan
 = 1 |   |   |
| cell3\_1.Flag
 |= INVISIBLEV
cell3\_1.RowSpan
 = 1
cell3\_1.ColumnSpan
 = 1 |   |   |
| cell4\_1.RowSpan
 = 4
cell4\_1.ColumnSpan
 = 1 |   |   |


 


CDTABLECELL
cell1\_1,cell2\_1,cell3\_1, cell2\_1, cell2\_2, cell3\_1, cell3\_2;


For the
following table:    

  






|  |  |
| --- | --- |
|   |   |
|   |
|   |
|   |   |   |
|  |  |  |


 


Use:




|  |  |  |
| --- | --- | --- |
| cell1\_1.Flag
 |= INVISIBLEV
cell1\_1.RowSpan
 = 1
cell1\_1.ColumnSpan
 = 1 | cell1\_2.Flag
 |= INVISIBLEV
cell1\_2.RowSpan
 = 1
cell1\_2.ColumnSpan
 = 1 |   |
| cell2\_1.Flag
 |= INVISIBLEV
cell2\_1.RowSpan
 =1
cell2\_1.ColumnSpan
 = 1 | cell2\_2.Flag
 |= INVISIBLEV
cell2\_2.RowSpan
 =1
cell2\_2.ColumnSpan
 = 1 |   |
| cell3\_1.Flag
 |= INVISIBLEH
cell3\_1.RowSpan
 = 1
cell3\_1.ColumnSpan
 = 1 | cell3\_2.RowSpan
 = 3
cell3\_2ColumnSpan
 = 2 |   |
|   |   |   |


 


  

Note that rich text fields are items of type TYPE\_COMPOSITE. Therefore, API
programs that run on non-Intel architecture platforms must perform
host/canonical conversion on CD record structures such as this when accessing
rich text item data in a note.


 **See Also :**


**[CDTABLEBEGIN](CDTABLEBEGIN.md)**


**[CDTABLECELL\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/62D1E80D356CC0B185256678004774FD)**


**[CDTABLEEND](CDTABLEEND.md)**


**[CDTC\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/B0B71D94A0C05DF1852561EA0050869E)**


**[CDTC\_xxx\_V42\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/817BB905822C66158525635E0072DF70)**


**[SIG\_CD\_xxx](SIG_CD_xxx.md)**


**[TABLE\_BORDER\_xxx](TABLE_BORDER_xxx.md)**



----------------------------------------------------------------------------------------------------------


 





