##### Chapter 6-4
##### Searching a View Index 

<b><font size="5" color="#000080">Views with One Text Key</font></b><br>
<br>
This section examines TEXTKEY, an example program that finds documents in a collection based on the documents' primary sort key. This is a useful operation because it allows you to build a collection once and use it repeatedly to find documents with different keys.<br>
<br>
<br>
<b><font size="4" color="#000080">NIFFindByName</font></b><br>
<br>
TEXTKEY uses the same functions and data types as the previous sample program and an additional function, NIFFindByName. NIFFindByName searches a collection for the first note whose primary sort key matches a given  string. The function sets a COLLECTIONPOSITION structure to indicate the location of this note in the collection. The function also returns the number of notes that have this key. <br>
<br>
<br>
<b><font size="4" color="#000080">Restrictions of NIFFindByName</font></b><br>
<br>
NIFFindByName is subject to the following restrictions:
<ul>
<ul></ul>

<li type="disc">You can search for only those notes whose primary key is equal to or begins with a certain string. You cannot find notes whose sort key simply contains a string. Use the FIND_PARTIAL match rule to find a string at the beginning of the sort key.
<li type="disc">You can search for matches on the primary key only. You cannot use multiple keys at the same time or search alternate keys.
<li type="disc">The primary key must be a string. You cannot search key fields that are numeric or time/date.</ul>
<br>
If you need more extensive search capabilities, use the C API function NIFFindByKey, discussed later in this chapter. For details about NIFFindByKey, see the <i>Reference.</i><br>
<br>
<br>
<b><font size="4" color="#000080">The TEXTKEY Sample Program</font></b><br>
<br>
The sample program TEXTKEY is invoked with three command line arguments: the name of the database, the name of the view to search, and the text string comprising the primary key to search on. TEXTKEY initially opens the database, finds the note ID of the view, and opens the collection as in previous examples.  It then looks for notes that have the given primary sort key.<br>
<br>
NOTE: For the purpose of this discussion, assume that TEXTKEY is searching for all notes in the specified view that have &quot;SMITH, NANCY&quot; as their primary key.
<table width="100%" border="1">
<tr valign="top"><td width="100%"><b>Example: Find notes in a view by primary TEXT key in TEXTKEY</b></td></tr>
</table>
<br>
<tt><font size="2">&nbsp;char &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; *text_key; &nbsp; /* key to search for in view */<br>
 DBHANDLE &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; db_handle; &nbsp; /* handle of the database */<br>
 HCOLLECTION &nbsp; &nbsp; &nbsp; &nbsp;coll_handle; /* collection handle */<br>
 COLLECTIONPOSITION coll_pos; &nbsp; &nbsp;/* position within collection */<br>
 DWORD &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;match_size; &nbsp;/* number of notes matching key */<br>
	</font></tt><br>
<tt><font size="2">/*</font></tt><br>
<tt><font size="2">&nbsp;Look for notes that have the given primary sort key (which must be of<br>
type text). We get back a COLLECTIONPOSITION structure describing where the <br>
first such note is in the collection and a count of how many such notes <br>
there are. Check the return code for &quot;not found&quot; versus a real error.</font></tt><br>
<tt><font size="2">&nbsp;*/</font></tt><br>
<br>
<tt><font size="2">&nbsp;error = NIFFindByName (<br>
 &nbsp; &nbsp; &nbsp; coll_handle, &nbsp; &nbsp; /* collection to look in */<br>
 &nbsp; &nbsp; &nbsp; text_key, &nbsp; &nbsp; &nbsp; /* string to match on */<br>
 &nbsp; &nbsp; &nbsp; FIND_CASE_INSENSITIVE,/* match rules */<br>
 &nbsp; &nbsp; &nbsp; &amp;coll_pos, &nbsp; &nbsp; &nbsp;/* where match begins (return) */<br>
 &nbsp; &nbsp; &nbsp; &amp;match_size); &nbsp; &nbsp; /* how many match (return) */</font></tt><br>
