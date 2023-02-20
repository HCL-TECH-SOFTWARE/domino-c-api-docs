##### Chapter 5-3
##### Reading Documents

To read documents, first find the document or documents you want in the database and then read fields from the document.<br>
<br>
<br>
<b><font size="5" color="#000080">Finding Documents</font></b><br>
<br>
<b><font size="4" color="#000080">NSFSearch and NIFReadEntries</font></b><br>
<br>
The HCL C API for Domino and Notes provides two ways to find documents in databases: NSFSearch and NIFReadEntries. This chapter explains how to find documents using NSFSearch. It also explains how to open the documents and how to read fields from documents. The &quot;Writing Documents&quot; chapter in this guide shows how to create new notes and write fields. The &quot;Views&quot; section explains how to use NIFReadEntries.<br>
<br>
We use the sample program RSIMPLE (short for ReadSIMPLE) to explain how to use NSFSearch and how to read fields. RSIMPLE resides in the directory samples\basic\rsimple. Load rsimple.c in an editor or print it so you can refer to it while you read this chapter.<br>
<br>
NSFSearch is a powerful routine for finding database notes, including documents, which are a special class of note called NOTE_CLASS_DOCUMENT. However, you can use NSFSearch to find any class of note in a database, including design notes. You can also use NSFSearch to find databases in directories or databases on a server. For information about finding databases with NSFSearch, see the &quot;Server and Database Listings&quot; chapter. <br>
<br>
 <br>
<b><font size="4" color="#000080">Using NSFSearch to Find Documents</font></b><br>
<br>
NSFSearch searches the specified database sequentially. For each note found that matches the selection criteria, the action routine you specify is called to process the note.<br>
<br>
Your program must specify the selection criteria and provide a subroutine -- called an &quot;action&quot; or &quot;call-back&quot; routine -- capable of processing notes that match the selection criteria. Specify this action routine when you call NSFSearch.<br>
<br>
NOTE: Your program does not call your action routine directly. Instead, your program calls NSFSearch, and NSFSearch calls the action routine.
<ul>
<ul><br>
</ul>
</ul>
<b><font size="4" color="#000080">NSFSearch Parameters</font></b><br>
<br>
The <i>Reference</i> contains a detailed description of NSFSearch. However, to facilitate this discussion, we reproduce the function prototype for NSFSearch below.
<table width="100%" border="1">
<tr valign="top"><td width="100%"><b>NSFSearch: Syntax</b></td></tr>
</table>
<tt><font size="2">STATUS LNPUBLIC NSFSearch (</font></tt><br>
<tt><font size="2">				DBHANDLE hDB,<br>
				FORMULAHANDLE hFormula,<br>
				char far *ViewTitle,<br>
				WORD SearchFlags,<br>
				WORD NoteClassMask,<br>
				TIMEDATE far *Since,<br>
				NSFSEARCHPROC action_routine,<br>
				void far *EnumRoutineParameter,<br>
				TIMEDATE far *retUntil);</font></tt><br>
