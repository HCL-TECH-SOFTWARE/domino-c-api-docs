##### Chapter 9-3
##### Setting Document Read Access

<b><font size="5" color="#000080">Introduction</font></b><br>
<br>
Notes versions prior to 3.0 used privilege levels to set the read access levels of documents in a database. Starting with Notes version 3.0, you can set the read access level of documents in a database using privilege levels (to maintain compatibility with earlier versions of Notes) and/or a name list. <br>
<br>
The name list consists of people, servers, groups, and roles. Roles in the name list are enclosed in brackets. You use the Notes user interface to create the read access levels of documents as follows: 
<ul type="disc">
<li>When you are editing a document, select File - Document Properties and select the panel with the key icon on the tab.
<li>When you are designing a form and defining its properties, select the panel with the key icon on the tab.</ul>
<br>
In the latter case, when you use the Notes user interface to create a document with the form, the document inherits the form's read access list.<br>
 <br>
<b><font size="5" color="#000080">The SETPRIVS </font></b><b><font size="5" color="#000080">Sample Program </font></b><br>
<br>
The sample program SETPRIVS allows you to set read access privilege levels or a name list; a command line argument specifies which the program is to set. If you specify privilege levels, the argument that follows determines the privilege levels to set. If you specify a<b><font color="#FF0000"> </font></b>name list, the arguments that follow determine the entries in the name list. You must enclose name list entries in brackets.<br>
<br>
The program uses a privilege mask contained in the document to set the read access privilege levels and a text list field in the document to set the read access name list.<br>
<br>
SETPRIVS first gets all the documents in a given view. It will set the read access privilege levels or name lists of these documents as specified on the command line.<br>
<br>
SETPRIVS then<b><font color="#FF0000"> </font></b>opens a collection and uses NIFReadEntries to get a buffer of all the note handles in the collection.<br>
<br>

<table width="100%" border="1">
<tr valign="top"><td width="100%"><b>setprivs.c: Get the documents whose read access will be modified</b></td></tr>
</table>
<tt><font size="2">&nbsp;typedef struct<br>
 &nbsp;{<br>
 &nbsp;WORD NumEntries;<br>
 &nbsp;char **pReaderEntries;<br>
 &nbsp;} READER_LIST;</font></tt><br>
<br>
<tt><font size="2">&nbsp;STATUS error;<br>
 char *ViewName;<br>
 short SetReaderList;<br>
 READER_LIST ReaderList;<br>
 DBHANDLE hDB;<br>
 HCOLLECTION hCollection;<br>
 NOTEID ViewNoteID;<br>
 WORD NewPrivileges;<br>
 DWORD NumUpdated = 0;<br>
 DWORD NumNotUpdated = 0;</font></tt><br>
<tt><font size="2"><br>
 if (error = NIFFindView(hDB, ViewName, &amp;ViewNoteID))<br>
 &nbsp; {<br>
 &nbsp; if (error == ERR_NOT_FOUND)<br>
 &nbsp; &nbsp; {<br>
 &nbsp; &nbsp; printf(&quot;View '%s' cannot be found\n&quot;, ViewName);<br>
 &nbsp; &nbsp; error = NOERROR;<br>
 &nbsp; &nbsp; }<br>
 &nbsp; goto Done;<br>
 &nbsp; }</font></tt><br>
<br>
<tt><font size="2">&nbsp;/* Open the collection of notes in the view at the current time.<br>
 &nbsp; Return a handle to the collection to the variable hCollection. */</font></tt><br>
<br>
<tt><font size="2">&nbsp;if (error = NIFOpenCollection(hDB, hDB, ViewNoteID,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;0,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;NULLHANDLE,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&amp;hCollection,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;NULL, NULL, NULL, NULL))<br>
 &nbsp; goto Done;</font></tt><br>
