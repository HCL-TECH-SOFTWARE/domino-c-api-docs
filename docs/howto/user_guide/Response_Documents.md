##### Chapter 12-3
##### Response Documents

This chapter explains how to create a response (or child) document in a database and how to find and read the responses to a main (parent) document.<br>
<br>
<br>
<b><font size="5" color="#000080">Response Reference List Item</font></b><br>
<br>
Response documents contain a response reference list item, which is an item with field name &quot;$REF&quot; and data type TYPE_NOTEREF_LIST. A response reference list consists of a LIST structure followed a UNID that identifies the parent document.<br>
The presence of a &quot;$REF&quot; field in a document makes the document a response to the parent document identified by the UNID.<br>
<br>
<b><font color="#000080">Characteristics of a Response Reference List item:</font></b><br>

<ul>
<li type="disc">The field name is always &quot;$REF&quot; (programs normally specify FIELD_LINK).
<li type="disc">At the API level, the data type is TYPE_NOTEREF_LIST.
<li type="disc">The item consists of a LIST header structure, followed by a UNIVERSALNOTEID (UNID).
<li type="disc">The UNID identifies the parent document.</ul>
<br>
<br>
<b><font size="5" color="#000080">Creating Response Documents</font></b><br>
<br>
<b><font color="#000080">Create the Response Reference List</font></b><br>
<br>
To create a response document, first obtain the UNID of the parent document and initialize a UNID data structure with this UNID. Also initialize a LIST data structure, setting the ListEntries member to 1. Pack the LIST structure and the UNID structure into a memory buffer so that the first byte of the UNID starts immediately after the last byte of the LIST. The resulting buffer contains the data value of the response reference list item.
<table width="100%" border="1">
<tr valign="top"><td width="100%"><b>Creating the Response Reference List</b></td></tr>
</table>
<tt><font size="2">if (error = NSFDbGetNoteInfo (db_handle, main_nid, &amp;main_oid,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &amp;lastmod_td, &amp;note_class))<br>
{<br>
 &nbsp; &nbsp;return ERR(error);<br>
}</font></tt><br>
<br>
<tt><font size="2">/* Initialize the LIST header part of the response reference list */<br>
ListHdr.ListEntries = (USHORT) 1;</font></tt><br>
<br>
<tt><font size="2">/* Initialize the UNID part of the response reference list */<br>
NoteUNID.File = main_oid.File; /* user-unique identifier */<br>
NoteUNID.Note = main_oid.Note; /* time/date when the note was created */</font></tt><br>
<br>
<tt><font size="2">/* Pack the LIST and the UNID members of the Noteref list into<br>
 &nbsp; a memory block.<br>
*/<br>
memcpy(buf, (char*)&amp;ListHdr, sizeof(LIST));<br>
memcpy((buf+sizeof(LIST)), (char*)&amp;NoteUNID, sizeof(UNID));</font></tt><br>
<br>
<br>
<b><font color="#000080">Append the Response Reference List Item</font></b><br>
<br>
Next, create or open the document that is to become the response document. Call NSFItemAppend to append the response reference list to this document. For the item name, specify FIELD_LINK. For the data type, specify TYPE_NOTEREF_LIST. For the data value, specify the buffer containing the packed LIST and UNID.<br>
<br>
Finally, update and close the response note.<br>
<br>

