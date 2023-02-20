##### Chapter 6-3
##### Listing the Documents in a View

This chapter examines the sample program VIEWIDS, which prints out a list of all documents in a specified view of a specified database. VIEWIDS demonstrates the use of several data types and functions that you can use to access views.<br>
<br>
<br>
<b><font size="5" color="#000080">Data Types</font></b><br>
<br>
The following two data types relate to collections:<br>

<ul type="disc">
<li>The HCOLLECTION data type is a handle for an open collection of notes. 
<li>The COLLECTIONPOSITION data structure is used to specify the position of a note in a view.</ul>
<br>
<br>
<b><font size="5" color="#000080">Functions</font></b><br>
<br>
C API functions that relate to views use the prefix NIF (Notes Index Facility).<br>
<br>
NIFFindView finds the note ID of a view, given the name of the view.<br>
<br>
NIFOpenCollection opens a collection associated with the view and database being used. It returns the address of a collection handle (HCOLLECTION) as one of its output parameters.<br>
<br>
NIFReadEntries scans a collection referenced by a collection handle (HCOLLECTION). You specify the starting position for the scan,<font color="#FF0000"> </font>by setting the COLLECTIONPOSITION parameter.<br>
 <br>
NIFCloseCollection closes the collection, updating data on disk if required and freeing memory allocated to the collection.<br>
<br>
<br>
<b><font size="5" color="#000080">The VIEWIDS Sample Program</font></b><br>
<br>
The sample program VIEWIDS builds a collection from a view and then finds the note IDs of all documents in the collection. The program does not actually read the documents. This section describes fragments of the program that illustrate use of the functions described above.<br>
<br>

<table width="100%" border="1">
<tr valign="top"><td width="100%"><b>Example:</b><font color="#FF0000"> </font><b>Get Note ID of the Specified View in VIEWIDS</b></td></tr>
</table>
<tt>&nbsp;</tt><tt>char &nbsp; &nbsp; &nbsp;*ViewName; &nbsp;/* name of the view we'll read */</tt><br>
<tt>&nbsp;</tt><tt><font size="2">DBHANDLE &nbsp;hDB; &nbsp; &nbsp; &nbsp; &nbsp;/* handle of the database */<br>
 NOTEID &nbsp; &nbsp;ViewID; &nbsp; &nbsp; /* note id of the view */<br>
	</font></tt><br>
<tt><font size="2">&nbsp;/* Get the note id of the view we want. */</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp;if (error = NIFFindView (hDB, ViewName, &amp;ViewID))<br>
 &nbsp; &nbsp; {<br>
 &nbsp; &nbsp; &nbsp; &nbsp; NSFDbClose (hDB);</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;text_len=OSLoadString(NULLHANDLE,ERR(error),error_text,sizeof(error_text));</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;printf(&quot;error: %s\n&quot;,error_text);</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;NotesTerm();<br>
 &nbsp; &nbsp; &nbsp; &nbsp; return(error);<br>
 &nbsp; &nbsp; }</font></tt><br>
<br>
This fragment calls NIFFindView. The inputs to the function are the handle of a database and the name of a view in the database. The output of the function is the note ID of the view. (Remember that views are a type of note.)<br>
<br>

<table width="100%" border="1">
<tr valign="top"><td width="100%"><b>Example:</b><font color="#FF0000"> </font><b>Opening a Collection in VIEWIDS</b></td></tr>
</table>
<tt><font size="2">&nbsp;DBHANDLE &nbsp; &nbsp; hDB; &nbsp; &nbsp; &nbsp; &nbsp; /* handle of the database */<br>
 NOTEID &nbsp; &nbsp; &nbsp; ViewID; &nbsp; &nbsp; &nbsp;/* note id of the view */<br>
 HCOLLECTION &nbsp;hCollection; /* collection handle */<br>
