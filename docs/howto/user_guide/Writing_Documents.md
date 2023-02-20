##### Chapter 5-4
##### Writing Documents

Writing a Domino or Notes document consists of two steps:<br>

<ol type="1">
<li>Opening or creating the document
<li>Writing fields into the document</ol>
<br>
The first part of this chapter explains how to open an existing document or create a new document. The second part shows how to write fields of four basic data types: plain text, numbers, time/date, and text lists. <br>
<br>
We will use the sample program WSIMPLE (short for WriteSIMPLE) to explain writing documents. WSIMPLE is in the subdirectory samples\basic\wsimple. Load wsimple.c in an editor or print it so you can refer to it while you read this chapter.<br>
<br>
<br>
<b><font size="5" color="#000080">Opening and Creating Documents</font></b><br>
 <br>
Documents are notes of class NOTE_CLASS_DOCUMENT. The procedures for opening, creating, updating, and closing documents are the same for all classes of notes.<br>
<br>
You must open a note before you can write or modify data in the note. The function NSFNoteOpen opens a note in a database. NSFNoteOpen requires a NOTEID as input to specify the note, so the note must already exist. The &quot;Reading Documents&quot; chapter shows how to find a note and get the NOTEID using the function NSFSearch. NSFNoteOpen yields a note handle, which is required for most reads and all writes to the fields.<br>
<br>
Use NSFNoteCreate to create a new note. NSFNoteCreate also opens the new note, returning a note handle.<br>
<br>
<br>
<b><font size="5" color="#000080">Updating and Closing Documents</font></b><br>
<br>
Creating or opening a note causes Domino or Notes to maintain an object in memory specified by the note handle. The note handle is required for most reads and all writes to the fields. Any write to a field of a note is held in memory until the note is updated to disk. The function NSFNoteUpdate takes a note handle as input and updates the .nsf file on disk with all the fields written using that handle. Data written using the note handle must be updated to disk before the note is closed, otherwise the data is discarded. Use NSFNoteClose to close any open note and release the memory when the handle is no longer needed.<br>
<br>
The segment of wsimple.c below creates a new note in preparation for writing fields to the document, updates the note to the database on disk, and closes the note.<br>
<br>

<table width="100%" border="1">
<tr valign="top"><td width="100%"><b>wsimple.c: Creating and Updating a Note</b></td></tr>
</table>
<tt><font size="2">&nbsp; DBHANDLE &nbsp; db_handle; &nbsp; /* database handle &nbsp; &nbsp; &nbsp;*/<br>
 &nbsp;NOTEHANDLE note_handle; /* note handle &nbsp; &nbsp; &nbsp; &nbsp;*/<br>
 &nbsp;STATUS &nbsp; &nbsp; error; &nbsp; &nbsp; &nbsp; /* return code from API calls */</font></tt><br>
<br>
<tt><font size="2">&nbsp; if (error = NSFNoteCreate (db_handle, &amp;note_handle))<br>
 &nbsp;{<br>
 &nbsp; &nbsp; &nbsp;PrintAPIError(error);</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; NSFDbClose (db_handle);</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; NotesTerm();</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; return(1);<br>
 &nbsp;}<br>
 &nbsp;</font></tt><tt>.</tt><tt><font size="2"><br>
 &nbsp;</font></tt><tt>.</tt><tt><font size="2">&nbsp;Add and modify fields in the document.<br>
 &nbsp;</font></tt><tt>.</tt><br>
<br>
<tt><font size="2">&nbsp; /* Add the new note to the database. */<br>
 &nbsp;if (error = NSFNoteUpdate (note_handle, 0))<br>
 &nbsp;{</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; PrintAPIError(error);<br>
 &nbsp; &nbsp; &nbsp;NSFNoteClose (note_handle);<br>
 &nbsp; &nbsp; &nbsp;NSFDbClose (db_handle);<br>
 &nbsp; &nbsp; &nbsp;NotesTerm();</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; return(1);<br>
 &nbsp;}</font></tt><br>
<br>
<tt><font size="2">&nbsp; /* Close the note. (Remove its structure from memory.) */<br>
 &nbsp;if (error = NSFNoteClose (note_handle))<br>
 &nbsp;{</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; PrintAPIError(error);<br>
 &nbsp; &nbsp; &nbsp;NSFDbClose (db_handle);<br>
 &nbsp; &nbsp; &nbsp;NotesTerm();</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; return(1);<br>
 &nbsp;}</font></tt><br>