<table width="100%" border="1">
<tr valign="top"><td width="100%"><b>Appending the Response Reference List Item</b></td></tr>
</table>
<tt><font size="2">/* Open the second note - the one to make into a response document. */<br>
if (error = NSFNoteOpen(db_handle, resp_nid, 0, &amp;note_handle))<br>
{<br>
 &nbsp; &nbsp;return ERR(error);<br>
}</font></tt><br>
<br>
<tt><font size="2">/* Append the completed response reference list to the second note<br>
 &nbsp; as an item of type TYPE_NOTEREF_LIST.<br>
*/<br>
if (error = NSFItemAppend ( note_handle,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;ITEM_SUMMARY,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;FIELD_LINK, &nbsp; &nbsp; &nbsp; &nbsp; /* $REF */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;strlen(FIELD_LINK),<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;TYPE_NOTEREF_LIST, &nbsp;/* data type */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;buf, &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* resp ref list */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;(DWORD)(sizeof(LIST) + sizeof(UNID)) ))<br>
{<br>
 &nbsp; &nbsp;NSFNoteClose(note_handle);<br>
 &nbsp; &nbsp;return ERR(error);<br>
}</font></tt><br>
<br>
<br>
<b><font size="5" color="#000080">Reading Response Documents</font></b><br>
<br>
Hierarchical views display response documents indented below the corresponding main document. <br>
<br>
Since a COLLECTION object, obtained by NIFOpenCollection, preserves the ordering and indenting of the view, the best way to find response documents in a database is to use a hierarchical view COLLECTION and NIFReadEntries.<br>
<br>
A response reference list links a child document to its parent. However, the parent document does not contain a link to the child. Given a parent document, then, the only practical way to find the corresponding child documents is to navigate to the child using a hierarchical view.<br>
<br>
<br>
<b><font size="4" color="#000080">Example Using NIFReadEntries</font></b><br>
<br>
The example source code below processes documents in a hierarchical view. It loops over main documents in the view. Each time through the loop, it reads one main document and all the responses to that main document. It calls NIFReadEntries three times: first to read one main document, then to skip to the child of the main document and read all the children, and then to navigate to the next main document.<br>
<br>