</font></tt><br>
<tt><font size="2">/* Get a collection using this view. */</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp;if (error = NIFOpenCollection(<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; hDB, &nbsp; /* handle of db with view */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; hDB, &nbsp; /* handle of db with data */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ViewID, &nbsp; &nbsp; /* note id of the view */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 0, &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; /* collection open flags */</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;NULLHANDLE, &nbsp;/* handle to unread ID list (input and return) */</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&amp;hCollection,/* collection handle (return) */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; NULLHANDLE, &nbsp;/* handle to open view note (return) */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; NULL,	 &nbsp; &nbsp; &nbsp;/* universal note id of view (return) */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; NULLHANDLE, &nbsp;/* handle to collapsed list (return) */</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;NULLHANDLE)) /* handle to selected list (return) */<br>
 &nbsp; &nbsp; {<br>
 &nbsp; &nbsp; &nbsp; &nbsp; NSFDbClose (hDB);<br>
 &nbsp; &nbsp; &nbsp; &nbsp; </font></tt><tt><font size="2">text_len=OSLoadString(NULLHANDLE,ERR(error),error_text,sizeof(error_text));</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;printf(&quot;error: %s\n&quot;,error_text);</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;NotesTerm();<br>
 &nbsp; &nbsp; &nbsp; &nbsp; return(error);</font></tt><tt><font size="2"><br>
 &nbsp; &nbsp; }</font></tt><br>
<br>
<br>
This fragment calls the function NIFOpenCollection to open the collection associated with the view that the program is using. The first argument (input) to this function is the handle of the database that contains the view note. The second argument (input) is the handle of the database that contains the data to which the view is applied.<br>
<br>
NOTE: When you use the Notes user interface, these two databases always are the same. With the C API, you can apply views from one database to another database. You can take advantage of this feature by using the user interface to create a special database containing views that you need in C API programs. Your C API code can then apply the views in the&quot;view database&quot; to any other database.<br>
<br>
The third argument (input) to NIFOpenCollection is the note ID of the view to use. This note ID, of course, is in the database referred to by the first argument; we obtained the view's note ID when we called NIFFindView. The fourth argument (input) is a set of flags that control the way the collection is opened. For more information about these flags, see the <i>Reference</i><i>.</i> This program uses none of the flags.<br>
<br>
The sixth argument (output) to NIFOpenCollection is the handle of the current<font color="#FF0000"> </font>collection for this view of the database. The collection reflects the data in the database at the moment the call completes.<br>
<br>
NOTE: If a database might change while your program is running, use the function NIFUpdateCollection. This function re-synchronizes a collection with the database whenever you call it.<br>
<br>
The other arguments to NIFOpenCollection return information about the collection that you may find useful in some programs.  For more information about these arguments, see the <i>Reference</i><i>.</i><br>
<br>

<table width="100%" border="1">
<tr valign="top"><td width="100%"><b>Example: Reading Entries In a Collection in VIEWIDS</b></td></tr>
</table>
<br>
<tt><font size="2">&nbsp;HCOLLECTION &nbsp; &nbsp; &nbsp; &nbsp;hCollection; &nbsp; /* collection handle */<br>
 COLLECTIONPOSITION CollPosition; &nbsp;/* position within collection */<br>
 HANDLE &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; hBuffer; &nbsp; &nbsp; &nbsp; /* handle to buffer of note ids */<br>
 DWORD &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;EntriesFound; &nbsp;/* number of entries found */</font></tt><br>
<tt><font size="2">&nbsp;DWORD &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;NotesFound=0; &nbsp;/* number of documents found */</font></tt><br>
<tt><font size="2">&nbsp;WORD			SignalFlag &nbsp; &nbsp; /* signal and share warning flags */</font></tt><br>
<br>
<br>
<tt><font size="2">/* Set up the data structure, COLLECTIONPOSITION, that controls where in<br>
the collection we will begin when we read the collection. &nbsp;Specify that we<br>
want to start at the beginning. */</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; CollPosition.Level = 0;<br>
 &nbsp; &nbsp;CollPosition.Tumbler[0] = 0;</font></tt><br>
<br>
<tt><font size="2">/* Get a buffer with information about each entry in the collection.<br>
 &nbsp; Perform this routine in a loop. &nbsp;Terminate loop when SignalFlag<br>
 &nbsp; indicates that there is no more information to get. &nbsp; */</font></tt><br>