<br>
<br>
The first argument (input) to NSFSearch is the handle to the database that will be searched. <br>
<br>
The next five arguments to NSFSearch specify the selection criteria.<br>
<br>
The second argument (input) to NSFSearch is an optional formula argument, which can greatly improve program efficiency when you only want to process a subset of the notes in the database. Selection formulas consist of the same Notes @ functions, field names, and logical operators as view selection formulas and conform to the same syntax. Any formula that works in view selection will work in NSFSearch, and you may omit the keyword SELECT. Specifying the formula argument as NULLHANDLE is the same as specifying @All.<br>
<br>
This selection formula is initially expressed as a character string. Before calling NSFSearch, you must compile the character string using NSFFormulaCompile, which yields a formula handle. Since @All selects all documents in the database, RSIMPLE could have been implemented without NSFFormulaCompile by specifying NULLHANDLE as the second parameter to NSFSearch. RSIMPLE uses NSFFormulaCompile to demonstrate how to compile selection formulas to get handles.<br>
<br>
The fifth argument (input) to NSFSearch is a mask of &quot;note classes&quot; that restricts the search to basic classes of notes, such as &quot;documents,&quot; &quot;views,&quot; or &quot;forms.&quot; To find documents, specify NOTE_CLASS_DOCUMENT.<br>
<br>
You can use the sixth argument (input) to NSFSearch to limit the search to only those notes modified since the given time/date, thus allowing you to see only the newly-updated notes in a database. The corresponding ninth argument (output) returns the &quot;end time/date&quot; so you can later perform another incremental search.<br>
<br>
The search can be abnormally terminated if the supplied action routine returns an error. The error is returned to the caller of NSFSearch.<br>
<br>
<br>
<b><font size="4" color="#000080">Example Using NSFSearch</font></b><br>
<br>
The MAIN_PROC routine of rsimple.c (below) opens the Domino database, prepares the selection formula, and calls NSFSearch. The action routine in RSIMPLE performs all the per-document work. Once the search is complete, the program cleans up and returns.
<table width="100%" border="1">
<tr valign="top"><td width="100%"><b>rsimple.c: Finding all Documents in a Database</b></td></tr>
</table>
<br>
<tt><font size="2">MAIN_PROC<br>
{</font></tt><br>
<tt><font size="2">&nbsp; char &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; *db_filename; &nbsp; /* pathname of source database */<br>
 &nbsp;DBHANDLE &nbsp; &nbsp; &nbsp; db_handle; &nbsp; &nbsp; &nbsp;/* handle of source database */<br>
 &nbsp;char &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; *formula; &nbsp; &nbsp; &nbsp; /* a character text selection formula */<br>
 &nbsp;FORMULAHANDLE &nbsp;formula_handle; /* a compiled selection formula */<br>
 &nbsp;WORD &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; wdc; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* a word we don't care about */</font></tt><br>
<tt><font size="2">&nbsp; STATUS &nbsp; &nbsp; &nbsp; &nbsp; error; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* return status from API calls */</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp;db_filename = database_name;</font></tt><br>
<tt><font size="2">&nbsp; &nbsp;ProcessArgs(argc, argv, db_filename);</font></tt><br>
<tt><font size="2">&nbsp; &nbsp;OS_INITIALIZE(error);</font></tt><br>
<tt><font size="2">&nbsp; &nbsp;if (error)</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp;NOTES_INIT_ERROR;</font></tt><br>
<br>
<tt><font size="2">	if (error = NSFDbOpen (db_filename, &amp;db_handle))<br>
		API_RETURN (ERR(error));</font></tt><br>
<br>
<tt><font size="2">/* Write a character text selection formula. */</font></tt><br>
<br>
<tt><font size="2">	formula = &quot;@All&quot;; </font></tt><br>
<br>
<tt><font size="2">/* Compile the selection formula. */</font></tt><br>
<br>
<tt><font size="2">	if (error = NSFFormulaCompile (<br>
		NULL,			/* name of formula (none) */<br>
		0,			/* length of name */<br>
		formula,		/* the character text formula */<br>
		strlen(formula),	/* length of character text formula */<br>
		&amp;formula_handle,	/* handle to compiled formula */<br>
		&amp;wdc,			/* compiled formula length (don't care) */<br>
		&amp;wdc, 			/* return code from compile (don't care) */<br>
		&amp;wdc, &amp;wdc, &amp;wdc, &amp;wdc)) /* compile error info (don't care) */<br>
		<br>
		{<br>
		NSFDbClose (db_handle);<br>
		API_RETURN (ERR(error));<br>
		}</font></tt><br>
<br>
<tt><font size="2">/* Call NSFSearch to find the notes that match the selection criteria. For <br>
each note found, the routine print_fields is called. (If you always want<br>
to find all the documents in the database, you can set the 2nd argument<br>
to NULLHANDLE and eliminate the formula compilation.) */</font></tt><br>
<br>
<tt><font size="2">	if (error = NSFSearch (<br>
		db_handle,		/* database handle */<br>
		formula_handle,	/* selection formula */<br>
		NULL,			/* title of view in selection formula */<br>
		0,			/* search flags */<br>
		NOTE_CLASS_DOCUMENT,	/* note class to find */<br>
		NULL,			/* starting date (unused) */<br>
		print_fields,		/* call for each note found */<br>
		&amp;db_handle,		/* argument to print_fields */<br>
		NULL))			/* returned ending date (unused) */</font></tt><br>
<br>
<tt><font size="2">		{<br>
		NSFDbClose (db_handle);<br>
		API_RETURN (ERR(error));<br>
		}</font></tt><br>
<br>
<tt><font size="2">/* Free the memory allocated to the compiled formula. */</font></tt><br>
<br>
<tt><font size="2">	OSMemFree (formula_handle);</font></tt><br>
<br>
<tt><font size="2">/* Close the database. */</font></tt><br>
<br>
<tt><font size="2">	if (error = NSFDbClose (db_handle))<br>
		API_RETURN (ERR(error));</font></tt><br>
<br>
<tt><font size="2">/* End of main routine. */</font></tt><br>
<br>
<tt><font size="2">	API_RETURN (NOERROR);<br>
}</font></tt><br>
<br>
RSIMPLE calls NSFSearch only once to find all the documents in the database. By specifying the selection formula @All, the note class NOTE_CLASS_DOCUMENT, and no starting date, the action routine print_fields is called once for every document in the database.<br>
<br>
<br>
<b><font size="4" color="#000080">The Action Routine</font></b><br>
<br>
The seventh parameter to NSFSearch is the name of the action routine (in this case, print_fields). The action routine may be given any name, but it must conform to the calling syntax of action routines as specified in the <i>Reference</i> for NSFSearch. <br>
<br>
The eighth parameter to NSFSearch is an optional pass-through argument that is passed to the action routine when it is called. This pass-through argument allows NotesMain to provide context to the action routine, even though NotesMain does not call the action routine directly. <br>
<br>
The action, or call-back, routine specified to NSFSearch must conform to the following calling syntax:<br>