<br>
<br>
<b><font size="5" color="#000080">Writing Fields</font></b><br>
<br>
WSIMPLE calls NSFNoteCreate to create a new note before writing fields in it. NSFNoteCreate yields a note handle. WSIMPLE needs this handle when it calls C API functions such as NSFItemSetText to write data to the fields in the document.<br>
<br>
A document can contain any number of fields. Each field has a Field Name, a Data Type, a Data Length, a Data Value, and a flag word. Domino and Notes support many different data types. WSIMPLE demonstrates writing fields of four basic data types: text, number, time/date, and text list.<br>
<br>
The API provides specific functions, such as NSFItemSetText, to write fields of each of the four basic data types. The API also provides general functions, such as NSFItemAppend, to write any field of any data type. All functions that write fields require as input the note handle, the name of the field, and the data to write. The format of the data depends on the data type. <br>
<br>
WSIMPLE writes five fields to the new document. The first two fields are named FORM and PLAIN_TEXT, respectively, and are both of type text. The third field is named NUMBER and is of type number. The fourth field is named TIME_DATE and is of type time/date. The last field is named TEXT_LIST and is of type text list. <br>
<br>
<br>
<b><font size="4" color="#000080">Writing the FORM Field</font></b><br>
<br>
When creating new documents, a field named FORM is often written to the document to specify a default form to use to display this document. The FORM field should be of type text. Its value should be identical to the name of a form in the database, as specified in the Properties for Form Infobox in the Notes user interface.<br>
<br>

<table width="100%" border="1">
<tr valign="top"><td width="100%"><b>wsimple.c: Writing the FORM Field</b></td></tr>
</table>
<tt><font size="2">&nbsp; NOTEHANDLE note_handle; &nbsp;/* note handle &nbsp; &nbsp; &nbsp; &nbsp; */<br>
 &nbsp;STATUS &nbsp; &nbsp; error; &nbsp; &nbsp; &nbsp; &nbsp;/* return code from API calls */</font></tt><br>
<br>
<tt><font size="2">&nbsp; /* Write the FORM field to the note -- this field specifies<br>
 &nbsp; the default form to use when displaying the note.*/</font></tt><br>
<br>
<tt><font size="2">&nbsp; if (error = NSFItemSetText ( note_handle, <br>
 &nbsp; &nbsp; &nbsp; &nbsp;&quot;FORM&quot;,<br>
 &nbsp; &nbsp; &nbsp; &nbsp;&quot;SimpleDataForm&quot;, <br>
 &nbsp; &nbsp; &nbsp; &nbsp;MAXWORD))<br>
 &nbsp;{</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; PrintAPIError(error);<br>
 &nbsp; &nbsp; &nbsp;NSFNoteClose (note_handle);<br>
 &nbsp; &nbsp; &nbsp;NSFDbClose (db_handle);<br>
 &nbsp; &nbsp; &nbsp;NotesTerm();</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; return(1);<br>
 &nbsp;}</font></tt><br>
<br>
<br>
<b><font size="4" color="#000080">Writing Text Fields</font></b><br>
<br>
WSIMPLE uses NSFItemSetText to write data to a text field named PLAIN_TEXT. WSIMPLE uses the string &quot;The quick brown fox jumped over the lazy dogs.&quot; for the data value. 
<table width="100%" border="1">
<tr valign="top"><td width="100%"><b>wsimple.c: Writing a Text Field</b></td></tr>
</table>
<tt><font size="2">&nbsp; DBHANDLE &nbsp;db_handle; &nbsp; /* database handle &nbsp; &nbsp; &nbsp; */<br>
 &nbsp;NOTEHANDLE note_handle; &nbsp;/* note handle &nbsp; &nbsp; &nbsp; &nbsp; */<br>
 &nbsp;STATUS &nbsp; error; &nbsp; &nbsp; /* return code from API calls */</font></tt><br>
<br>
<tt><font size="2">&nbsp; /* Write a text field named PLAIN_TEXT to the note. */</font></tt><br>
<br>
<tt><font size="2">&nbsp; if (error = NSFItemSetText ( note_handle, <br>
 &nbsp; &nbsp; &nbsp; &nbsp;&quot;PLAIN_TEXT&quot;,<br>
 &nbsp; &nbsp; &nbsp; &nbsp;&quot;The quick brown fox jumped over the lazy dogs.&quot;,<br>
 &nbsp; &nbsp; &nbsp; &nbsp;MAXWORD))<br>
 &nbsp;{</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; PrintAPIError(error);<br>
 &nbsp; &nbsp; &nbsp;NSFNoteClose (note_handle);<br>
 &nbsp; &nbsp; &nbsp;NSFDbClose (db_handle);<br>
 &nbsp; &nbsp; &nbsp;NotesTerm();</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; return(1);<br>
 &nbsp;}</font></tt><br>
