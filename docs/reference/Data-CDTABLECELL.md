##### Data Type : Composite Data
##### CDTABLECELL - Specifies the cell of a table.
---
##### #include <editods.h>
**Description :**
This structure specifies the cell of a table.  Use this structure when 
accessing a table in a rich text field.

If the CDTABLECELL_USE_V42BORDERS is set in the Flags member of this structure, 
then the table was created with Domino or Notes Release 4.5 or later and 
contains border width information that is not available in previous releases of 
Notes.  In this case, the Border member should contain the equivalent of the 
v42Border member value, so that the table can be read by earlier releases of 
Notes.    For example, a v42Border value which translates to a bottom cell 
border width of 4, a top cell border width of 0,  a right cell border width of 
1 and a left cell border width of 10, will map to a Border value that 
translates to a bottom cell border of TABLE_BORDER_DOUBLE, a top cell border 
width of TABLE_BORDER_NONE, a right cell border width of TABLE_BORDER_SINGLE, 
and a left cell border width of TABLE_BORDER_DOUBLE.  See the CDTC_xxx and 
CDTC_xxx_V42_xxx entries for details.

The RowSpan member and the ColumnSpan member of this structure are used to 
merge or span a group of contiguous cells into one cell.  If the cell is not 
involved in a merger, each of these structure members should be set to 1.

In order to specify a group of spanned cells, you specify the RowSpan and 
ColumnSpan members of this structure for the most bottom-right cell in the 
group.  This is the cell that is doing the spanning.  RowSpan specifies the 
number of rows spanned by the cell; use 1 for the cell itself and add 1 for 
every cell above it.  ColumnSpan specifies the number of columns spanned by the 
cell; use 1 for the cell itself and add 1 for every cell to the left of it.  
For all other cells in this group, specify 1 for RowSpan and 1 for ColumnSpan.  
Also, for all cells that are not in the same row as the cell doing the 
spanning, specify CDTABLECELL_INVISIBLEV for the Flags member of this 
structure.  Specify CDTABLECELL_INVISIBLEH for the Flags member of this 
structure for those cells in the group that are in the same row as the cell 
doing the spanning.  These flags indicate that these cells are invisible.  Do 
not set the Flags member to CDTABLECELL_INVISIBLEH or to CDTABLECELL_INVISIBLEV 
for the cell that is doing the spanning.  The cell that is doing the spanning 
will have a RowSpan and/or a ColumnSpan that is greater than one and will be 
the size of all the cells it spans.

For example, 
CDTABLECELL cell1_1,cell2_1,cell3_1, cell4_1;
For the following table:  
		
		
		
		

Use:
cell1_1.Flag |= INVISIBLEV
cell1_1.RowSpan = 1
cell1_1.ColumnSpan = 1		
cell2_1.Flag |= INVISIBLEV
cell2_1.RowSpan = 1
cell2_1.ColumnSpan = 1		
cell3_1.Flag |= INVISIBLEV
cell3_1.RowSpan = 1
cell3_1.ColumnSpan = 1		
cell4_1.RowSpan = 4
cell4_1.ColumnSpan = 1		

CDTABLECELL cell1_1,cell2_1,cell3_1, cell2_1, cell2_2, cell3_1, cell3_2;
For the following table:  

		
		
		
		

Use:
cell1_1.Flag |= INVISIBLEV
cell1_1.RowSpan = 1
cell1_1.ColumnSpan = 1	cell1_2.Flag |= INVISIBLEV
	cell1_2.RowSpan = 1
	cell1_2.ColumnSpan = 1	
cell2_1.Flag |= INVISIBLEV
cell2_1.RowSpan =1
cell2_1.ColumnSpan = 1	cell2_2.Flag |= INVISIBLEV
	cell2_2.RowSpan =1
	cell2_2.ColumnSpan = 1	
cell3_1.Flag |= INVISIBLEH
cell3_1.RowSpan = 1
cell3_1.ColumnSpan = 1	cell3_2.RowSpan = 3
	cell3_2ColumnSpan = 2	
		


Note that rich text fields are items of type TYPE_COMPOSITE. Therefore, API 
programs that run on non-Intel architecture platforms must perform 
host/canonical conversion on CD record structures such as this when accessing 
rich text item data in a note.
**See Also :**
[CDTABLEBEGIN](D:/md_files/CDTABLEBEGIN.md)
[CDTABLECELL_xxx](D:/md_files/CDTABLECELL_xxx.md)
[CDTABLEEND](D:/md_files/CDTABLEEND.md)
[CDTC_xxx](D:/md_files/CDTC_xxx.md)
[CDTC_xxx_V42_xxx](D:/md_files/CDTC_xxx_V42_xxx.md)
[SIG_CD_xxx](D:/md_files/SIG_CD_xxx.md)
[TABLE_BORDER_xxx](D:/md_files/TABLE_BORDER_xxx.md)
---