<br>
<tt><font size="2">&nbsp;{<br>
 COLLECTIONPOSITION IndexPos;</font></tt><br>
<tt><font size="2">&nbsp;DWORD EntriesReturned;<br>
 HANDLE hBuffer;<br>
 WORD &nbsp;SignalFlag; &nbsp; &nbsp; &nbsp; /* signal and share warning flags */</font></tt><br>
<br>
<tt><font size="2">&nbsp;IndexPos.Level = 0;<br>
 IndexPos.Tumbler[0] = 0;</font></tt><br>
<br>
<tt><font size="2">&nbsp;/* Create a buffer of note IDs copied from the collection and store the<br>
 &nbsp; note IDs in a buffer with handle hBuffer. */<br>
 do<br>
 &nbsp; {<br>
 &nbsp; error = NIFReadEntries(hCollection,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &amp;IndexPos,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; NAVIGATE_NEXT, 1L,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; NAVIGATE_NEXT, MAXDWORD,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; READ_MASK_NOTEID,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &amp;hBuffer, NULL,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; NULL, &amp;EntriesReturned, &amp;SignalFlag);</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp;/* processing of each note follows */</font></tt><br>
<tt><font size="2">&nbsp; &nbsp;...</font></tt><br>
<tt><font size="2">&nbsp; &nbsp;} while (SignalFlag &amp; SIGNAL_MORE_TO_DO);</font></tt><br>
<br>
<tt><font size="2">&nbsp;/* All note IDs have been captured, close the collection. */</font></tt><br>
<tt><font size="2">&nbsp;NIFCloseCollection (hCollection);</font></tt><br>
<br>
<tt><font size="2">}</font></tt><br>
<br>
<br>
<b><font size="4" color="#000080">Setting Read Access</font></b><br>
<br>
The next section of code sets the read access for each note (document) found. It calls OSLock to lock the buffer of note IDs and then opens each note in turn. If you specified setting the read access name list on the command line, the code calls the routine UpdateReaderList. If you specified setting the read access privilege level, the code calls the routine UpdatePrivMask.<br>
<br>
The read access name list is a special field in a document called $Readers. It is a field of type<b><font color="#FF0000"> </font></b>TYPE_TEXT_LIST with the ITEM_SUMMARY and ITEM_READERS flags set. In UpdateReaderList, if the $Readers text list field exists in this note, it is deleted. If you specified an empty text list entry on the command line, the note is updated. An empty text list entry clears the read access name list. If the text list from the command line is not empty, the code creates a $Readers text list field and adds the text list entries to the list. It then updates the note.<br>
<br>
In UpdatePrivMask, the original privilege mask is saved and a new privilege mask is set. If the new privilege mask is different from the original privilege mask, the note is updated.<br>
<br>
Finally, the code closes the note and unlocks and frees the memory.<br>
<br>
<br>

