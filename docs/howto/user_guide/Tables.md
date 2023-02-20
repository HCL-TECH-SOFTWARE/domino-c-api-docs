##### Chapter 7-2
##### Tables

<b><font size="5" color="#000080">Introduction</font></b><br>
<br>
This chapter explains how to create a table in the rich text field of a document.<br>
<br>
<br>
<b><font size="5" color="#000080">CD Table Records</font></b><br>
<br>
A table in a rich text field consists of a CDTABLEBEGIN record, one or more CDTABLECELL records, and a CDTABLEEND. <br>
<br>
<br>
<b><font size="5" color="#000080">Creating a Table</font></b><br>
<br>
To create a table in a rich text field, initialize the necessary CD records, convert them to Domino canonical format in a buffer in the proper sequence, and then call NSFItemAppend to append the buffer to the rich text field of an open note.<br>
<br>
A table cannot be the first paragraph in a rich text field; there must be at least one paragraph before it. Therefore, initialize and append at least a CDPABDEFINITION, a CDPABREFERENCE, and a CDTEXT record with a 0-length string before the first CDTABLEBEGIN.<br>
<br>
The Notes editor imposes the following rules on tables in rich text fields:<br>

<ul type="disc">
<li>Editor tables must occupy their own paragraphs. That is, before outputting a CDTABLEBEGIN record, you must create an empty paragraph. You can do this minimally by outputting a CDPARAGRAPH record followed by a CDTEXT record with text of 0 length. The LeftMargin field of the CDTABLEBEGIN record is the margin at which the leftmost border is painted. After the table has been started with a CDTABLEBEGIN record, records that define the table cells must be output. The first record that defines a cell is the CDTABLECELL record. Among other items, this record contains the left and right margins of the cell. These margins represent the extreme margins that any paragraph in the cell can use. In other words, no paragraph in the cell can have a left margin or first line left margin less than that of the cell's left margin. <br>
Likewise, no paragraph can have a right margin greater than the cell's right margin. Note that these margins are not the locations of the cell borders. The border positions are implied by the HorizInterCellSpace and the widths of the cell contents (Cell.RightMargin - Cell.LeftMargin).</ul>

<ul type="disc">
<li>Each cell must have at least one paragraph. CDPARAGRAPH, CDPABDEFINITION, CDPABREFERENCE, and CDTEXT records are enough. All PABs referenced by paragraphs in a table must have PABFLAG_DISPLAY_RM set in the Flags WORD. This forces Notes to honor and display the right margin of the paragraph. CD records for following cells are packed one directly after another. After you create the top row of CDPABDEFINITIONS, we suggest that you reuse these existing cell paragraph PABIDs in CDPABREFERENCEs in the remaining cell paragraphs. This saves memory and reduces needless calculations.</ul>

<ul type="disc">
<li>After you define all the cells, you must define<font color="#FF0000"> </font>a CDTABLEEND record. This signifies that you have completely specified<font color="#FF0000"> </font>the table. Also note that there must be at least one paragraph following a table in any rich text field. You can do this minimally by outputting a CDPARAGRAPH, a CDPABREFERENCE, and a CDTEXT record with a 0-length string.  </ul>
<br>
You must observe several general rules when creating a table, since they are enforced by the user interface when it attempts to display a table that you have created programmatically: <br>