<br>
This call to NSFItemSetText writes a new text field called PLAIN_TEXT. The actual text is the third argument. The fourth argument specifies the length of the text. <br>
<br>
If the fourth argument is specified as MAXWORD, the string must be a null-terminated string, and NSFItemSetText will write all the characters up to the first NULL character. Specifying the length of the string explicitly, instead of specifying MAXWORD, lets you write a string of text containing embedded NULL characters to the document.<br>
<br>
<br>
<b><font size="4" color="#000080">Writing Number Fields</font></b><br>
<br>
WSIMPLE uses the API function NSFItemSetNumber to write a field named NUMBER, of data type TYPE_NUMBER, to the document. 
<table width="100%" border="1">
<tr valign="top"><td width="100%"><b>wsimple.c: Writing a Number to a Document</b></td></tr>
</table>
<tt><font size="2">&nbsp; NOTEHANDLE note_handle; /* note handle &nbsp; &nbsp; &nbsp; &nbsp; */<br>
 &nbsp;NUMBER &nbsp; &nbsp; num_field; &nbsp; /* contents of a numeric field */<br>
 &nbsp;STATUS &nbsp; &nbsp; error; &nbsp; &nbsp; &nbsp; /* return code from API calls */</font></tt><br>
<br>
<tt><font size="2">/* Write a field named NUMBER to the note. */</font></tt><br>
<br>
<tt><font size="2">&nbsp; num_field = 125.007;</font></tt><br>
<br>
<tt><font size="2">&nbsp; if (error = NSFItemSetNumber (note_handle, &quot;NUMBER&quot;, &amp;num_field))<br>
 &nbsp;{</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; PrintAPIError(error);<br>
 &nbsp; &nbsp; &nbsp;NSFNoteClose (note_handle);<br>
 &nbsp; &nbsp; &nbsp;NSFDbClose (db_handle);<br>
 &nbsp; &nbsp; &nbsp;NotesTerm();</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; return(1);<br>
 &nbsp;}</font></tt><br>
<br>
WSIMPLE initializes the variable num_field to the value 125.007. The variable num_field is of type NUMBER, which is defined by the HCL C API for Domino and Notes to be an eight-byte double. NSFItemSetNumber requires as input a pointer to a variable of this type. <br>
<br>
<br>
<b><font size="4" color="#000080">Writing Time/Date Fields</font></b><br>
<br>
WSIMPLE use the API function NSFItemSetTime to write a time/date field named TIME_DATE to the new document. The time/date value it writes is the current time/date, obtained by calling the API function OSCurrentTIMEDATE.<br>
<br>

<table width="100%" border="1">
<tr valign="top"><td width="100%"><b>wsimple.c: Writing a Time/Date Field to a Document</b></td></tr>
</table>
<tt><font size="2">	NOTEHANDL</font></tt><tt><font size="2">E &nbsp; note_handle; &nbsp;/* note handle */<br>
	TIMEDATE &nbsp; &nbsp; timedate; &nbsp; &nbsp; /* contents of a time/date field */<br>
	STATUS &nbsp; &nbsp; &nbsp; error; &nbsp; &nbsp; &nbsp; &nbsp;/* return code from API calls */</font></tt><br>
<br>
<tt><font size="2">&nbsp; /* Get the current time/date and write it<br>
 &nbsp; &nbsp; to a field named TIME_DATE. */</font></tt><br>
<br>
<tt><font size="2">	OSCurrentTIMEDATE(&amp;timedate);</font></tt><br>
<br>
<tt><font size="2">	if (error = NSFItemSetTime (note_handle, &quot;TIME_DATE&quot;, &amp;timedate))<br>
 &nbsp; &nbsp; &nbsp;{</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; PrintAPIError(error);</font></tt><tt><font size="2"><br>
	 &nbsp; &nbsp;NSFNoteClose (note_handle);<br>
	 &nbsp; &nbsp;NSFDbClose (db_handle);<br>
	</font></tt><tt><font size="2">&nbsp; &nbsp; NotesTerm();</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; return(1);</font></tt><tt><font size="2"><br>
	}</font></tt><br>