<ul>STATUS (LNCALLBACKPTR action_routine)<br>
          (void far * action_param,<br>
           SEARCH_MATCH far * search_match,<br>
           ITEM_TABLE far * summary_buffer)</ul>
<br>
NSFSearch calls the action routine once for every note it finds that matches the search criteria. When NSFSearch calls the action routine, it specifies, in the first parameter to the action routine, the pass-through parameter that was specified as the eighth parameter to NSFSearch.<br>
<br>
The second and third parameters to the action routine (search_match and summary_buffer) provide information the action routine needs to process the document. search_match contains assorted information about the found note, including the Note ID. summary_buffer contains the values of some of the fields in the note.<br>
<br>
Under Windows, the action routine must be exported via an EXPORTS statement in a .def file so that it may be called from Domino or Notes.<br>
<br>
Under Windows, you must create a procedure instance for the action routine before calling NSFSearch. Assign the address returned from MakeProcInstance to a FARPROC pointer and specify that value as the seventh argument to NSFSearch. When the call to NSFSearch returns, you must free the procedure instance associated with the FARPROC pointer. <br>
<br>
The sequential nature of NSFSearch means that NSFSearch finds notes in no particular order from the point of view of the HCL C API for Domino and Notes or the user. In fact, it finds notes in the order they appear in the .nsf file, but Domino or Notes may store newer notes closer to the beginning of an .nsf file than older notes if file space becomes available there. Your C API program must not assume that notes will be delivered to the action routine in any predictable order.<br>
<br>
NOTE: If the search is not time-constrained (that is, if the &quot;since&quot; argument is NULL or specifies the TIMEDATE_WILDCARD ANYDAY/ALLDAY), NSFSearch may find a given note more than once during the same search. If a non-time-constrained search passes a certain note to the action routine, and that note is subsequently updated, NSFSearch may find the note again and pass it to the action routine a second time during the same search. This may happen if Domino or Notes relocates the updated note to a position farther down in the file. <br>
<br>
If your algorithm requires that you process each note only once, use time-constrained searches. Alternatively, build an ID table as you search, avoid updating notes in the action routine, and process the ID table after the search completes. ID tables are guaranteed not to contain a given note ID more than once. In the action routine, add the ID of each note found to the ID table. When the search is complete, process each ID in the table. <br>
<br>
<br>
<b><font size="4" color="#000080">Reading Documents Using the Action Routine</font></b><br>
<br>
In RSIMPLE, the print_fields action routine reads and prints four fields in the document. To access the fields, print_fields uses NSFNoteOpen to open the document in the database. NSFNoteOpen requires a NOTEID as input to specify the note. The print_fields routine gets the NOTEID from the second parameter, the SEARCH_MATCH structure.<br>
<br>
The print_fields routine checks the SE_FMATCH flag in the SEARCH_MATCH structure, gets the note ID and prints it, and then passes the note ID to NSFNoteOpen. NSFNoteOpen returns a handle that is used to access fields in the note and to close the note.<br>
<br>