<ul type="disc">
<li>The maximum RightMargin for any paragraph is 22.75 inches.
<li>The maximum table width is 22.75 inches - LeftMargin inches.
<li>The maximum number of rows in a table is 255.
<li>The maximum number of columns in a table is 64.
<li>The minimum intercell distance is 0.0625 inches (1/16th of an inch).</ul>
<br>
<br>
<b><font size="5" color="#000080">Required CD Records</font></b><br>
<br>
This section shows the data structures of the required CD records.<br>
<br>
When you initialize these data structures, you must zero any fields that you do not initialize with specific values. This is also true of partially-used flags fields. In other words, if only the low 5 bits of a flags word are set, you must set the high 11 bits to 0.
<table width="100%" border="1">
<tr valign="top"><td width="100%"><b>Required CD Records for Defining Tables</b></td></tr>
</table>
<tt><font size="2">/* &nbsp;</font></tt><tt><font size="2">Begin Table Record - This record specifies the beginning</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; of a table. It contains interesting information about the</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; format and size of the table.<br>
*/</font></tt><br>
<tt><font size="2">typedef struct<br>
{<br>
 &nbsp;BSIG Header;<br>
 &nbsp;WORD LeftMargin;<br>
 &nbsp;WORD HorizInterCellSpace;<br>
 &nbsp;WORD VertInterCellSpace;</font></tt><br>
<tt><font size="2">&nbsp; WORD V4HorizInterCellSpace;<br>
 &nbsp;WORD V4VertInterCellSpace;<br>
 &nbsp;WORD Flags;<br>
} CDTABLEBEGIN;</font></tt><br>
<br>
<tt><font size="2">Header &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;Standard BSIG with Signature set to </font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; SIG_CD_TABLEBEGIN<br>
LeftMargin &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;Left margin (in twips) of the table.</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 1 INCH = 72 POINTS, and 1 POINT = 20 TWIPS<br>
HorizInterCellSpace &nbsp; Space (in twips) between each cell and its <br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;column border.<br>
VertInterCellSpace &nbsp; &nbsp;Space (in twips) between each cell and its</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; row border.</font></tt><br>
<tt><font size="2">V4HorizInterCellSpace Defaults to 0. (Spare in V3) &nbsp;</font></tt><br>
<tt><font size="2">V4VertInterCellSpace &nbsp;Defaults to 0. (Spare in V3)<br>
Flags &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; Bits to follow<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;0 &nbsp; &nbsp; 1 if Fit to window is desired<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;0 if Fit to windows is not desired<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;1-15 &nbsp;0</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; CDTABLE_AUTO_CELL_WIDTH (0x0001)</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; CDTABLE_V4_BORDERS (0x0002) &nbsp;</font></tt><br>
<br>
<tt><font size="2">/* &nbsp;</font></tt><tt><font size="2">Table Cell Record - This record defines a cell within a table.</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; It contains interesting information about the format and size</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; of the cell.<br>
*/</font></tt><br>
<br>
<tt><font size="2">typedef struct<br>
{<br>
	BSIG Header;<br>
	BYTE Row;						<br>
	BYTE Column;					<br>
	WORD LeftMargin;				<br>
	WORD RightMargin;				<br>
	WORD FractionalWidth;			<br>
	BYTE Border;					<br>
	BYTE Flags;						<br>
	WORD v42Border;</font></tt><br>
<tt><font size="2">	BYTE RowSpan;</font></tt><tt><font size="2"><br>
</font></tt><tt><font size="2">	BYTE ColumnSpan;<br>
	WORD BackgroundColor;<br>
} CDTABLECELL;</font></tt><br>
<br>
<tt><font size="2">Header &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; Standard BSIG with Signature set to <br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; SIG_CD_TABLECELL<br>
Row &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;Specifies the row number (0 based).<br>
Column &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; Specifies the column number (0 based).<br>
LeftMargin &nbsp; &nbsp; &nbsp; Left margin (in twips) of the cell.<br>
RightMargin &nbsp; &nbsp; &nbsp;Right margin (in twips) of the cell.<br>
FractionalWidth &nbsp;20&quot; (in twips) * CellWidth / TableWidth (used <br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; only if the CDTABLEBEGIN record has the<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; fit to window bit asserted).<br>
Border &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; Bits to follow<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 0-1 &nbsp; &nbsp;Left border<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 2-3 &nbsp; &nbsp;Right border<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 4-5 &nbsp; &nbsp;Top border<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 6-7 &nbsp; &nbsp;Bottom border<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; TABLE_BORDER_NONE, TABLE_BORDER_SINGLE, and <br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; TABLE_BORDER_DOUBLE are the allowed values<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; for the borders </font></tt><tt><font size="2">(see shift and mask CDTC_xxx values).</font></tt><tt><font size="2"><br>
Flags &nbsp; &nbsp; &nbsp;	 &nbsp; &nbsp;</font></tt><tt><font size="2">Only two are currently in use:</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; </font></tt><tt>CDTABLECELL_USE_BKGCOLOR - Set if background color is specified.<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;CDTABLECELL_USE_V42BORDERS - Set if table was created with </tt><br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;Notes Release 4.5 or later.</tt><tt><font size="2"><br>
v42Border &nbsp; &nbsp; &nbsp; &nbsp;</font></tt><tt><font size="2">Sets wider borders in Notes Release 4.5 or later</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;(see shift and mask CDTC_xxx_V42_xxx values</font></tt><tt><font size="2">).</font></tt><br>
<tt><font size="2">ColumnSpan &nbsp; &nbsp; &nbsp; Must be set to 0.</font></tt><br>
<tt><font size="2">RowSpan &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;Must be set to 0.<br>
BackgroundColor &nbsp;Sets background color.</font></tt><br>
<br>
<tt><font size="2">/* &nbsp;</font></tt><tt><font size="2">End Table Record - This record specifies the end of a table. */</font></tt><br>
<tt><font size="2">typedef struct &nbsp;<br>
{<br>
 &nbsp; &nbsp;BSIG Header;<br>
 &nbsp; &nbsp;WORD SpareWORD;<br>
 &nbsp; &nbsp;WORD SpareFlags;<br>
} CDTABLEEND;</font></tt><br>
<br>
<tt><font size="2">Header &nbsp; &nbsp; &nbsp; &nbsp;Standard BSIG with Signature set to SIG_CD_TABLEEND<br>
SpareWORD &nbsp; &nbsp; Must be set to 0.<br>
SpareFlags &nbsp; &nbsp;Must be set to 0.</font></tt><br>
<br>
<br>
<b><font size="5" color="#000080">The MKTABLE</font></b><font color="#000080"> </font><b><font size="5" color="#000080">Sample Program</font></b><br>
<br>
The source code of the MKTABLE sample program consists of 4 files:<br>