<br>
<tt>&nbsp; &nbsp; &nbsp; do</tt><br>
<tt>&nbsp; &nbsp; &nbsp; {</tt><br>
<tt><font size="2">&nbsp; &nbsp;if ( error = NIFReadEntries(<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;hCollection, &nbsp; &nbsp; &nbsp; /* handle to this collection */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&amp;CollPosition, &nbsp; &nbsp; /* where to start in collection */</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; NAVIGATE_NEXT, &nbsp; &nbsp; /* order to use when skipping */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;1L, &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* number to skip */</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; NAVIGATE_NEXT, &nbsp; &nbsp; /* order to use when reading */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;0xFFFFFFFF, &nbsp; &nbsp; &nbsp; &nbsp;/* max number to read */</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; READ_MASK_NOTEID, &nbsp;/* info we want */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&amp;hBuffer, &nbsp; &nbsp;/* handle to info buffer (return)	*/<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;NULL, &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* length of info buffer (return) */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;NULL, &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* entries skipped (return) */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&amp;EntriesFound, &nbsp; &nbsp;/* entries read (return) */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&amp;SignalFlag))	 &nbsp;/* share warning and more signal flag</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;(return) */</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp; &nbsp;NIFCloseCollection (hCollection);<br>
 &nbsp; &nbsp; &nbsp; &nbsp;NSFDbClose (hDB);<br>
 &nbsp; &nbsp; &nbsp; &nbsp;</font></tt><tt><font size="2">text_len=OSLoadString(NULLHANDLE,ERR(error),error_text,sizeof(error_text));</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; printf(&quot;error: %s\n&quot;,error_text);</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; NotesTerm();<br>
 &nbsp; &nbsp; &nbsp; &nbsp;return(error);</font></tt><tt><font size="2"><br>
 &nbsp; }</font></tt><br>
<br>
<br>
The code initializes the COLLECTIONPOSITION structure to the beginning of the collection. For structure operations other than initialization, such as sets and reads, use the C API functions explained below.<br>
<br>
After initializing COLLECTIONPOSITION, the program calls NIFReadEntries, which reads a collection and returns information from it. The first argument (input) to this function is the handle of the collection, obtained through the call to NIFOpenCollection. The second argument (input) is a COLLECTIONPOSITION, which points to the location in the collection where NIFReadEntries starts its actions. <br>
<br>
From this starting point, NIFReadEntries operates in two phases. First, the function skips some number of entries in the collection, based on your instructions contained in the third and fourth  arguments (both inputs). The third argument is the manner in which to navigate the collection tree while skipping entries, and the fourth argument is the number of entries to skip. For information about the flags that can appear in the third argument, see NAVIGATE_FLAG in the <i>Reference.</i> As the function skips entries, the COLLECTIONPOSITION structure changes to indicate the skipping.<br>
<br>
In the example code, when NIFReadEntries is called for the first time, the second argument means, &quot;Start at the beginning, before the first entry&quot;; the third argument means, &quot;Go to the next entry as indicated by the skip count&quot;; and the fourth argument means, &quot;Skip one.&quot; After the skipping phase, the COLLECTIONPOSITION points to the first entry in the collection.<br>
<br>
In its second phase, NIFReadEntries reads some number of entries in the collection and returns information about them. The fifth, sixth, and seventh arguments (all inputs) control the manner in which NIFReadEntries does this. The fifth argument specifies how to navigate the collection tree while reading entries. The sixth argument is the number of entries to read. The seventh argument is the information to return about each entry read. The reading phase begins at the COLLECTIONPOSITION set by the skipping phase. <br>
<br>
In the example code, the fifth argument means, &quot;Find the next entry using a pre-order (node-left-right) scan of the collection tree.&quot; This reads<font color="#FF0000"> </font>the collection just as it is displayed by the Notes user interface. The sixth argument means, &quot;Find as many entries as possible.&quot; The seventh argument specifies that the note ID of each entry be returned. For information about the flags you can specify in the seventh argument, see READ_MASK_XXX in the <i>Reference.</i> <br>
<br>
Based on these settings for arguments three through seven, NIFReadEntries reads each entry in the collection and returns its note ID in the same order as the notes appear in the view at the user interface.<br>
<br>
NOTE: While navigating a collection, NIFReadEntries treats all objects in the tree identically, skipping and reading categories, documents, and responses in the same way.<br>
<br>
The eighth argument (output) to NIFReadEntries is a handle to the buffer of information that the function returns. In this example, the buffer contains note IDs.  As in the example, your programs should check that a valid handle is returned and exit if it is a NULLHANDLE, signifying that no data buffer exists. The eleventh argument (output) is the number of entries read.<br>
<br>
The ninth and tenth arguments to NIFReadEntries return other information that you may find useful in your programs. For more information about these arguments, see the <i>Reference.</i><br>
<br>
The twelfth argument returns a set of flags indicating whether there is more information than can fit in the returned buffer and/or whether the collection has changed since it was last read. The example code calls NIFReadEntries repeatedly in a loop until the SIGNAL_MORE_TO_DO bit is cleared in this parameter, to ensure that it obtains information about all the notes in a collection. When NIFReadEntries is about to be called again, the COLLECTION position points to the last entry read in the previous call.  Using NAVIGATE_NEXT for the skip navigate flag (the third parameter) and 1L for the skip count (the fourth parameter) properly updates the COLLECTION position to point to the next entry.  For more information about these arguments, see the <i>Reference.</i><br>
<br>