<table width="100%" border="1">
<tr valign="top"><td width="100%"><b>Example Reading Response Documents</b></td></tr>
</table>
<tt><font size="2">/* set coll_pos to first doc in view */<br>
 &nbsp; &nbsp;coll_pos.Level = 0;<br>
 &nbsp; &nbsp;coll_pos.Tumbler[0] = 1;</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; while(TRUE) &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; /* loop over all main docs in view */<br>
 &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp; &nbsp;err = NIFReadEntries( &nbsp; coll_hdl,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&amp;coll_pos, &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* where the match begins */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;NAVIGATE_CURRENT, &nbsp; /* order to skip entries */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;0, &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* no. of entries to skip */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;NAVIGATE_NEXT_PEER, /* navigate at this level */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;1, &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* just get one note id */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;READ_MASK_NOTEID, &nbsp; /* get the note ID */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&amp;buff_hdl, &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* Note ID return buffer */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;NULL, &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; /* length of return buffer */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;NULL, &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; /* no. entries skipped */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&amp;notes_found, &nbsp; &nbsp; &nbsp; /* entries read */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;NULL); &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* share warning */<br>
 &nbsp; &nbsp; &nbsp; &nbsp;if (err)<br>
 &nbsp; &nbsp; &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;printf(&quot;Error: unable to read next entry note in view.\n&quot;);</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; if (buff_hdl != NULLHANDLE)<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;OSMemFree(buff_hdl);<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;}<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;goto EXIT5;<br>
 &nbsp; &nbsp; &nbsp; &nbsp;}<br>
 &nbsp; &nbsp; &nbsp; &nbsp;/* If note is a category note, skip to next main document */<br>
 &nbsp; &nbsp; &nbsp; &nbsp;if (err = SkipToMainDocument(&amp;buff_hdl, &amp;notes_found, &amp;coll_hdl, <br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &amp;coll_pos))<br>
 &nbsp; &nbsp; &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;goto EXIT5;<br>
 &nbsp; &nbsp; &nbsp; &nbsp;}<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* process the main doc */<br>
 &nbsp; &nbsp; &nbsp; &nbsp;err = ProcessNotes(buff_hdl, notes_found, maindoc_label);<br>
 &nbsp; &nbsp; &nbsp; &nbsp;OSMemFree(buff_hdl);<br>
 &nbsp; &nbsp; &nbsp; &nbsp;if (err)<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;goto EXIT5;<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* read all response docs */<br>
 &nbsp; &nbsp; &nbsp; &nbsp;err = NIFReadEntries( &nbsp; coll_hdl,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&amp;coll_pos, &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* where the match begins */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;NAVIGATE_CHILD, &nbsp; &nbsp; /* skip main document */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;1, &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* skip 1 to responses */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;NAVIGATE_NEXT_PEER, /* navigate at this level */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;0xFFFF, &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; /* return ALL responses */</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; READ_MASK_NOTEID, &nbsp; /* get the note IDs */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&amp;buff_hdl, &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* Note ID return buffer */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;NULL, &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; /* length of return buffer */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;NULL, &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; /* no. entries skipped */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&amp;notes_found, &nbsp; &nbsp; &nbsp; /* entries read */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;NULL); &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* share warning */<br>
 &nbsp; &nbsp; &nbsp; &nbsp;if (err)<br>
 &nbsp; &nbsp; &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;printf(&quot;Error: unable to read response documents.\n&quot;);<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;if (buff_hdl != NULLHANDLE)<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;OSMemFree(buff_hdl);<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;}<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;goto EXIT5;<br>
 &nbsp; &nbsp; &nbsp; &nbsp;}<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* process response docs */<br>
 &nbsp; &nbsp; &nbsp; &nbsp;err = ProcessNotes(buff_hdl, notes_found, response_label);<br>
 &nbsp; &nbsp; &nbsp; &nbsp;OSMemFree(buff_hdl);<br>
 &nbsp; &nbsp; &nbsp; &nbsp;if (err)<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;goto EXIT5;<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* print footer and EOF */<br>
 &nbsp; &nbsp; &nbsp; &nbsp;write (evar.outfile_hdl, evar.footer, strlen(evar.footer));</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; if (evar.endoffile)<br>
 &nbsp; &nbsp; &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;write (evar.outfile_hdl, endchar, strlen(endchar));<br>
 &nbsp; &nbsp; &nbsp; &nbsp;} &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; <br>
 &nbsp; &nbsp; &nbsp; &nbsp;/*<br>
 &nbsp; &nbsp; &nbsp; &nbsp; * Skip to next main document in view. If no more documents, break <br>
 &nbsp; &nbsp; &nbsp; &nbsp; * out of loop. To detect that there are no more main docs, save <br>
 &nbsp; &nbsp; &nbsp; &nbsp; * the current position, then skip 1 to next main document<br>
 &nbsp; &nbsp; &nbsp; &nbsp; * but read 0 entries. Then compare new position to saved value. If <br>
 &nbsp; &nbsp; &nbsp; &nbsp; * position didn't change, have reached end of view. Else go back <br>
 &nbsp; &nbsp; &nbsp; &nbsp; * to top of loop to process next main document. <br>
 &nbsp; &nbsp; &nbsp; &nbsp; */<br>
 &nbsp; &nbsp; &nbsp; &nbsp;<br>
 &nbsp; &nbsp; &nbsp; &nbsp;SaveCollPos = coll_pos ;<br>
 &nbsp; &nbsp; &nbsp; &nbsp; <br>
 &nbsp; &nbsp; &nbsp; &nbsp;/* PrintIndexPos(&amp;coll_pos); */</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; err = NIFReadEntries (coll_hdl, &amp;coll_pos, <br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;NAVIGATE_NEXT_MAIN, 1,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;0, 0, 0, NULL, NULL, NULL, NULL, NULL); &nbsp; &nbsp;<br>
 &nbsp; &nbsp; &nbsp; &nbsp;if (err)<br>
 &nbsp; &nbsp; &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;printf(&quot;Error: unable to skip from response documents in view.\n&quot;);<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;goto EXIT5;<br>
 &nbsp; &nbsp; &nbsp; &nbsp;}<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* done when no change in coll pos */<br>
 &nbsp; &nbsp; &nbsp; &nbsp;for(i = 0, CollPosTumblerChanged = FALSE; <br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;i &lt;= (int)min(SaveCollPos.Level, coll_pos.Level); <br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;i++)<br>
 &nbsp; &nbsp; &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;if (SaveCollPos.Tumbler[i] != coll_pos.Tumbler[i])<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;CollPosTumblerChanged = TRUE;<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;}<br>
 &nbsp; &nbsp; &nbsp; &nbsp;}<br>
 &nbsp; &nbsp; &nbsp; &nbsp;if (!CollPosTumblerChanged &amp;&amp; (SaveCollPos.Level == coll_pos.Level))<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;break; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* coll pos unchanged: done! */<br>
 &nbsp; &nbsp; &nbsp; &nbsp;<br>
 &nbsp; &nbsp;} &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; /* end of loop over main docs */<br>