<table width="100%" border="1">
<tr valign="top"><td width="100%"><b>rsimple.c: Opening a Note</b></td></tr>
</table>

<ul><tt><font size="2">STATUS LNCALLBACK print_fields	<br>
			(void far *db_handle, <br>
			SEARCH_MATCH far *search_info, <br>
			ITEM_TABLE far *summary_info)<br>
{</font></tt><br>
<tt><font size="2">	NOTEHANDLE	note_handle;<br>
	STATUS		error;</font></tt><br>
<br>
<br>
<tt><font size="2">/* Skip this note if it does not really match the search criteria (it is<br>
now deleted or modified). This is not necessary for full searches,<br>
but is shown here in case a starting date was used in the search. */</font></tt><br>
<br>
<tt><font size="2">	</font></tt><tt><font size="2">/* if (search_info-&gt;MatchesFormula != SE_FMATCH) &nbsp; V3 */<br>
 &nbsp;if (!(search_info-&gt;SERetFlags &amp; SE_FMATCH)) &nbsp; /* V4 */</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; return (NOERROR);</font></tt><br>
        <br>
<tt><font size="2">/* Print the note ID. */</font></tt><br>
<br>
<tt><font size="2">	printf (&quot;\nNote ID is: %lX.\n&quot;, search_info-&gt;ID.NoteID);</font></tt><br>
<br>
<tt><font size="2">/* Open the note. */</font></tt><br>
<br>
<tt><font size="2">	if (error = NSFNoteOpen (<br>
			*(DBHANDLE far *)db_handle,	/* database handle */<br>
			search_info-&gt;ID.NoteID,	/* note ID */<br>
			0,			/* open flags */<br>
			&amp;note_handle))		/* note handle (return) */<br>
		<br>
		return (ERR(error));</font></tt><br>
<br>
<tt><font size="2">&nbsp; </font></tt><tt>.</tt><tt><font size="2"><br>
 &nbsp;</font></tt><tt>.</tt><tt><font size="2">&nbsp;Operations on Documents<br>
 &nbsp;</font></tt><tt>.</tt><br>
<br>
<tt><font size="2">/* Close the note. */</font></tt><br>
<br>
<tt><font size="2">	if (error = NSFNoteClose (note_handle))<br>
		return (ERR(error));</font></tt><br>
<br>
<tt><font size="2">/* End of subroutine. */</font></tt><br>
<br>
<tt><font size="2">&nbsp; return (NOERROR);</font></tt><br>
<br>
<tt><font size="2">}</font></tt><br>
</ul>
The action routine should always check the SERetFlags member of the SEARCH_MATCH structure and only process the note if MatchesFormula equals SE_FMATCH. On time-delimited searches, NSFSearch may call the action routine on a document that does not match the selection criteria. If it does, SERetFlags will not be set to SE_FMATCH. In this case, the action routine should not process the note; instead, it should simply return NOERROR.<br>
<br>
<br>
<b><font size="5" color="#000080">Reading Documents</font></b><br>
<br>
RSIMPLE calls NSFNoteOpen to open the note before accessing it. NSFNoteOpen yields a note handle. RSIMPLE needs this handle when it calls C API functions such as NSFItemGetText to read fields in the document.<br>
<br>
<br>
<b><font size="4" color="#000080">Reading Fields in a Document</font></b><br>
<br>
A document may contain any number of fields. Each field has a Field Name, a Data Type, a Data Length, a Data Value, and a flag word.  Many different data types are supported. RSIMPLE demonstrates reading four basic data types: text, number, time/date, and text list.<br>
<br>
The C API provides specific functions, such as NSFItemGetText, to read fields of each of the four basic data types. The C API also provides general functions, such as NSFItemInfo, to read any field of any data type. Generally, all functions that read fields in notes require as input the note handle and the name of the field. They return the field values in different ways, depending on the data type.<br>
<br>
<br>
<b><font size="4" color="#000080">Reading Text Fields</font></b><br>
<br>
RSIMPLE uses a two-step process to read a text field named PLAIN_TEXT. First it asks if the field is present in the document. If it is present, RSIMPLE gets the value and prints it out. Otherwise, it prints &quot;PLAIN_TEXT field not found.&quot;
<table width="100%" border="1">
<tr valign="top"><td width="100%"><b>rsimple.c: Reading a Text Field</b></td></tr>
</table>
<tt><font size="2">&nbsp; NOTEHANDLE note_handle;<br>
 &nbsp;BOOL &nbsp; &nbsp; &nbsp; field_found;<br>
 &nbsp;char &nbsp; &nbsp; &nbsp; field_text[500];<br>
 &nbsp;STATUS &nbsp; &nbsp; error;</font></tt><br>
