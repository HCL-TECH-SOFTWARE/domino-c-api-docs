##### Data Type : Composite Data
##### CDTABLECELL - Specifies the cell of a table.
---
```
#include <editods.h>
```

**Definition :**

typedef struct {
   BSIG Header;
   BYTE Row;             /* Row number (0 based) */
   BYTE Column;          /* Column number (0 based) */
   WORD LeftMargin;      /* Twips */
   WORD RightMargin;     /* Twips */
   WORD FractionalWidth; /* 20" (in twips) * CellWidth / TableWidth
                            Used only if AutoCellWidth is
                            specified in the TABLEBEGIN. */
   BYTE Border;          /* 4 cell borders, each 2 bits wide
                            (see shift and mask CDTC_xxx values)
                            Value of each cell border is one of
                            TABLE_BORDER_xxx. */
   BYTE Flags;           /* see CDTABLECELL_xxx */
   WORD v42Border;       /* wider borders, see CDTC_xxx_V42_xxx */
   BYTE RowSpan;
   BYTE ColumnSpan;
   WORD BackgroundColor; /* Color of background of cell */
} CDTABLECELL;

**Description :**

This structure specifies the cell of a table.  Use this structure when accessing a table in a rich text field.
<ul><br>
<br>
If the CDTABLECELL_USE_V42BORDERS is set in the Flags member of this structure, then the table was created with Domino or Notes Release 4.5 or later and contains border width information that is not available in previous releases of Notes.  In this case, the Border member should contain the equivalent of the v42Border member value, so that the table can be read by earlier releases of Notes.    For example, a v42Border value which translates to a bottom cell border width of 4, a top cell border width of 0,  a right cell border width of 1 and a left cell border width of 10, will map to a Border value that translates to a bottom cell border of TABLE_BORDER_DOUBLE, a top cell border width of TABLE_BORDER_NONE, a right cell border width of TABLE_BORDER_SINGLE, and a left cell border width of TABLE_BORDER_DOUBLE.  See the CDTC_xxx and CDTC_xxx_V42_xxx entries for details.<br>
<br>
The RowSpan member and the ColumnSpan member of this structure are used to merge or span a group of contiguous cells into one cell.  If the cell is not involved in a merger, each of these structure members should be set to 1.<br>
<br>
In order to specify a group of spanned cells, you specify the RowSpan and ColumnSpan members of this structure for the most bottom-right cell in the group.  This is the cell that is doing the spanning.  RowSpan specifies the number of rows spanned by the cell; use 1 for the cell itself and add 1 for every cell above it.  ColumnSpan specifies the number of columns spanned by the cell; use 1 for the cell itself and add 1 for every cell to the left of it.  For all other cells in this group, specify 1 for RowSpan and 1 for ColumnSpan.  Also, for all cells that are not in the same row as the cell doing the spanning, specify CDTABLECELL_INVISIBLEV for the Flags member of this structure.  Specify CDTABLECELL_INVISIBLEH for the Flags member of this structure for those cells in the group that are in the same row as the cell doing the spanning.  These flags indicate that these cells are invisible.  Do not set the Flags member to CDTABLECELL_INVISIBLEH or to CDTABLECELL_INVISIBLEV for the cell that is doing the spanning.  The cell that is doing the spanning will have a RowSpan and/or a ColumnSpan that is greater than one and will be the size of all the cells it spans.<br>
<br>
For example, <br>
CDTABLECELL cell1_1,cell2_1,cell3_1, cell4_1;<br>
For the following table:  
<table width="100%" border="1">
<tr valign="top"><td width="43%" rowspan="4"><img width="1" height="1" src="/icons/ecblank.gif" border="0" alt=""></td><td width="43%"><img width="1" height="1" src="/icons/ecblank.gif" border="0" alt=""></td><td width="13%"><img width="1" height="1" src="/icons/ecblank.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="43%"><img width="1" height="1" src="/icons/ecblank.gif" border="0" alt=""></td><td width="13%"><img width="1" height="1" src="/icons/ecblank.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="43%"><img width="1" height="1" src="/icons/ecblank.gif" border="0" alt=""></td><td width="13%"><img width="1" height="1" src="/icons/ecblank.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="43%"><img width="1" height="1" src="/icons/ecblank.gif" border="0" alt=""></td><td width="13%"><img width="1" height="1" src="/icons/ecblank.gif" border="0" alt=""></td></tr>
</table>
Use:
<table width="100%" border="1">
<tr valign="top"><td width="33%">cell1_1.Flag |= INVISIBLEV<br>
cell1_1.RowSpan = 1<br>
cell1_1.ColumnSpan = 1</td><td width="33%"><img width="1" height="1" src="/icons/ecblank.gif" border="0" alt=""></td><td width="33%"><img width="1" height="1" src="/icons/ecblank.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="33%">cell2_1.Flag |= INVISIBLEV<br>
cell2_1.RowSpan = 1<br>
cell2_1.ColumnSpan = 1</td><td width="33%"><img width="1" height="1" src="/icons/ecblank.gif" border="0" alt=""></td><td width="33%"><img width="1" height="1" src="/icons/ecblank.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="33%">cell3_1.Flag |= INVISIBLEV<br>
cell3_1.RowSpan = 1<br>
cell3_1.ColumnSpan = 1</td><td width="33%"><img width="1" height="1" src="/icons/ecblank.gif" border="0" alt=""></td><td width="33%"><img width="1" height="1" src="/icons/ecblank.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="33%">cell4_1.RowSpan = 4<br>
cell4_1.ColumnSpan = 1</td><td width="33%"><img width="1" height="1" src="/icons/ecblank.gif" border="0" alt=""></td><td width="33%"><img width="1" height="1" src="/icons/ecblank.gif" border="0" alt=""></td></tr>
</table>
CDTABLECELL cell1_1,cell2_1,cell3_1, cell2_1, cell2_2, cell3_1, cell3_2;<br>
For the following table:  <br>