</font></tt><br>
<br>
The first call to NIFReadEntries reads just the main document. It reads only one document by specifying ReturnCount = 1 in the fifth argument.<br>
<br>
The second call to NIFReadEntries navigates to the child of the main document, skipping one, and reading the maximum number of documents possible. Note that the call specifies <tt><font size="2">NAVIGATE_NEXT_PEER</font></tt> as the ReturnNavigator argument, ensuring that NIFReadEntries reads only child documents. <tt><font size="2">NAVIGATE_NEXT_PEER</font></tt> causes NIFReadEntries to stop before reading the next main document.<br>
<br>
The third call to NIFReadEntries specifies <tt>NAVIGATE_NEXT_MAIN</tt> as the Skip Navigator argument and a skip count of 1. This moves the collection position up from the last response document to the next main document. Note that no documents are read in this third call to NIFReadEntries. Only the COLLECTIONPOSITION is affected.<br>
<br>
The remaining code in the loop checks that the COLLECTIONPOSITION did indeed change. If the COLLECTIONPOSITION did not change, there are no more entries in the collection. This condition ends the loop.<br>
<br>
<br>
<b><font size="4" color="#000080">Example Using Indent Level</font></b><br>
<br>
The sample program ONECAT reads the main documents in a category, deliberately skipping over the response notes. It uses the indent level information to distinguish main documents from response documents.<br>
<br>
After opening the database and the collection, ONECAT calls NIFFindByName to position the COLLECTIONPOSITION to the first main document in the specified category.<br>
<br>
ONECAT then calls NIFReadEntries in a loop, starting at the first document in the category, to get information about the remaining entries in the collection. ONECAT specifies the<b><font color="#FF0000"> </font></b>read mask as READ_MASK_NOTEID +<b><font color="#FF0000"> </font></b>READ_MASK_INDENTLEVELS + READ_MASK_INDEXPOSITION to get the note ID, the indent level, and the collection position of each document read.<br>
<br>
ONECAT loops over the entries in the buffer returned by NIFReadEntries. For each entry, it compares the indent level against the indent level of main documents (MAIN_TOPIC_INDENT). For category entries, the indent level is only used in multi-level columns (multiple levels of categories in one column). For note entries, the indent level tells whether the note is a main topic, response, or response to response. Main topics have an indent level of 0. Response documents have an indent level of 1.<br>
<br>