<br>
<tt><font size="2">&nbsp; /* Look for the PLAIN_TEXT field within this note. */<br>
 &nbsp;field_found = NSFItemIsPresent (note_handle,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&quot;PLAIN_TEXT&quot;,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;strlen (&quot;PLAIN_TEXT&quot;));</font></tt><br>
<br>
<tt><font size="2">&nbsp; /* If PLAIN_TEXT field is there, get contents and print it.<br>
 &nbsp; If the PLAIN_TEXT field is not there, print a message.*/<br>
 &nbsp;if (field_found)<br>
 &nbsp; {<br>
 &nbsp; field_len = NSFItemGetText (note_handle, <br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&quot;PLAIN_TEXT&quot;,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;field_text,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;sizeof (field_text));<br>
 &nbsp; printf (&quot;PLAIN_TEXT field is: %s\n&quot;, field_text);<br>
 &nbsp; }<br>
 &nbsp;else<br>
 &nbsp; printf (&quot;PLAIN_TEXT field not found.\n&quot;);</font></tt><br>
<br>
NSFItemIsPresent returns a boolean value that is TRUE if the field is in the document. RSIMPLE stores this return value in the variable field_found, then calls NSFItemGetText to get the contents of the field named PLAIN_TEXT and store it in the variable field_text as a NULL-terminated string, suitable for print-out using printf.<br>
<br>
<br>
<b><font size="4" color="#000080">Reading Number Fields</font></b><br>
<br>
RSIMPLE uses the C API function NSFItemGetNumber to get a field named NUMBER that is of data type TYPE_NUMBER.
<table width="100%" border="1">
<tr valign="top"><td width="100%"><b>rsimple.c: Reading a Number from a Document</b></td></tr>
</table>
<tt><font size="2">&nbsp; NOTEHANDLE note_handle;<br>
 &nbsp;BOOL &nbsp; &nbsp; &nbsp; field_found;<br>
 &nbsp;NUMBER &nbsp; &nbsp; number_field;<br>
 &nbsp;STATUS &nbsp; &nbsp; error;</font></tt><br>