<br>
<tt><font size="2">&nbsp;if (ERR(error) == ERR_NOT_FOUND) <br>
 {<br>
 &nbsp; printf (&quot;\nKey not found in the collection.\n&quot;);<br>
 &nbsp; NIFCloseCollection (coll_handle);<br>
 &nbsp; NSFDbClose (db_handle);<br>
 &nbsp; API_RETURN (NOERROR);<br>
 }<br>
	<br>
 if (error)<br>
 {<br>
 &nbsp; NIFCloseCollection (coll_handle);<br>
 &nbsp; NSFDbClose (db_handle);<br>
 &nbsp; API_RETURN (ERR(error));<br>
 }</font></tt><br>
<br>
<br>
This code fragment shows the C API function NIFFindByName, which uses the sorting order of a view to find specific entries in the collection. This function allows you to find documents whose primary sort key for the view begins with a specified string. <br>
<br>
The first argument (input) to NIFFindByName is the handle of the collection to search. The second argument (input) is the string to look for in the primary key. The third argument (input) contains the matching rules to be used during the search. The fourth argument (output) is a COLLECTIONPOSITION that points to the first place in the collection where the string is found. The fifth argument (output) is the number of matches found.<br>
<br>
The example code searches the primary key of the collection for the string &quot;SMITH, NANCY.&quot; The match rules specify that the searching is to be case-insensitive. When the first &quot;SMITH, NANCY&quot; is found in the primary sort key of the collection, the COLLECTIONPOSITION structure is set to point to this entry. The total number of entries whose primary key begins with &quot;SMITH, NANCY&quot; is returned in the fifth argument.
<ul>
<ul>
<table width="100%" border="1">
<tr valign="top"><td width="100%"><b>Example: Reading Collection Entries That Match the Search Criteria in TEXTKEY</b></td></tr>
</table>
</ul>
</ul>
<tt>&nbsp;DWORD &nbsp; notes_found; &nbsp; &nbsp; &nbsp; &nbsp;/* number of notes found */<br>
 DWORD &nbsp; match_size; &nbsp; &nbsp; &nbsp; &nbsp; /* number of notes matching key */</tt><br>
<tt>&nbsp;DWORD &nbsp; note_count = 0; &nbsp; &nbsp; /* ordinal number of the note */</tt><tt><font size="2">&nbsp;</font></tt><br>
<tt><font size="2">&nbsp;BOOL &nbsp; &nbsp;FirstTime = TRUE; &nbsp; /* used in NIFReadEntries loop */</font></tt><br>
<tt><font size="2">&nbsp;HCOLLECTION &nbsp; &nbsp; &nbsp; &nbsp;coll_handle; &nbsp;/* collection handle */<br>
 COLLECTIONPOSITION coll_pos; &nbsp; &nbsp; /* position within collection */<br>
 </font></tt><br>
<tt><font size="2">/* Get a buffer of all the note IDs that have this key. */</font></tt><br>
<br>
<tt><font size="2">&nbsp;if (error = NIFReadEntries(<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;coll_handle, &nbsp; &nbsp; &nbsp;/* handle to this collection */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&amp;coll_pos, &nbsp; &nbsp; &nbsp; &nbsp;/* where to start in collection */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;FirstTime ? NAVIGATE_CURRENT : NAVIGATE_NEXT,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* order to use when skipping */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;FirstTime ? 0L : 1L, /* number to skip */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;NAVIGATE_NEXT, &nbsp; &nbsp;/* order to use when reading */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;match_size - note_count, &nbsp; &nbsp; &nbsp; </font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; /* max number to read */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;READ_MASK_NOTEID, /* info we want */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&amp;buffer_handle, &nbsp; /* handle to info (return)	*/<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;NULL, &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; /* length of buffer (return) */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;NULL, &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; /* entries skipped (return) */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&amp;notes_found, &nbsp; &nbsp; /* entries read (return) */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&amp;signal_flag)) &nbsp; &nbsp;/* signal and share warnings (return) */</font></tt><br>
<br>
<tt><font size="2">&nbsp;{<br>
 &nbsp; &nbsp; NIFCloseCollection (coll_handle);<br>
 &nbsp; &nbsp; NSFDbClose (db_handle);<br>
 &nbsp; &nbsp; API_RETURN (ERR(error));<br>
 }</font></tt><br>