<table width="100%" border="1">
<tr valign="top"><td width="100%"><b>Example: Parsing the Buffer Returned by NIFReadEntries in VIEWIDS</b></td></tr>
</table>
<br>
<tt><font size="2">&nbsp;HANDLE &nbsp;hBuffer; &nbsp; &nbsp; &nbsp; /* handle to buffer of note ids */<br>
 NOTEID &nbsp;*IdList; &nbsp; &nbsp; &nbsp; /* pointer to a note id */</font></tt><br>
<br>
<br>
<tt><font size="2">/* Lock down (freeze the location of) the buffer of entry IDs. Cast<br>
the resulting pointer to the type we need. */</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; IdList = (NOTEID *) OSLockObject (hBuffer);</font></tt><br>
<br>
<tt><font size="2">/* Print out the list of note IDs found by this search. Don't print a note <br>
ID if it is a &quot;dummy&quot; ID that stands for a category in the collection. */</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; printf (&quot;\n&quot;);<br>
 &nbsp; &nbsp;for (i=0; i&lt;EntriesFound; i++)<br>
 &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp; &nbsp;if (NOTEID_CATEGORY &amp; IdList[i]) continue; <br>
 &nbsp; &nbsp; &nbsp; &nbsp;printf (&quot;Note count is %lu. \t Note ID is: %lX\n&quot;, </font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;++NotesFound, IdList[i]);<br>
 &nbsp; &nbsp;}</font></tt><br>
<br>
<tt><font size="2">/* Unlock the list of IDs. */</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; OSUnlockObject (hBuffer);</font></tt><br>
<br>
<tt><font size="2">/* Free the memory allocated by NIFReadEntries. */</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; OSMemFree (hBuffer);</font></tt><br>
<br>
<tt>/* Loop if the end of the collection has not been reached because the buffer<br>
 &nbsp; was full. &nbsp;*/</tt><br>
<br>
<tt>&nbsp; &nbsp;} &nbsp;while (SignalFlag &amp; SIGNAL_MORE_TO_DO);</tt><br>
<br>
This code calls OSLockObject to lock the memory location of the returned note ID buffer and cast the resulting locked pointer to the type of data in the buffer, then prints out all the note IDs in the buffer. If the view uses categories, there will be a category entry in the buffer at each place that a category heading appears in the collection. The code tests for these category entries so they are not printed along with the note IDs.<br>
<br>
The code then unlocks and frees the buffer allocated by NIFReadEntries and closes the collection,  because a program must close every resource that it opens. Although we don't show it here, the program should close the database properly.
---