<table width="100%" border="1">
<tr valign="top"><td width="100%"><b>setprivs.c: The loop that sets the read access</b></td></tr>
</table>
<tt><font size="2">&nbsp; &nbsp;if (hBuffer != NULLHANDLE)<br>
 &nbsp; &nbsp; {<br>
 &nbsp; &nbsp; char String[512];<br>
 &nbsp; &nbsp; DWORD i;</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp;/* NIFReadEntries requires memory to be locked<br>
 &nbsp; &nbsp; &nbsp; (if hBuffer &lt;&gt; 0) &nbsp;*/<br>
 &nbsp; &nbsp; NOTEID *entry = OSLock(NOTEID, hBuffer);</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp;/* process each individual noteID &nbsp; &nbsp;*/<br>
 &nbsp; &nbsp; for (i=0; i &lt; EntriesReturned; i++, entry++)<br>
 &nbsp; &nbsp; &nbsp; {<br>
 &nbsp; &nbsp; &nbsp; NOTEHANDLE hNote;</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp;/* skip this noteID if it is for a category entry */<br>
 &nbsp; &nbsp; &nbsp; if (*entry &amp; NOTEID_CATEGORY)<br>
 &nbsp; &nbsp; &nbsp; &nbsp; continue;</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp;/* open each note separately, follow each with<br>
 &nbsp; &nbsp; &nbsp; &nbsp; close of note */<br>
 &nbsp; &nbsp; &nbsp; if (error = NSFNoteOpen(hDB, *entry, 0, &amp;hNote))</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp; &nbsp; OSLoadString(NULLHANDLE, ERR(error), String,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;sizeof(String)-1);<br>
 &nbsp; &nbsp; &nbsp; &nbsp; printf(&quot;Error '%s' reading docment %#lX -- %s\n&quot;,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; String, *entry, &quot; skipping it&quot;);</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;error = NOERROR;<br>
 &nbsp; &nbsp; &nbsp; &nbsp; continue;<br>
 &nbsp; &nbsp; &nbsp; &nbsp; }</font></tt><br>
<br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp;if (SetReaderList)<br>
 &nbsp; &nbsp; &nbsp; &nbsp; error = UpdateReaderList (hNote, ReaderList,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&amp;NumNotUpdated, &amp;NumUpdated);<br>
 &nbsp; &nbsp; &nbsp; else<br>
 &nbsp; &nbsp; &nbsp; &nbsp; error = UpdatePrivMask (hNote, NewPrivileges,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &amp;NumNotUpdated, &amp;NumUpdated);</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; </font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp;/* close each note &nbsp; */<br>
 &nbsp; &nbsp; &nbsp; NSFNoteClose(hNote)</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp;if (error)</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;{</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;OSLoadString(NULLHANDLE, ERR(error), String,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; sizeof(String)-1);</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;printf(&quot;Error '%s' writing document %#lX -- %s\n&quot;,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;String, *entry, &quot;skipping it&quot;);</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;error = NOERROR;</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;continue;<br>
 &nbsp; &nbsp; &nbsp; &nbsp; }<br>
 &nbsp; &nbsp; } &nbsp;/* for loop */</font></tt><br>
<br>
<tt><font size="2">&nbsp; /* finished with all noteIDs, unlock memory and free it &nbsp; */<br>
 &nbsp;OSUnlockObject(hBuffer);<br>
 &nbsp;OSMemFree(hBuffer);<br>
 &nbsp;} /* </font></tt><tt><font size="2">if (hBuffer != NULLHANDLE) */</font></tt><br>
<br>

<table width="100%" border="1">
<tr valign="top"><td width="100%"><b>setprivs.c:  Updating the read access name list</b></td></tr>
</table>
<tt><font size="2">STATUS UpdateReaderList (NOTEHANDLE hNote, READER_LIST ReaderList,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; DWORD *pdwNumNotUpdated, DWORD *pdwNumUpdated)</font></tt><br>
<tt><font size="2">{<br>
 &nbsp; &nbsp;STATUS error = NOERROR;<br>
 &nbsp; &nbsp;HANDLE hList; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* handle to privilege text list */<br>
 &nbsp; &nbsp;VOID *pList; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; /* pointer to the privilege text list */<br>
 &nbsp; &nbsp;WORD wListSize; &nbsp; &nbsp; &nbsp; &nbsp;/* total size of text list structure */<br>
 &nbsp; &nbsp;WORD i;<br>
 &nbsp; &nbsp;char *pTextEntry;</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; /* If the &quot;$Readers&quot; field exists, delete it. */</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; if (NSFItemIsPresent(hNote, DESIGN_READERS , (WORD) strlen(DESIGN_READERS)))<br>
 &nbsp; &nbsp; &nbsp; &nbsp;if (error = NSFItemDelete (hNote, DESIGN_READERS,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; (WORD)strlen(DESIGN_READERS)))<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;return (error);</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; pTextEntry = *(ReaderList.pReaderEntries);<br>
 &nbsp; &nbsp;if (pTextEntry[0] == '\0')<br>
 &nbsp; &nbsp; &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp; &nbsp;/* Just update the note - the $Readers field is deleted */</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; if (!(error = NSFNoteUpdate(hNote, UPDATE_NOCOMMIT)))<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;(*pdwNumUpdated)++;</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; return (error);<br>
 &nbsp; &nbsp; &nbsp; &nbsp;}</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; /* Create an empty text list structure */</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; if (error = ListAllocate (0, 0, FALSE, &amp;hList, &amp;pList, &amp;wListSize))<br>
 &nbsp; &nbsp; &nbsp; &nbsp;return (error);</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; OSUnlock(hList);</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; pList=NULL;</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; /* Add each text list entry */<br>
 &nbsp; &nbsp;for (i = 0; i &lt; ReaderList.NumEntries; i++)<br>
 &nbsp; &nbsp; &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp; &nbsp;pTextEntry = *(ReaderList.pReaderEntries + i);</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; if (error = ListAddEntry (hList, FALSE, &amp;wListSize, i,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;pTextEntry,(WORD)strlen(pTextEntry)))<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;OSMemFree(hList);<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;return (error);<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;}</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; } &nbsp;/* for */</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; /* Add the completed field to the note. */</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; pList = OSLockObject (hList);<br>
 &nbsp; &nbsp;error = NSFItemAppend (hNote, ITEM_SUMMARY | ITEM_READERS,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; DESIGN_READERS, (WORD)strlen (DESIGN_READERS),<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; TYPE_TEXT_LIST, pList, wListSize);</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; /* Unlock and free the buffer that was holding the text list field. */</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp;OSUnlock(hList);<br>
 &nbsp; &nbsp; OSMemFree(hList);<br>
 &nbsp; &nbsp; if (error)<br>
 &nbsp; &nbsp; &nbsp; &nbsp;return (error);</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; /* Update the note */</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; if (!(error = NSFNoteUpdate(hNote, UPDATE_NOCOMMIT)))<br>
 &nbsp; &nbsp; &nbsp; &nbsp;(*pdwNumUpdated)++;</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; return (error);</font></tt><br>