<br>
<tt><font size="2">/* Check to make sure there was a buffer of information returned.<br>
(This is just for safety. We know that some notes matched the search<br>
key.) */ </font></tt><br>
<br>
<tt><font size="2">&nbsp;if (buffer_handle == NULLHANDLE)<br>
 {<br>
 &nbsp; &nbsp; NIFCloseCollection (coll_handle);<br>
 &nbsp; &nbsp; NSFDbClose (db_handle);<br>
 &nbsp; &nbsp; printf (&quot;\nEmpty buffer returned by NIFReadEntries.\n&quot;);<br>
 &nbsp; &nbsp; API_RETURN (NOERROR);<br>
 }</font></tt><br>
<br>
<tt><font size="2">/* Lock down (freeze the location) of the buffer of notes IDs. Cast<br>
the resulting pointer to the type we need. */</font></tt><br>
<br>
<tt><font size="2">&nbsp;id_list = (NOTEID *) OSLockObject (buffer_handle);</font></tt><br>
<br>
<tt><font size="2">/* Print out the list of note IDs found by this search. */</font></tt><br>
<br>
<tt><font size="2">&nbsp;printf (&quot;\n&quot;);<br>
 for (i=0; i&lt;notes_found; i++)<br>
 &nbsp; &nbsp; printf (&quot;Note count is %lu. \t Note ID is: %lX\n&quot;, <br>
	 &nbsp; &nbsp; &nbsp; &nbsp; ++note_count, id_list[i]);</font></tt><br>
<br>
<br>
TEXTKEY calls NIFReadEntries to retrieve the IDs of the notes found by the search. The program passes to NIFReadEntries the COLLECTIONPOSITION found by NIFFindByName. When called for the first time, NIFReadEntries skips no notes during its skipping phase. Therefore, during the reading phase, NIFReadEntries starts reading at the first note that has<font color="#FF0000"> </font>&quot;SMITH, NANCY&quot; as its key. <br>
<br>
The program also passes to NIFReadEntries the number of notes that have &quot;SMITH, NANCY&quot; as their key. NIFReadEntries then reads exactly this number of notes. If the program did not cut off the reading phase in this manner, NIFReadEntries would return information about all the notes following the first &quot;SMITH, NANCY.&quot;<br>
<br>
NIFReadEntries returns a handle to a buffer containing a list of the note IDs it found. If the handle is invalid, the code cleans up and exits with an error. Otherwise, it locks the buffer and retrieves the note IDs one by one.<br>
<br>
If there are more notes to be read, NIFReadEntries is called again. This time, the function skips the first entry since it was already read in the previous call.<br>
<br>
<br>
<b><font size="5" color="#000080">Views with Multiple Keys</font></b><br>
<br>
This section examines TWOKEY, an example program that finds documents in a view based on two different search keys. Besides calling most of the same C API functions as TEXTKEY, TWOKEY also calls the function NIFFindByKey.<br>
<br>
<br>
<b><font size="4" color="#000080">NIFFindByKEY</font></b><br>
<br>
NIFFindByKey searches a collection for the first note whose sort key (or keys) match those specified in the second function parameter. The function sets a COLLECTIONPOSITION structure to indicate the location of this note in the collection. It also returns the number of notes that match the specified keys.<br>
<br>
The second parameter passed to NIFFindByKey is a buffer containing two data types, ITEMs and ITEMTABLEs. These are explained in the &quot;Data Types&quot; section of this chapter.<br>
<br>
<br>
<b><font size="4" color="#000080">Restrictions of NIFFindByKey</font></b><br>
<br>
NIFFindByKey is subject to the following restrictions:<br>