<ul type="disc">
<li>mktable.h	Header file with function declarations and constant definitions
<li>mktable.c 	Main file
<li>cdrecord.c	Routines that deal with paragraph and text CD<font color="#FF0000"> </font>records
<li>cdtable.c	Routines that deal with table CD records</ul>
<br>
The file cdrecord.c contains the following functions for appending CD records to a buffer:<br>

<ul type="disc">
<li>CDPutPabdef creates a paragraph definition Paragraph Attribute Block (PAB) and writes it to a buffer.
<li>CDPutPabref creates a PAB reference and writes it to a buffer.
<li>CDPutPara creates a paragraph record and writes it to a buffer.
<li>CDPutText creates a text block, fills it in, and writes it to a buffer.</ul>
<br>
The data in the buffer must be in Domino canonical format. <br>
<br>
The file cdtable.c has references to the three rules shown above - just search for the word &quot;Rule&quot; using your favorite editor.<font color="#FF0000"> </font><br>
<br>
The file cdtable.c contains the following functions for creating tables in a rich text format:<br>
<br>
CDPutTable creates a complete table based on the number of rows, columns, table width, textlist of cell text entries, and so on, and writes it to a buffer.<br>
CDPutTableBegin creates a CDTABLEBEGIN record in the supplied buffer.<br>
CDPutCell creates a CDTABLECELL record in the supplied buffer.<br>
CDPutTableEnd creates a CDTABLEEND record in the supplied buffer.<br>
<br>
The data in the buffer must be in Domino canonical format.<br>
<br>
NOTE: Some C API programs do not perform host/canonical conversion when accessing or creating low-level structures in rich text. Canonical conversion is not strictly necessary for programs that run only on Intel-architecture platforms such as Windows. However, the source code for such programs is not portable. Source code that does perform host/canonical conversion will run on any platform supported by Domino and Notes, including UNIX platforms. For more information on canonical format requirements, read the &quot;Domino Canonical Format&quot; chapter in this guide.<br>
<br>
Also note that cdrecord.c and cdtable.c routines use the ODSWriteMemory function to convert the CD structures from machine-specific format into Domino canonical format. To reference data from one of<font color="#FF0000"> </font>these structures (PABID, LeftMargin, and so on), copy the structure and use the ODSReadMemory function to<font color="#FF0000"> </font>convert the data back into the machine-specific format.
---