<br>
<tt><font size="2">&nbsp; /* Look for (and get if it's there) the NUMBER field within<br>
 &nbsp; this note. */<br>
 &nbsp;field_found = NSFItemGetNumber (note_handle, <br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&quot;NUMBER&quot;,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&amp;number_field);</font></tt><br>

<ul><tt><font size="2">/* If the NUMBER field was found, print it. */</font></tt><br>
<br>
<tt><font size="2">	if (field_found)<br>
		printf (&quot;NUMBER field is: %g\n&quot;, number_field);</font></tt><br>
<br>
<tt><font size="2">/* If the NUMBER field was not found, print a message. */</font></tt><br>
<br>
<tt><font size="2">	else <br>
		printf (&quot;NUMBER field not found.\n&quot;); <br>
	</font></tt></ul>
<br>
NSFItemGetNumber returns the value of the field to the variable number_field. The function does not require NSFItemIsPresent because it returns a boolean indicating whether NUMBER is in the document.<br>
<br>
<br>
<b><font size="4" color="#000080">Reading Time/Date Fields</font></b><br>
 <br>
RSIMPLE uses a two-step process to read a time/date field named TIME_DATE. First it asks if the field is present in the document. If it is there, RSIMPLE converts the value to text and prints it out. Otherwise, it prints &quot;TIME_DATE field not found.&quot;
<table width="100%" border="1">
<tr valign="top"><td width="100%"><b>rsimple.c: Reading a Time/Date Field from a Document</b></td></tr>
</table>
<tt><font size="2">&nbsp; NOTEHANDLE note_handle;<br>
 &nbsp;BOOL &nbsp; &nbsp; &nbsp; field_found;</font></tt><br>
<br>
<tt><font size="2">&nbsp; /* Look for the TIME_DATE field within this note. */<br>
 &nbsp;field_found = NSFItemIsPresent (note_handle,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&quot;TIME_DATE&quot;,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;strlen (&quot;TIME_DATE&quot;));</font></tt><br>
<br>
<tt><font size="2">&nbsp; /* If the TIME_DATE field is there, get the contents of the<br>
 &nbsp; field as a character string and print it out.<br>
 &nbsp; If the TIME_DATE field is not there, print a message.<br>
 &nbsp;*/<br>
 &nbsp;if (field_found)<br>
 &nbsp; {<br>
 &nbsp; field_len = NSFItemConvertToText (note_handle, <br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;TIME_DATE&quot;,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; field_text,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; sizeof (field_text),<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ';'); /* multi-value separator */</font></tt><br>
<tt><font size="2">	 printf (&quot;TIME_DATE field is: %s\n&quot;, field_text);</font></tt><br>
<br>
<tt><font size="2">	 }</font></tt><br>
<br>
<tt><font size="2">/* If the TIME_DATE field is not there, print a message. */</font></tt><br>
<br>
<tt><font size="2">	else<br>
		printf (&quot;TIME_DATE field not found.\n&quot;);</font></tt><br>