<ul type="disc">
<li>You cannot use NIFFindByKey to find notes that are categorized under multiple categories, since the resulting position is unpredictable.
<li>You cannot use the function to locate responses.
<li>You must specify the ITEMs passed into NIFFindByKey in the same order as the sorted columns of the view, from left to right.  Other unsorted columns may lie between the sorted columns you want to search. For example, suppose view columns 1, 3, 4, and 5 are sorted.  The key buffer may contain search keys for column 1 only; columns 1 and 3; columns 1, 3, and 4; or all the sorted columns.</ul>
<br>
<br>
<b><font size="4" color="#000080">Partial-Key Searches</font></b><br>
<br>
Using the FIND_PARTIAL match rule allows the supplied string to match any key that begins with that string, whatever may follow in the key.  For example, the string &quot;abc&quot; matches &quot;abc&quot;, &quot;abcd&quot;, &quot;abc7&quot;, and so on.  When you use FIND_PARTIAL with multiple-key searches, partial matching is used for all the specified keys.  The partial match must succeed for all the specified keys in order for a document to be selected.<br>
<br>
Partial-key searches are sensitive to the order in which documents are sorted in the view.  When you use multiple search keys, the COLLECTIONPOSITION is set to the first document that matches on all the keys.  Additional documents match the search keys until a document is encountered that does not match on all keys.  Any documents following the non-matching document cannot be located with a partial-key search, even if the documents match the partial search keys.<br>
<br>
For example, assume the following documents in a view:<br>

<ul>11	Smith	23<br>
11	Smithson	23<br>
11	Smithson	37<br>
11	Smithy	23</ul>
<br>
A partial-key search using the keys &quot;11&quot;, &quot;Smith&quot;, and &quot;23&quot; finds only the first two records;  encountering the record &quot;11 Smithson 37&quot; ends the search.<br>
<br>
<br>
<b><font size="4" color="#000080">Data Types</font></b><br>
<br>
<b><font color="#000080">ITEM</font></b><br>
<br>
The ITEM data type contains information about a data field. It contains two USHORTs, one to specify the length in bytes of the name of the field and the other to specify the length in bytes of a field's value. NIFFindByKey does not use the field name information, so the length of the field name should be set to zero.<br>
<br>
<b><font color="#000080">ITEM_TABLE</font></b><br>
<br>
The ITEM_TABLE data type is a variable-length data type that specifies summary information about the fields in a document. It consists of:<br>

<ul type="disc">
<li>A USHORT specifying the total length of this ITEM_TABLE structure
<li>A USHORT specifying the number of items in the table
<li>An array of ITEMs describing the field in a document
<li>An array containing the packed data for each field
<ul></ul>
</ul>
 <br>
