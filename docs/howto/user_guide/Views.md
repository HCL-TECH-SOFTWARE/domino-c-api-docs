##### Chapter 8-2
##### Views

A view note is a note of class NOTE_CLASS_VIEW, which defines how documents in a database are sorted and displayed. The sample program MAKEVIEW demonstrates how to create a view note, and the sample program READVIEW shows how to read an existing view.<br>
<br>
A view note consists of at least three items: a $TITLE item, a $FORMULA item, and a $VIEWFORMAT item. A view note may also contain other items, depending on the options used in the view.<br>
<br>
 <br>
<b><font size="5" color="#000080">$TITLE</font></b><br>
<br>
The $TITLE item is simply an item of type TYPE_TEXT, which contains a string specifying the name of the view.<br>
<br>
<br>
<b><font size="5" color="#000080">$FORMULA</font></b><br>
 <br>
The $FORMULA item is an item of type TYPE_FORMULA, which contains the view selection formula (compiled using NSFFormulaCompile), any column formulas (also compiled), and a list of the item names<font color="#FF0000"> </font>of each column. The $FORMULA item is constructed as follows:<br>
 
<ol type="1">
<li>Compile the selection formula. <br>
<br>
For each column in the view:<br>

<li>Compile the column formula.
<li>Call NSFFormulaSummaryItem to set the column itemname in the $FORMULA item.
<li>Call NSFFormulaMerge to merge the column formula into the $FORMULA item. 
<ul> </ul>
</ol>
In order to create a view that indents response documents or if you want a replication conflict indicator to appear in your view, add a $Conflict and then a $REF to the end of the summary items in the $FORMULA item using NSFFormulaSummaryItem before you append the $FORMULA to the note.<br>
<br>
<br>
<b><font size="5" color="#000080">$VIEWFORMAT</font></b><br>
 <br>
The $VIEWFORMAT item is an item of type TYPE_VIEW_FORMAT. It consists of a VIEW_TABLE_FORMAT structure, one or more VIEW_COLUMN_FORMAT structures (one for each column), a VIEW_TABLE_FORMAT2 structure, one or more VIEW_COLUMN_FORMAT2 structures (one for each column), and a VIEW_TABLE_FORMAT3 structure. If the VIEW_COLUMN_FORMAT2 and VIEW_TABLE_FORMAT3 structures are not provided programatically, a default for each will be created.<br>
<br>
<b><font size="4" color="#000080">VIEW_TABLE_FORMAT</font></b><br>
<br>
The VIEW_TABLE_FORMAT structure contains information on how the view is formatted (for example, whether unread documents should be highlighted).<br>
<br>
<b><font size="4" color="#000080">VIEW_COLUMN_FORMAT</font></b><br>
<br>
The VIEW_COLUMN_FORMAT structure defines the appearance of each column in the view (for example, the size of the column title, the size of the compiled column formula, the column width, and whether the column is sorted).<br>
<br>
Following the series of VIEW_COLUMN_FORMAT structures (one for each column) are the packed, variable-length strings whose lengths are defined in the structures -- the column's itemname, title, formula, and constant value. The strings associated with the first column are listed first, followed by the second column's strings, and so on.<br>
<br>
To create a view that indents response documents in a given column, set the Flags1 member of the VIEW_COLUMN_FORMAT item of that column to VCF1_M_Response.<br>
<br>
<b><font size="4" color="#000080">VIEW_TABLE_FORMAT2</font></b><br>
<br>
The VIEW_TABLE_FORMAT2 structure contains additional formatting information, including the view background color and fonts.<br>
<br>
<b><font size="4" color="#000080">VIEW_COLUMN_FORMAT2</font></b><br>
<br>
The VIEW_COLUMN_FORMAT2 structure contains additional formatting information, including the FontID of the column header. There is one  VIEW_COLUMN_FORMAT2 structure for each column. <br>
<br>
<b><font size="4" color="#000080">VIEW_TABLE_FORMAT3</font></b><br>
<br>
The VIEW_TABLE_FORMAT3 structure contains additional formatting information, including the R5 view background color.<br>
<br>
<br>
<b><font size="5" color="#000080">OTHER FIELDS</font></b><br>
<br>
Optionally, views can contain other fields.<br>
<br>
<b><font size="4" color="#000080">$COLLATION</font></b><br>
<br>
A $COLLATION field is required for categorized, sorted views.  <br>
<br>
The $COLLATION item consists of a COLLATION structure followed by a COLLATE_DESCRIPTOR structure for each category or sort key, followed by the packed item names of the categorized or sorted columns.<br>
<br>
The sample program MAKEVIEW defines this optional field.<br>
<br>
<b><font size="4" color="#000080">$Flags</font></b><br>
<br>
This text field, defined by the DESIGN_FLAGS symbol in stdnames.h, contains a sequence of characters that further describe the note. This field may appear in a variety of design notes, including view notes. The symbol set DESIGN_FLAG_xxx in stdnames.h defines the characters that can appear in this field. Certain characters are specific to certain types of design notes, as described in stdnames.h. <br>
<br>
<br>
<b><font size="5" color="#000080">Folders</font></b><br>
<br>
Folders are implemented as a specialized type of view. A folder note is a view note whose $Flags item field is set to  DESIGN_FLAG_FOLDER_VIEW. A folder note also contains an item, $Collection, that contains the list of documents and folders contained in the folder. The HCL C API for Domino and Notes has folder functions that simplify access to folders. Applications do not need to manipulate the on-disk records directly.
---
