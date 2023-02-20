##### Chapter 6-5
##### Advanced Operations

This chapter discusses several more useful operations that you can perform on views.<br>
<br>
<br>
<b><font size="5" color="#000080">Listing All the Documents in a Category</font></b><br>
<br>
The sample program ONECAT finds all the main-topic documents in a view category. First, it calls NIFFindByName to search for the first note in the view category specified on the command line. It then calls NIFReadEntries, telling it to start at the first note in the category. The read flags READ_MASK_NOTEID, READ_MASK_INDENTLEVELS, and READ_MASK_INDEXPOSITION are set. (A note's indent level tells whether it is a main document, a response, a response to response, and so on.)<br>
<br>
The program parses the<font color="#FF0000"> </font>buffer returned by NIFReadEntries<font color="#FF0000"> </font>for main-topic documents until it finds<font color="#FF0000"> </font>another top-level category document, marking the start of another category in the view. As the program finds<font color="#FF0000"> </font>each main-topic document, it displays the document<font color="#FF0000"> </font>note ID.<br>
<br>
<br>
<b><font size="5" color="#000080">Getting Summary Information for a View</font></b><br>
<br>
Call NIFReadEntries with READ_MASK_SUMMARYVALUES set to obtain a buffer containing the view column value data of each  note in a view. This lets you read the values of a note's simple data fields (also known as summary data values) that appear in the view without the overhead of opening the note.<br>
<br>
The information in a view summary of values is as follows:<br>

<ul>ITEM_VALUE_TABLE containing header information (total length of summary, number of items in summary)<br>
WORD containing length of item #1 (including data type)<br>
WORD containingthe length of item #2 (including data type)<br>
WORD containing the length of item #3 (including data type)<br>
...<br>
USHORT containing the data type of item #1<br>
value of item #1<br>
USHORT containing the data type of item #2<br>
value of item #2<br>
USHORT containing the data type of item #3<br>
value of item #3<br>
....</ul>
<br>
The sample program VIEWSUMM calls NIFReadEntries with READ_MASK_NOTEID and READ_MASK_SUMMARYVALUES. The function returns a buffer containing the note ID and summary data for each item in the view. For each item, VIEWSUMM parses the note ID, then passes a pointer to the note's summary buffer to the local function PrintSummary. PrintSummary parses the summary information and displays the value of each item in the summary.<br>
<br>
<br>
<b><font size="5" color="#000080">Complex Navigation of a Collection</font></b><br>
<br>
The sample program NAVIGATE demonstrates how to do complex navigation in a collection by repeatedly calling NIFReadEntries with properly set navigation flags. The program goes to the second major category in the collection and then to the second subcategory in the main category. The program then prints the note IDs of all the main topic documents in the subcategory.<br>
<br>
The program begins by setting<font color="#FF0000"> </font>the COLLECTIONPOSITION structure, used by the first call to NIFReadEntries, to point to the beginning of the collection. It sets the skip_navigate_flags parameter to NAVIGATE_NEXT_PEER, which tells the function to skip to the next entry that is at the same level in the view hierarchy as the current one.<br>
<br>
After the first call to NIFReadEntries, the COLLECTIONPOSITION structure is set to the position of the first note satisfying the function call. The program then calls<font color="#FF0000"> </font>NIFReadEntries a second time, and the function<font color="#FF0000"> </font>starts reading from the new collection position. This time, the skip_navigate_flags parameter is set to NAVIGATE_CHILD, which tells the function to go down one level into subcategories.<br>
<br>
The program calls<font color="#FF0000"> </font>NIFReadEntries a third time with skip_navigate_flags set to NAVIGATE_NEXT_PEER to get to the second subcategory. Then it calls the function<font color="#FF0000"> </font>once more in a do loop with skip_navigate_flags set to NAVIGATE_CHILD, which sets the collection position to the main-topic level. Now the program can parse the list of note IDs, printing each one.
---