<b><font size="4" color="#000080">The TWOKEY Sample Program</font></b><br>
<br>
The sample program TWOKEY is invoked with two command line arguments: a text key to search on and a number key to search on. It opens the database TWOKEY.NSF, finds all documents in the view KEYVIEW that match on both supplied keys, and prints out the note ID for each matching document.<br>
<br>
NOTE: For the purpose of this discussion, assume that TWOKEY is searching for all notes in the specified view that have &quot;Elvis&quot; as their primary key and &quot;99&quot; as their secondary key.
<table width="100%" border="1">
<tr valign="top"><td width="100%"><b>Example: Create key_buffer parameter for call to NIFFindByKey in TWOKEY</b></td></tr>
</table>
<tt><font size="2">&nbsp; &nbsp;char &nbsp; &nbsp;*pTemp; &nbsp; &nbsp; &nbsp; &nbsp; /* working pointer to key &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; */<br>
 &nbsp; char &nbsp; &nbsp;*pKey; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* saved pointer to key &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; */<br>
 &nbsp; char &nbsp; &nbsp;*Key1; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* primary key &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;*/<br>
 &nbsp; char &nbsp; &nbsp;*Key2; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* secondary key &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;*/<br>
 &nbsp; WORD &nbsp; &nbsp; Item1ValueLen; /* len of actual primary text to match on */<br>
 &nbsp; WORD &nbsp; &nbsp; Item2ValueLen; /* len of actual secondary key to match on*/</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp;WORD &nbsp; &nbsp; Item1ValueLen, Item2ValueLen, signal_flag;<br>
 &nbsp; BOOL &nbsp; &nbsp; FirstTime = TRUE;</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp;ITEM_TABLE &nbsp;Itemtbl;<br>
 &nbsp; ITEM &nbsp; &nbsp; &nbsp; &nbsp;Item;<br>
 &nbsp; WORD &nbsp; &nbsp; &nbsp; &nbsp;Word;</font></tt><br>
<br>
<br>
<br>
<br>
<tt><font size="2">/* ======================================================================<br>
This is the interesting part of NIFFindByKey() - Building the key.</font></tt><br>
<br>
<tt><font size="2">Note: Space for Key1 and Key2 is dynamically allocated.<br>
*/</font></tt><br>
<br>
<tt><font size="2">/* Processing input arguments */</font></tt><br>
<br>
<tt><font size="2">ProcessArgs(argc, argv, Key1, Key2);</font></tt><br>
<tt><font size="2"><br>
</font></tt><tt><font size="2">/* Translate the input key to LMBCS */<br>
TranslatedKeyLen = OSTranslate (<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;OS_TRANSLATE_NATIVE_TO_LMBCS,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;Key1,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;(WORD) strlen (Key1),<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;TranslatedKey,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;STRING_LENGTH);<br>
Item1ValueLen = TranslatedKeyLen + sizeof(WORD);<br>
Item2ValueLen = sizeof(double) + sizeof(WORD);</font></tt><br>
<br>
<tt><font size="2">/* Allocate memory for the key's use. */<br>
pKey = (char *)malloc(MALLOC_AMOUNT);<br>
if (pKey == NULL) &nbsp; &nbsp;</font></tt><br>
<tt><font size="2">{<br>
 &nbsp; printf(&quot;Error: Out of memory.\n&quot;);<br>
 &nbsp; </font></tt><font face="Courier New">returnCode=1;</font><br>
<font face="Courier New">   goto exit1;</font><tt><font size="2"><br>
}</font></tt><br>
<br>
<tt><font size="2">pTemp = pKey;</font></tt><br>
<br>
<tt><font size="2">/* ============================================================================<br>
 &nbsp;The key should look like:<br>
 &nbsp;an ITEM_TABLE, followed by an ITEM for every component of the key (a single<br>
 &nbsp;key has one ITEM, a two part key has two ITEMs, etc...) and then packed data<br>
 &nbsp;for each of the ITEMs.</font></tt><br>
<br>
<tt><font size="2">&nbsp; ITEM_TABLE:<br>
 &nbsp; &nbsp; Length - total length of the key<br>
 &nbsp; &nbsp; Items - number of components to the key<br>
--<br>
 &nbsp;ITEM 1:<br>
 &nbsp; &nbsp; NameLength - 0 (NIFFindByKey does not use the field name)<br>
 &nbsp; &nbsp; ValueLength - length of the actual primary key + sizeof(the type field)<br>
 &nbsp; .<br>
 &nbsp; .<br>
 &nbsp; .<br>
 &nbsp;ITEM n:<br>
 &nbsp; &nbsp; NameLength - 0 (NIFFindByKey does not use the field name)<br>
 &nbsp; &nbsp; ValueLength - length of the actual nth key + sizeof(the type field)<br>
--<br>
 &nbsp;Key 1 Type &nbsp;- type of the primary field, see the include files<br>
 &nbsp;Key 1 Value - actual value of the primary field, w/ no terminating zero<br>
 &nbsp; .<br>
 &nbsp; .<br>
 &nbsp; .<br>
 &nbsp;Key n Type &nbsp;- type of the nth sort field, see the include files<br>
 &nbsp;Key n Value - actual value of the nth sort field, w/ no terminating zero<br>
*/</font></tt><br>
<br>
<tt><font size="2">/* Creating the ITEM_TABLE structure in the key */<br>
 &nbsp;Itemtbl.Length = ( &nbsp; sizeof(Itemtbl) +<br>
 &nbsp; &nbsp; &nbsp; &nbsp; (2*(sizeof(Item))) + Item1ValueLen + Item2ValueLen);<br>
 &nbsp;Itemtbl.Items = 2;<br>
 &nbsp;memcpy (pTemp, &amp;Itemtbl, sizeof(Itemtbl));<br>
 &nbsp;pTemp += sizeof(Itemtbl);</font></tt><br>