<br>
<tt><font size="2">}</font></tt><br>
<br>

<table width="100%" border="1">
<tr valign="top"><td width="100%"><b>setprivs.c:  Updating the read access privilege levels</b></td></tr>
</table>
<tt><font size="2">STATUS UpdatePrivMask (NOTEHANDLE hNote, WORD NewPrivMask,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; DWORD *pdwNumNotUpdated, DWORD *pdwNumUpdated)</font></tt><br>
<tt><font size="2">{<br>
 &nbsp; &nbsp;WORD OldPrivMask;<br>
 &nbsp; &nbsp;STATUS error = NOERROR;</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; /* get original privileges, check to see if different */<br>
 &nbsp; &nbsp;NSFNoteGetInfo(hNote, _NOTE_PRIVILEGES, &amp;OldPrivMask);<br>
 &nbsp; &nbsp;if (OldPrivMask == NewPrivMask)<br>
 &nbsp; &nbsp; &nbsp; (*pdwNumNotUpdated)++;<br>
 &nbsp; &nbsp;else<br>
 &nbsp; &nbsp; &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp; &nbsp;NSFNoteSetInfo (hNote, _NOTE_PRIVILEGES, &amp;NewPrivMask);<br>
 &nbsp; &nbsp; &nbsp; &nbsp;if (!(error = NSFNoteUpdate(hNote, UPDATE_NOCOMMIT)))<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;(*pdwNumUpdated)++;<br>
 &nbsp; &nbsp; &nbsp; &nbsp;}<br>
 &nbsp; &nbsp;return (error);<br>
}</font></tt><br>
<br>
<br>
<b><font size="4" color="#000080">Viewing the Read Access Name List</font></b><br>
<br>
In Notes, open the database and select a document. Select File - Document Properties and select the key tab. The read access name list is displayed in the text box.<font color="#FF0000"> </font><br>
<br>
<br>
<b><font size="4" color="#000080">Viewing the Read Access Privilege Levels</font></b><br>
<br>
In Notes, open the database and select a document.  Select File - Document Properties and select the key tab.<br>
<br>
<br>
<b><font size="4" color="#000080">Encoding the Read Access Privilege Levels</font></b><br>
<br>
Privilege levels are specified by the numbers 1 through 5. Each number refers to a specific bit in the WORD used in the third argument of NSFNoteSetInfo. The chart below shows the bits and their corresponding decimal values. To set multiple privilege levels, you must set multiple bits.<br>
<br>
Privilege	Bit		Decimal<br>
Level		Number	Value<br>
------------------------------------------------------<br>
1			0			1<br>
2			1			2<br>
3			2			4 <br>
4			3			8<br>
5			4			16	<br>
<br>
The privilege code specified in the command line of SETPRIVS is passed as the third argument to NSFNoteSetInfo and is the sum of the desired privilege level decimal values. For example, to specify privilege 3 and privilege 4 on the command line, use 12 for the privilege code. Privilege level 3 has a decimal value of 4 and privilege level 4 has a decimal value of 8. The sum of the two decimal values is 12.
---