<table width="100%" border="1">
<tr valign="top"><td width="67%" rowspan="3" colspan="2"><img width="1" height="1" src="/icons/ecblank.gif" border="0" alt=""></td><td width="33%"><img width="1" height="1" src="/icons/ecblank.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="33%"><img width="1" height="1" src="/icons/ecblank.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="33%"><img width="1" height="1" src="/icons/ecblank.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="33%"><img width="1" height="1" src="/icons/ecblank.gif" border="0" alt=""></td><td width="33%"><img width="1" height="1" src="/icons/ecblank.gif" border="0" alt=""></td><td width="33%"><img width="1" height="1" src="/icons/ecblank.gif" border="0" alt=""></td></tr>
</table>
</ul>
Use:
<table width="100%" border="1">
<tr valign="top"><td width="33%">cell1_1.Flag |= INVISIBLEV<br>
cell1_1.RowSpan = 1<br>
cell1_1.ColumnSpan = 1</td><td width="33%">cell1_2.Flag |= INVISIBLEV<br>
cell1_2.RowSpan = 1<br>
cell1_2.ColumnSpan = 1</td><td width="33%"><img width="1" height="1" src="/icons/ecblank.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="33%">cell2_1.Flag |= INVISIBLEV<br>
cell2_1.RowSpan =1<br>
cell2_1.ColumnSpan = 1</td><td width="33%">cell2_2.Flag |= INVISIBLEV<br>
cell2_2.RowSpan =1<br>
cell2_2.ColumnSpan = 1</td><td width="33%"><img width="1" height="1" src="/icons/ecblank.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="33%">cell3_1.Flag |= INVISIBLEH<br>
cell3_1.RowSpan = 1<br>
cell3_1.ColumnSpan = 1</td><td width="33%">cell3_2.RowSpan = 3<br>
cell3_2ColumnSpan = 2</td><td width="33%"><img width="1" height="1" src="/icons/ecblank.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="33%"><img width="1" height="1" src="/icons/ecblank.gif" border="0" alt=""></td><td width="33%"><img width="1" height="1" src="/icons/ecblank.gif" border="0" alt=""></td><td width="33%"><img width="1" height="1" src="/icons/ecblank.gif" border="0" alt=""></td></tr>
</table>

<ul><br>
Note that rich text fields are items of type TYPE_COMPOSITE. Therefore, API programs that run on non-Intel architecture platforms must perform host/canonical conversion on CD record structures such as this when accessing rich text item data in a note.</ul>



**See Also :**
[CDTABLEBEGIN](/domino-c-api-docs/reference/Data/CDTABLEBEGIN)
[CDTABLECELL_xxx](/domino-c-api-docs/reference/Symb/CDTABLECELL_xxx)
[CDTABLEEND](/domino-c-api-docs/reference/Data/CDTABLEEND)
[CDTC_xxx](/domino-c-api-docs/reference/Symb/CDTC_xxx)
[CDTC_xxx_V42_xxx](/domino-c-api-docs/reference/Symb/CDTC_xxx_V42_xxx)
[SIG_CD_xxx](/domino-c-api-docs/reference/Symb/SIG_CD_xxx)
[TABLE_BORDER_xxx](/domino-c-api-docs/reference/Symb/TABLE_BORDER_xxx)
---