<br>
<tt><font size="2">/* Creating the ITEMs in the key */<br>
/* Initialize first ITEM in the key */</font></tt><br>
<br>
<tt><font size="2">&nbsp; Item.NameLength = 0;<br>
 &nbsp;Item.ValueLength = Item1ValueLen;<br>
 &nbsp;memcpy (pTemp, &amp;Item, sizeof(Item));<br>
 &nbsp;pTemp += sizeof(Item);</font></tt><br>
<br>
<tt><font size="2">/* Initialize second ITEM in the key */</font></tt><br>
<br>
<tt><font size="2">&nbsp; Item.NameLength = 0;<br>
 &nbsp;Item.ValueLength = Item2ValueLen;<br>
 &nbsp;memcpy (pTemp, &amp;Item, sizeof(Item));<br>
 &nbsp;pTemp += sizeof(Item);</font></tt><br>
<br>
<tt><font size="2">/* Create the key titles, key types &amp; key values &nbsp;*/</font></tt><br>
<br>
<tt><font size="2">&nbsp; Word = TYPE_TEXT; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; /* key 1 type (found in nsfdata.h */<br>
 &nbsp;memcpy (pTemp, &amp;Word, sizeof(Word));<br>
 &nbsp;pTemp += sizeof(Word);</font></tt><br>
<br>
<tt><font size="2">&nbsp; memcpy (pTemp, TranslatedKey, TranslatedKeyLen);<br>
 &nbsp;pTemp += TranslatedKeyLen;</font></tt><br>