<br>
The return value from NSFItemIsPresent is stored in the variable field_found. If field_found is TRUE, RSIMPLE calls NSFItemConvertToText to convert the contents of the field named PLAIN_TEXT to text format and store it in the variable field_text as a NULL-terminated string, suitable for print-out using printf. <br>
<br>
NSFItemConvertToText returns the actual length of the text string. The caller must specify the size of the buffer where the converted text will be stored. The last argument is the separator that Notes should use to separate any multi-valued<font color="#FF0000"> </font>fields. A semicolon is the default value for the last argument; if you enter zero, the result is the same.<br>
<br>
<br>
<b><font size="4" color="#000080">Reading Text-List Fields</font></b><br>
<br>
A text-list field is a multi-valued text field.<br>
<br>
RSIMPLE uses a three-step process to read the last value of a text-list field named TEXT_LIST. First it asks if the field is present. If it is, RSIMPLE gets the number of values in the text-list, gets the value of the last item on the list, and prints it out. If the field is not present, RSIMPLE prints &quot;TEXT_LIST field not found.&quot;
<table width="100%" border="1">
<tr valign="top"><td width="100%"><b>rsimple.c: Reading a Text-List Field from a Document</b></td></tr>
</table>
<tt><font size="2">&nbsp; NOTEHANDLE note_handle; &nbsp; &nbsp; /* note handle &nbsp; &nbsp; &nbsp; &nbsp; */<br>
 &nbsp;BOOL &nbsp; &nbsp; &nbsp; field_found; &nbsp; &nbsp; /* indicate field presence &nbsp; */<br>
 &nbsp;WORD &nbsp; &nbsp; &nbsp; field_len; &nbsp; &nbsp; &nbsp; /* actual length of field &nbsp; */<br>
 &nbsp;WORD &nbsp; &nbsp; &nbsp; list_entries; &nbsp; &nbsp;/* count of entries &nbsp; &nbsp; &nbsp;*/<br>
 &nbsp;char &nbsp; &nbsp; &nbsp; field_text[500]; /* buffer for result &nbsp; &nbsp; &nbsp;*/<br>
 &nbsp;STATUS &nbsp; &nbsp; &nbsp;error; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* return code from API calls */</font></tt><br>
<br>
<tt><font size="2">&nbsp; /* Look for the TEXT_LIST field within this note. */<br>
 &nbsp;field_found = NSFItemIsPresent ( note_handle,<br>
 &nbsp; &nbsp; &nbsp; &nbsp;&quot;TEXT_LIST&quot;,<br>
 &nbsp; &nbsp; &nbsp; &nbsp;strlen (&quot;TEXT_LIST&quot;));</font></tt><br>
<br>
<tt><font size="2">&nbsp; /* If the TEXT_LIST field is present, do the next few<br>
 &nbsp; &nbsp; sections of code.<br>
 &nbsp; If it is not there, print a message. */<br>
 &nbsp;if (field_found)<br>
 &nbsp; { <br>
 &nbsp; /* Find the number of entries in TEXT_LIST */<br>
 &nbsp; list_entries = NSFItemGetTextListEntries(note_handle,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&quot;TEXT_LIST&quot;);</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp;/* Get the last entry in TEXT_LIST.<br>
 &nbsp; &nbsp; The fields are numbered from 0 to n-1.<br>
 &nbsp; &nbsp; So we subtract one from the number returned above. */</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp;field_len = NSFItemGetTextListEntry ( note_handle,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;TEXT_LIST&quot;,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; list_entries - 1, /* field to get*/<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; field_text,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; sizeof (field_text) -1 );</font></tt>
<ul><tt><font size="2">	/* Print out the last entry in TEXT_LIST. */</font></tt><br>
<br>
<tt><font size="2">	 printf (&quot;The last entry in TEXT_LIST is: %s\n&quot;, field_text);</font></tt><br>
<br>
<tt><font size="2">	} </font></tt><br>
<br>
<tt><font size="2">/* If the TEXT_LIST field is not there, print a message. */</font></tt><br>
<br>
<tt><font size="2">	else<br>
		printf (&quot;TEXT_LIST field not found.\n&quot;);</font></tt></ul>
<br>
<br>
The return value from NSFItemIsPresent is stored in the variable field_found. If field_found is TRUE, RSIMPLE calls NSFItemGetTextListEntries to get the number of entries (values) in the list. It stores this number in the variable list_entries.<br>
<br>
To get the last entry on the list, RSIMPLE calls NSFItemGetTextListEntry. NSFItemGetTextListEntry requires as input the ordinal position of the desired text list entry. This position is zero-based (that is, the first entry is number 0, the second is number 1, the third 2, and so on). To get the last entry, RSIMPLE specifies the number of entries minus one.<br>
<br>
NSFItemGetTextListEntry stores a NULL-terminated string in field_text, suitable for print-out using printf. <br>
<br>
NSFItemGetTextListEntry returns the actual length of the text string. The caller must specify the size of the storage buffer for the text entry.
---