<table width="100%" border="1">
<tr valign="top"><td width="100%"><b>ONECAT: Identifying Main Documents</b></td></tr>
</table>
<tt>&nbsp; &nbsp; &nbsp; if (error = NIFReadEntries(<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; coll_handle, &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* handle to this collection */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &amp;cat_index, &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; /* where to start in collection */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; </tt><tt>FirstTime ? NAVIGATE_CURRENT : NAVIGATE_NEXT,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; /* order to use when skipping */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; FirstTime ? 0L : 1L, &nbsp; &nbsp;/* number to skip */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; NAVIGATE_NEXT, &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* order to use when reading */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 0xFFFFFFFF, &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; /* max number to read */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; READ_MASK_NOTEID + &nbsp; &nbsp; &nbsp;/* info we want */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; READ_MASK_INDENTLEVELS +<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; READ_MASK_INDEXPOSITION,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &amp;buffer_handle, &nbsp; &nbsp; &nbsp; &nbsp; /* handle to info buffer (return) &nbsp;*/<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; NULL, &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; /* length of info buffer (return) */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; NULL, &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; /* entries skipped (return) */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &amp;entries_found, &nbsp; &nbsp; &nbsp; &nbsp; /* entries read (return) */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &amp;signal_flag)) &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* signal and share warnings (return) */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; {<br>
 &nbsp; &nbsp; &nbsp; &nbsp; NIFCloseCollection (coll_handle);<br>
 &nbsp; &nbsp; &nbsp; &nbsp; NSFDbClose (db_handle);</tt><br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;return (ERR(error));<br>
 &nbsp; &nbsp; &nbsp; &nbsp; }<br>
 </tt><br>
<tt>/* Lock down (freeze the location) of the information buffer. Cast<br>
the resulting pointer to the type we need. */</tt><br>
<br>
<tt>&nbsp; &nbsp; &nbsp; buff_ptr = (BYTE *) OSLockObject (buffer_handle);</tt><br>
<br>
<tt>/* Start a loop that extracts the info about each collection entry from<br>
the information buffer. */</tt><br>
<br>
<tt>&nbsp; &nbsp; &nbsp; printf (&quot;\n&quot;);<br>
 &nbsp; &nbsp; &nbsp;for (i = 1; i &lt;= entries_found; i++)<br>
 &nbsp; &nbsp; &nbsp; &nbsp; {</tt><br>
<br>
<tt>/* Get the ID of this entry. */</tt><br>
<br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;entry_id = *(NOTEID*) buff_ptr;<br>
 &nbsp; &nbsp; &nbsp; &nbsp; buff_ptr += sizeof (NOTEID);</tt><br>
<br>
<tt>/* Get the &quot;indent level&quot; of this entry. For category entries, the indent<br>
level is only used in multi-level columns (multiple levels of categories<br>
in one column). For note entries, the indent level tells whether the<br>
note is a main topic, response, response to response, and so on. */</tt><br>
<br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;entry_indent = *(WORD*) buff_ptr;<br>
 &nbsp; &nbsp; &nbsp; &nbsp; buff_ptr += sizeof (WORD);</tt><br>
<br>
<tt>/* Find the size of this entry's index information. Each entry's index<br>
info may be a different length, since it is truncated just to the length<br>
needed. */</tt><br>
<br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;entry_index_size = COLLECTIONPOSITIONSIZE<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ((COLLECTIONPOSITION*) buff_ptr);</tt><br>
<br>
<tt>/* Get the COLLECTIONPOSITION of the entry. */</tt><br>
<br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;memcpy (&amp;entry_index, buff_ptr, entry_index_size);<br>
 &nbsp; &nbsp; &nbsp; &nbsp; buff_ptr += entry_index_size;</tt><br>
<br>
<tt>/* If this entry is a top-level category, then we have found all the notes<br>
in the category we want. (We will have reached the next major category.) */</tt><br>
<br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;if (entry_index.Level == CATEGORY_LEVEL_BEING_SEARCHED)<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;break;</tt><br>
<br>
<tt>/* If this entry is a lower-level category, skip over it. */</tt><br>
<br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;if (NOTEID_CATEGORY &amp; entry_id) continue;</tt><br>
<br>
<tt>/* If this entry is a response doc (or response to response, and so on),</tt><br>
<tt>skip over it. */</tt><br>
<br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;if (entry_indent != MAIN_TOPIC_INDENT) continue;</tt><br>
<br>
<tt>/* We have found a main-topic note. Print out its note ID. */</tt><br>
<br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;printf (&quot;Main topic count is: %lu. \tNote ID is: %lX.\n&quot;,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;++main_topics_found, entry_id);</tt><br>
<br>
<tt>/* End of loop that gets info about each entry. */</tt><br>
<br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;}</tt>
---