<tt><font size="2"><br>
</font></tt><tt><font size="2">&nbsp; Word = TYPE_NUMBER; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* key 2 type (found in nsfdata.h */<br>
 &nbsp;memcpy (pTemp, &amp;Word, sizeof(Word));<br>
 &nbsp;pTemp += sizeof(Word);</font></tt><br>
<tt><font size="2">&nbsp; &nbsp;</font></tt><br>
<tt><font size="2">&nbsp; Double = atof(Key2);<br>
 &nbsp;memcpy (pTemp, &amp;Double, sizeof(Double)); /* key 2 value &nbsp;*/<br>
 &nbsp;pTemp += sizeof(Double);<br>
</font></tt><br>
<br>
The buffer created should look like this:<br>
<br>

<table border="1">
<tr valign="top"><td width="240"><div align="center">Total length of table</div></td><td width="288"><div align="center">ITEM_TABLE structure</div></td></tr>

<tr valign="top"><td width="240"><div align="center">Number of items (search keys) in table.</div></td><td width="288"><img width="1" height="1" src="../images/Searching_a_View_Index_0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="240"><div align="center">0 </div>String length of field name.  Field name  is not used by NIFFindByKey.)</td><td width="288"><div align="center">First ITEM structure</div></td></tr>

<tr valign="top"><td width="240">String length of the actual primary key value, including the length of the data type.</td><td width="288"><img width="1" height="1" src="../images/Searching_a_View_Index_0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="240"><div align="center">0 </div>String length of field name.  Field name  is not used in NIFFindByKey.</td><td width="288"><div align="center">Second ITEM structure</div></td></tr>

<tr valign="top"><td width="240">String length of the actual secondary key value, including the length of the data type.</td><td width="288"><img width="1" height="1" src="../images/Searching_a_View_Index_0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="240">Type of data in primary field. (TYPE_TEXT)</td><td width="288"><div align="center">Data pertaining to primary key.</div></td></tr>

<tr valign="top"><td width="240">Primary key value to search for. (&quot;Elvis&quot;)</td><td width="288"><div align="center">Key value. Not NULL-terminated.</div></td></tr>

<tr valign="top"><td width="240">Type of data in secondary field. (TYPE_NUMBER)</td><td width="288"><div align="center">Data pertaining to secondary key.</div></td></tr>

<tr valign="top"><td width="240">Floating point integer containing the secondary key value to search for. (99)</td><td width="288"><img width="1" height="1" src="../images/Searching_a_View_Index_0.gif" border="0" alt=""></td></tr>
</table>

<table width="100%" border="1">
<tr valign="top"><td width="100%"><b>Example: Find notes in a view by primary TEXT key and secondary NUMBER key in TWOKEY</b></td></tr>
</table>
<br>
<tt>&nbsp;</tt><tt><font size="2">char &nbsp; &nbsp;*pKey; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* saved pointer to key &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; */<br>
 HCOLLECTION hCollection;/* collection handle &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;*/<br>
 COLLECTIONPOSITION posCollection; &nbsp; /* position within collection */<br>
 DWORD &nbsp; &nbsp;NumNotesMatch; /* number of notes matching key &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; */</font></tt><br>
<br>
<tt><font size="2"><br>
 </font></tt><tt><font size="2">/*<br>
 &nbsp; Look for notes that have the given two-part sort key.<br>
 &nbsp; A COLECTIONPOSITION structure is returned, describing where the first <br>
 &nbsp; matching note is in the collection, and a count of how many such notes <br>
 &nbsp; there are.<br>
*/<br>
 &nbsp; error = NIFFindByKey(<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;hCollection,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;pKey, &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* refer to key &nbsp; */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;FIND_CASE_INSENSITIVE, &nbsp; &nbsp; /* match rules */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; /* FIND_PARTIAL could be added to find wildcard matches */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &amp;posCollection, /* where match begins (return) */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &amp;NumNotesMatch);/* how many match (return) */</font></tt><br>
<br>
<tt><font size="2">/* Done with the key now that posCollection &amp; NumNotesMatch are prepared; <br>
 &nbsp; don't forget to free the memory.<br>
*/</font></tt><br>
<tt><font size="2">&nbsp; &nbsp;.</font></tt><br>
<tt><font size="2">&nbsp; &nbsp;.</font></tt><br>
<tt><font size="2">&nbsp; &nbsp;.</font></tt><br>
<tt><font size="2">&nbsp; &nbsp;free(pKey);<br>
 &nbsp; free(Key1);<br>
 &nbsp; free(Key2);</font></tt><br>
<tt><font size="2">&nbsp; &nbsp;free(TranslatedKey);</font></tt><br>
<br>
<tt><font size="2"><br>
/</font></tt><tt>* ======================================================================= */</tt><br>
<br>
The above code fragment illustrates the call to NIFFFindByKey. The third parameter specifies rules to use in deciding whether a note matches the keys. For definitions of these flags, see FIND_FLAGS in the <i>Reference.</i><br>
<br>
Once NIFFindByKey returns, you could then call NIFReadEntries to get a buffer containing the note IDs of all documents that match both keys.
---