<br>
WSIMPLE calls OSCurrentTIMEDATE to initialize the variable timedate to the current time and date. The variable timedate is of type TIMEDATE. The HCL C API for Domino and Notes defines the type TIMEDATE. NSFItemSetTime requires a pointer to a variable of type TIMEDATE to set the value.<br>
<br>
<br>
<b><font size="4" color="#000080">Writing Text-List Fields</font></b><br>
<br>
Text-list fields are multi-valued text fields. WSIMPLE uses a three step process to write a text-list field named TEXT_LIST with three values to the new document. The three text values are the strings &quot;Charles,&quot; &quot;Janet,&quot; and &quot;Chuck.&quot;<br>
<br>
To create a text-list field, use NSFItemCreateTextList, which also puts the first value in the field. Then use NSFItemAppendTextList to add additional values to the field.
<table width="100%" border="1">
<tr valign="top"><td width="100%"><b>wsimple.c: Writing a Text-List Field to a Document</b></td></tr>
</table>
<tt><font size="2">&nbsp; NOTEHANDLE note_handle; &nbsp;/* note handle &nbsp; &nbsp; &nbsp; &nbsp; */<br>
 &nbsp;STATUS &nbsp; &nbsp; error; &nbsp; &nbsp; &nbsp; &nbsp;/* return code from API calls */</font></tt><br>
<br>
<tt><font size="2">&nbsp; /* Create a text-list field and add it to the note. */<br>
 &nbsp;if (error = NSFItemCreateTextList ( note_handle, <br>
 &nbsp; &nbsp; &nbsp; &nbsp;&quot;TEXT_LIST&quot;,<br>
 &nbsp; &nbsp; &nbsp; &nbsp;&quot;Charles&quot;, <br>
 &nbsp; &nbsp; &nbsp; &nbsp;MAXWORD))<br>
 &nbsp;{</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; PrintAPIError(error);<br>
 &nbsp; &nbsp; &nbsp;NSFNoteClose (note_handle);<br>
 &nbsp; &nbsp; &nbsp;NSFDbClose (db_handle);<br>
 &nbsp; </font></tt><tt><font size="2">	NotesTerm();</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; return(1);<br>
 &nbsp;}</font></tt><br>
<br>
<tt><font size="2">&nbsp; /* Add an item to the text-list field. */<br>
 &nbsp;if (error = NSFItemAppendTextList ( note_handle, <br>
 &nbsp; &nbsp; &nbsp; &nbsp;&quot;TEXT_LIST&quot;,<br>
 &nbsp; &nbsp; &nbsp; &nbsp;&quot;Janet&quot;, <br>
 &nbsp; &nbsp; &nbsp; &nbsp;MAXWORD,<br>
 &nbsp; &nbsp; &nbsp; &nbsp;TRUE))<br>
 &nbsp;{</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; PrintAPIError(error);<br>
 &nbsp; &nbsp; &nbsp;NSFNoteClose (note_handle);<br>
 &nbsp; &nbsp; &nbsp;NSFDbClose (db_handle);<br>
 &nbsp; &nbsp; &nbsp;NotesTerm();</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; return(1);<br>
 &nbsp;}</font></tt><br>
<tt><font size="2">&nbsp; /* Add another item to the text-list field. */</font></tt><br>
<tt><font size="2">&nbsp; if (error = NSFItemAppendTextList ( note_handle, <br>
	 &nbsp; &quot;TEXT_LIST&quot;,<br>
	 &nbsp; &quot;Chuck&quot;, <br>
	 &nbsp; MAXWORD,<br>
	 &nbsp; TRUE))<br>
 &nbsp;{</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; PrintAPIError(error);</font></tt><tt><font size="2"><br>
	NSFNoteClose (note_handle);<br>
 &nbsp; &nbsp; &nbsp;NSFDbClose (db_handle);<br>
</font></tt><tt><font size="2">&nbsp; &nbsp; &nbsp; NotesTerm();</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; return(1);<br>
 &nbsp;}</font></tt><br>
<br>
In this example, NSFItemCreateTextList creates the text-list field TEXT_LIST with the initial entry &quot;Charles.&quot; Then NSFItemAppendTextList adds the string &quot;Janet&quot; to the same field. At this point there are two entries in the field TEXT_LIST. The second call to NSFItemAppendTextList appends the third value, &quot;Chuck,&quot; to the text list.<br>
<br>
After writing these fields to the document, WSIMPLE updates the note as explained above, closes the note, closes the database, and returns.<br>
<br>
<b><font size="5" color="#000080">Special Field - Do Not Create a Replication or Save Conflict </font></b><br>
If a note has a $ConflictAction field with a value of &quot;2&quot; in it, the Replicator will NOT create a replication conflict document.  If you do not want a note to replicate, <font size="2"> </font>create an item of TYPE_TEXT and name it $ConflictAction.  Set its value to &quot;2&quot;.
---
