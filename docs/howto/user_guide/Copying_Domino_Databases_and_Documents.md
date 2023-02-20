##### Chapter 5-2
##### Copying Domino Databases and Documents

This chapter describes example programs that access some of the parts of a Domino database. The examples access database header information and notes without reading their internal structure. <br>
<br>
<br>
<b><font size="5" color="#000080">COPYDB: Making a Replica Copy of a Database</font></b><br>
<br>
The sample program COPYDB makes a replica copy of a Domino database. It demonstrates how to create a new database and how to access the various components of a database. The source code for copydb.c is in the directory samples\basic\copydb.<br>
<br>
COPYDB first creates a new database, then copies all the parts of the source database -- including the replication settings, the access control list, and all the notes -- to the new database. By copying these parts, COPYDB creates a new database that is a replica copy of the original. Once it has created the database, COPYDB sets the title of the new database to the user-specified value.<br>
<br>
<br>
<b><font size="4" color="#000080">Creating a New Database</font></b><br>
<br>
COPYDB either prompts for the filename of the database to be copied, the filename for the resulting database copy, and the title of the resulting database, or gets this information from the command line arguments. After processing this information, COPYDB calls NSFDbCreate to create a new database. <br>
<br>
The newly created database is completely empty. It has no title, no access control list (everyone is a manager), no icon, no forms, no views, and no documents. Also, the database is closed. To copy various parts of the source database to the new database, COPYDB calls NSFDbOpen to open the new database.
<table width="100%" border="1">
<tr valign="top"><td width="100%"><b>copydb.c: Creating and Opening the Copied Database</b></td></tr>
</table>
 <tt><font size="2">&nbsp;if (error = NSFDbCreate (output_path, DBCLASS_NOTEFILE, FALSE))<br>
 &nbsp; {<br>
 &nbsp; NSFDbClose (input_handle);<br>
 &nbsp; API_RETURN (ERR(error));<br>
 &nbsp; }</font></tt><br>
<br>
<tt><font size="2">&nbsp; if (error = NSFDbOpen (output_path, &amp;output_handle))<br>
 &nbsp; {<br>
 &nbsp; NSFDbClose (input_handle);<br>
 &nbsp; API_RETURN (ERR(error));<br>
 &nbsp; }</font></tt><br>
<br>
NSFDbCreate takes three parameters: a path name, a database class, and an overwrite flag. <br>
<br>
COPYDB uses the path name specified as the path name parameter to NSFDbCreate. To create a copy database that resides on your local machine, specify a path name argument of the form:<br>

<ul>[directory\]filename[.ext]</ul>
<br>
Omit the directory if it is the Domino or Notes data directory and the file extension if it is .nsf. To create a database that resides on a remote server, use the C API function OSPathNetConstruct to create a path name that includes the network path to the database.<br>
<br>
COPYDB uses the symbolic value DBCLASS_NOTEFILE as the database class. DBCLASS_NOTEFILE specifies that the new database is an ordinary Domino database.<br>
<br>
The overwrite flag tells NSFDbCreate whether to overwrite an existing Domino database with the same file name, if one exists. COPYDB specifies FALSE to prevent NSFDbCreate from overwriting an existing Domino database.<br>
<br>
<br>
<br>
<b><font size="4" color="#000080">Copying the Replication Settings</font></b><br>
<br>
After creating the destination database, COPYDB copies three parts of the source database to the destination database: the replication settings, the access control list, and all the notes. <br>
<br>
The replication settings for a database reside in a data structure of type DBREPLICAINFO. The replication settings include the database replica ID. Giving the new database the same replica ID as the source database means that the new database can replicate with the source.<br>
<br>
Note that COPYDB copies the replication settings before copying the notes. It does this because the replica ID of the database affects the IDs of notes copied into the database. By copying the replication settings first, the notes copied later become replica copies of the notes in the source database.<br>
<br>
COPYDB first calls the function NSFDbReplicaInfoGet to get the replication settings from the source database. Then it calls NSFDbReplicaInfoSet to set the replication settings in the new database.
<table width="100%" border="1">
<tr valign="top"><td width="100%"><b>copydb.c: Copying the Replication Settings</b></td></tr>
</table>
<tt><font size="2">&nbsp; DBHANDLE &nbsp; &nbsp; &nbsp; input_handle; &nbsp; /* handle of input database &nbsp;*/<br>
 &nbsp;DBHANDLE &nbsp; &nbsp; &nbsp; output_handle; &nbsp;/* handle of output database */<br>
 &nbsp;DBREPLICAINFO &nbsp;replica_info; &nbsp; /* db replication info &nbsp; &nbsp;*/<br>
 &nbsp;STATUS &nbsp; &nbsp; &nbsp; &nbsp; error; &nbsp; &nbsp; &nbsp;</font></tt><font color="#FF0000">         </font><tt><font size="2">/* return status from API calls */</font></tt><br>
<br>
<tt><font size="2">&nbsp; if (error = NSFDbReplicaInfoGet (input_handle, &amp;replica_info))<br>
 &nbsp; {<br>
 &nbsp; NSFDbClose (input_handle);<br>
 &nbsp; NSFDbClose (output_handle);<br>
 &nbsp; API_RETURN (ERR(error));<br>
 &nbsp; }</font></tt><br>
<br>
<tt><font size="2">&nbsp; if (error = NSFDbReplicaInfoSet (output_handle, &amp;replica_info))<br>
 &nbsp; {<br>
 &nbsp; NSFDbClose (input_handle);<br>
 &nbsp; NSFDbClose (output_handle);<br>
 &nbsp; API_RETURN (ERR(error));<br>
 &nbsp; }</font></tt><br>
<br>
Your program can initialize the DBREPLICAINFO structure directly instead of calling NSFDbReplicaInfoGet. Do this if you do not want the new database to be able to replicate with the source database, or if you need to set or clear other Replication Settings options. If the replica ID you set in the destination does not match the ID of the source, the destination database is not a replica of the source database.<br>
<br>
Note that the replication history is separate from the replication settings.<br>
<br>
<br>
<b><font size="4" color="#000080">Copying the Access Control List (ACL)</font></b><br>
<br>
After creating the destination database, setting the title, and copying the replication settings, COPYDB copies the Access Control List from the source database to the destination database.<br>
<br>
COPYDB uses the C API function NSFDbCopyACL, which copies a complete user access control list from one database to another, to copy an ACL that was already defined in the source database to the new database.
<table width="100%" border="1">
<tr valign="top"><td width="100%"><b>copydb.c: Copying the Access Control List</b></td></tr>
</table>
<tt><font size="2">&nbsp; DBHANDLE &nbsp;input_handle; &nbsp; /* handle of input database &nbsp;*/<br>
 &nbsp;DBHANDLE &nbsp;output_handle; &nbsp;/* handle of output database */<br>
 &nbsp;STATUS &nbsp; &nbsp;error; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* return status from API calls */</font></tt><br>
<br>
<tt><font size="2">&nbsp; if (error = NSFDbCopyACL (input_handle, output_handle))<br>
 &nbsp; {<br>
 &nbsp; NSFDbClose (input_handle);<br>
 &nbsp; NSFDbClose (output_handle);<br>
 &nbsp; API_RETURN (ERR(error));<br>
 &nbsp; }</font></tt><br>
<br>
<br>
In the C API <i>Reference</i><i>,</i> there is a note class called NOTE_CLASS_ACL. This type of note contains information about the database access control list. However, the note is not the access control list itself. The access control list is stored in the database header.<br>
<br>
<br>
<b><font size="4" color="#000080">Copying the Notes</font></b><br>
<br>
After copying the replication settings and the access control list, COPYDB copies all the notes from the source database to the destination. <br>
<br>
COPYDB does not use the function NSFDbCopy to copy all the notes, since such copies are not guaranteed to be replicas of the original notes. Instead, the program uses NSFDbGetModifiedNoteTable to obtain an ID Table of all notes in the database. The program then calls IDScan to obtain each NOTEID and NSFDbCopyNote to copy each note -- including all forms, views, filters, and documents -- from one database to the other. <br>
<br>
NSDbGetModifiedNoteTable retrieves only those notes that were created or modified since the specified cutoff time. This parameter is a TIMEDATE structure, a Domino- and Notes-specific binary representation of a time and date. The definition of the TIMEDATE structure is shown below. To read and write TIMEDATE structures, use the API functions that are designed to do so.<br>
<br>
<tt><font size="2">typedef struct { &nbsp; &nbsp; /* a single time/date */<br>
 &nbsp;DWORD Innards[2]; &nbsp;/* Innards[0] - Ticks within day (in 10 msec units) */<br>
 			 /* Innards[1] - Days since &quot;origin&quot; */<br>
} TIMEDATE;</font></tt><br>
<br>
COPYDB specifies a cutoff time/date of TIMEDATE_WILDCARD (ANYDAY\ALLDAY). This special constant specifies that no cutoff date should be used, so NSFDbGetModifiedNoteTable retrieves all notes, regardless of their creation or modification date. <br>
<br>
NSFDbGetModifiedNoteTable restricts the set of notes it copies according to a note class mask. The HCL C API for Domino and Notes defines a number of note classes, including documents, forms, and views. The <i>Reference</i> defines the special constant NOTE_CLASS_ALL as the note class mask that includes all classes of notes. COPYDB specifies NOTE_CLASS_ALL so that all notes are copied.
<table width="100%" border="1">
<tr valign="top"><td width="100%"><b>copydb.c: Copying the Notes</b></td></tr>
</table>
<tt><font size="2">&nbsp; DBHANDLE &nbsp;input_handle; &nbsp; /* handle of input database &nbsp;*/<br>
 &nbsp;DBHANDLE &nbsp;output_handle; &nbsp;/* handle of output database */</font></tt><br>
<tt><font size="2">&nbsp; DBID &nbsp; &nbsp; &nbsp;input_dbid; &nbsp; &nbsp; /* dbid of input database */<br>
 &nbsp;DBID &nbsp; &nbsp; &nbsp;output_dbid; &nbsp; &nbsp;/* dbid of output database */</font></tt><br>
<tt><font size="2">&nbsp; TIMEDATE &nbsp;last_time; &nbsp; &nbsp; &nbsp;/* returned from<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; NSFDbGetModifiedNoteTable */<br>
 &nbsp;HANDLE &nbsp; &nbsp;idtable_p; &nbsp; &nbsp; &nbsp;/* handle to id table */<br>
 &nbsp;DWORD &nbsp; &nbsp; num_scanned, num_entries;<br>
 &nbsp;NOTEID &nbsp; &nbsp;note_id;<br>
 &nbsp;TIMEDATE &nbsp;start_time; &nbsp; &nbsp; /* time/date of notes to copy */<br>
 &nbsp;STATUS &nbsp; &nbsp;error; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* return status from API calls */</font></tt><br>
<tt><font size="2">&nbsp; </font></tt><br>
        <tt>TimeConstant (TIMEDATE_WILDCARD, &amp;start_time);</tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp;NSFDbIDGet (input_handle, &amp;input_dbid);<br>
 &nbsp; NSFDbIDGet (output_handle, &amp;output_dbid);</font></tt><br>
<br>
<tt><font size="2">/* Get the NoteID table for all notes in the input database */<br>
 &nbsp; if (error = NSFDbGetModifiedNoteTable (input_handle,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;NOTE_CLASS_ALL,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;start_time, &amp;last_time,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&amp;idtable_p) )<br>
 &nbsp; &nbsp; &nbsp;if (error == ERR_NO_MODIFIED_NOTES)<br>
 &nbsp; &nbsp; &nbsp; &nbsp; printf (&quot;There are no documents in the Database.\n&quot;);<br>
 &nbsp; &nbsp; &nbsp;else<br>
 &nbsp; &nbsp; &nbsp; &nbsp; {<br>
 &nbsp; &nbsp; &nbsp; &nbsp; IDDestroyTable (idtable_p);<br>
 &nbsp; &nbsp; &nbsp; &nbsp; NSFDbClose (input_handle);<br>
 &nbsp; &nbsp; &nbsp; &nbsp; NSFDbClose (output_handle);<br>
 &nbsp; &nbsp; &nbsp; &nbsp; API_RETURN (ERR(error));<br>
 &nbsp; &nbsp; &nbsp; &nbsp; }<br>
 &nbsp; num_scanned = 0L;<br>
 &nbsp; num_entries = IDEntries (idtable_p);<br>
 &nbsp; if (num_entries)<br>
 &nbsp; &nbsp; &nbsp;while (IDScan (idtable_p, (FLAG)(num_scanned++ == 0), &amp;note_id) )</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;if (error = NSFDbCopyNote (input_handle, NULL,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&amp;replica_info.ID, note_id,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;output_handle, &amp;output_dbid,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&amp;replica_info.ID, NULL,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;NULL) )<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;IDDestroyTable (idtable_p);<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;NSFDbClose (input_handle);<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;NSFDbClose (output_handle);<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;API_RETURN (ERR(error));<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;}<br>
 &nbsp; IDDestroyTable (idtable_p);</font></tt><br>
<br>
<br>
<tt><font size="2">&nbsp; &nbsp;printf(&quot;\nDatabase copied&quot;);<br>
 &nbsp; fflush(stdout);</font></tt><br>
<br>
<br>
After this sequence of C API functions, the new database is complete.  It has the same replication settings, ACL, icon, policy<font color="#FF0000"> </font>and help documents, views, forms,  filters, and data notes as the input database. The new database has the same title as the original database. You have the option to change the title of the new database.<br>
<br>
<b><font size="4" color="#000080">Changing the Database Title</font></b><br>
<br>
Starting with Domino and Notes Release 4, you set the title of a new database after completing the notes copying process. COPYDB sample performs the following steps: <br>

<ul type="disc">
<li>Call NSFDbInfoGet to get the database information buffer.
<li>Call NSFDbInfoModify to change the title of the output database in its information buffer.
<li>Call NSFDbInfoSet to set the database information buffer.</ul>
<br>
COPYDB uses the database title specified by the user as the title of the new database. 
<table width="100%" border="1">
<tr valign="top"><td width="100%"><b>copydb.c: Setting the Database Title</b></td></tr>
</table>
<br>
<tt><font size="2">/* Clear the array for the database information buffer */<br>
 &nbsp; output_db_info[0] = '\0';</font></tt><br>
<br>
<tt><font size="2">/* Get the database information buffer. */</font></tt><br>
<tt><font size="2">&nbsp; &nbsp;if (error = NSFDbInfoGet (output_handle, output_db_info))<br>
 &nbsp; &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp;NSFDbClose (output_handle);<br>
 &nbsp; &nbsp; &nbsp;API_RETURN(ERR(error));<br>
 &nbsp; &nbsp; &nbsp;}</font></tt><br>
<br>
<tt><font size="2">/* Change the database title in the database information buffer */<br>
 &nbsp; NSFDbInfoModify (output_db_info, INFOPARSE_TITLE, output_title);</font></tt><br>
<br>
<tt><font size="2">/* Set the database information buffer. */</font></tt><br>
<tt><font size="2">&nbsp; &nbsp;if (error = NSFDbInfoSet (output_handle, output_db_info))<br>
 &nbsp; &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp;NSFDbClose (output_handle);<br>
 &nbsp; &nbsp; &nbsp;API_RETURN(ERR(error));<br>
 &nbsp; &nbsp; &nbsp;}</font></tt><br>
<br>
The database information buffer stores the information about the database title, categories, and design template options in a character array. COPYDB uses the function NSFDbInfoModify to change the database title in this character array, then passes the array as input to NSFDbInfoSet, giving the output database the new title. COPYDB then closes both the input and the output databases. <br>
<br>
<b><font size="4" color="#000080">Updating Database Information in the Icon Note</font></b><br>
<br>
Anytime a modification is made to the database with NSFDbInfoModify, you must also update the Icon Note, if one exists, with NSFItemSetText.  Pass the database information buffer as the third parameter to NSFItemSetText.  This synchronizes the database title, categories, class, and design class information in both places.  For example, when you create a new database from a template, after you have updated the title in the database information buffer with NSFDbInfoSet, you also need to update it in the Icon note as follows:<br>
<br>
<tt>/*	Update the icon note's title with that from the NTF. */</tt><br>
<tt>NOTEHANDLE hIconNote;</tt><br>
<br>
<tt>if (!NSFNoteOpen(output_handle, NOTE_ID_SPECIAL+NOTE_CLASS_ICON,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 0, &amp;hIconNote))<br>
{</tt><br>
<tt>&nbsp; &nbsp; /* Update the FIELD_TITLE (&quot;$TITLE&quot;) field if present */<br>
 &nbsp; &nbsp;if (NSFItemIsPresent (hIconNote, FIELD_TITLE, (WORD) strlen (FIELD_TITLE)) )<br>
 &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp; &nbsp;NSFItemSetText(hIconNote, FIELD_TITLE, output_db_info, MAXWORD);<br>
 &nbsp; &nbsp; &nbsp; &nbsp;NSFNoteUpdate(hIconNote, 0); <br>
 &nbsp; &nbsp;}</tt><br>
<tt>&nbsp; &nbsp; NSFNoteClose(hIconNote);<br>
}</tt><br>
<br>
<br>
<b><font size="5" color="#000080">CPNOTES: Copying a Subset of a Database</font></b><br>
<br>
<b><font size="4" color="#000080">Copying Selective Notes in a Database</font></b><br>
<br>
The sample program CPNOTES shows how to copy notes selectively, using the note classes and  modification times.
<table width="100%" border="1">
<tr valign="top"><td width="100%"><b>cpnotes.c: Copy of Notes Using Date Criteria</b></td></tr>
</table>
<tt><font size="2">&nbsp; &nbsp;TIMEDATE &nbsp; start_time; &nbsp;/* cutoff time in Domino binary form */<br>
 &nbsp; STATUS &nbsp; &nbsp; error; &nbsp; &nbsp; &nbsp; /* return status from API calls */</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp;/* Get the current time and date. */<br>
 &nbsp; OSCurrentTIMEDATE (&amp;start_time);</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp;/* Subtract one month from the current time/date. */<br>
 &nbsp; if (TimeDateAdjust(&amp;start_time, 0, 0, 0, 0, -1, 0))<br>
 &nbsp; &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp;NSFDbClose (input_handle);<br>
 &nbsp; &nbsp; &nbsp;NSFDbClose (output_handle);<br>
 &nbsp; &nbsp; &nbsp;printf (&quot;\nProblem adjusting time/date.\n&quot;);<br>
 &nbsp; &nbsp; &nbsp;API_RETURN (NOERROR);<br>
 &nbsp; &nbsp; &nbsp;}</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp;/* Copy only the documents (data notes) modified in the last month.*/<br>
 &nbsp; error = NSFDbCopy (input_handle,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;output_handle,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;start_time,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;NOTE_CLASS_DOCUMENT);</font></tt><br>
<br>
In the code above, the C API function TimeDateAdjust modifies a TIMEDATE structure to subtract one month from the current  date, so the call to NSFDbCopy copies only data notes modified in the last month.<br>
<br>
<br>
<b><font size="4" color="#000080">Using Dates Another Way</font></b><br>
<br>
Now we'll show another way to modify a character time/date string and use it to copy the help document. 
<table width="100%" border="1">
<tr valign="top"><td width="100%"><b>cpnotes.c: Using Dates</b></td></tr>
</table>
<tt><font size="2">&nbsp; &nbsp;char &nbsp; &nbsp; &nbsp;timetext[MAXALPHATIMEDATE+1]; /* character time/date */<br>
 &nbsp; char &nbsp; &nbsp; &nbsp;*text_pointer; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* pointer to timetext */</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp;/* Set a character time/date string to the start of 1996. */<br>
 &nbsp; strcpy (timetext, &quot;1/1/96 12:01 AM&quot;);</font></tt><br>
<tt><font size="2">&nbsp; &nbsp;text_pointer = timetext;</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp;/* Put the time/date text into Domino binary form. */<br>
 &nbsp; if (error = ConvertTextToTIMEDATE(NULL,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; NULL,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &amp;text_pointer,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; strlen(timetext),<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &amp;start_time))<br>
 &nbsp; &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp;NSFDbClose (input_handle);<br>
 &nbsp; &nbsp; &nbsp;NSFDbClose (output_handle);<br>
 &nbsp; &nbsp; &nbsp;API_RETURN (ERR(error));<br>
 &nbsp; &nbsp; &nbsp;}</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp;/* Copy the help document if modified since 1/1/96. */<br>
 &nbsp; error = NSFDbCopy (input_handle,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;output_handle,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;start_time,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;NOTE_CLASS_HELP);</font></tt><br>
<br>
This code calls ConvertTextToTIMEDATE to convert a character time/date string into Domino and Notes binary format. The first  argument to this function is the optional address of a structure of  internationalization settings. This structure affects the interpretation of the character time/date string. Since it is omitted, ConvertTextToTIMEDATE uses the current  internationalization settings in effect at the time of the call. The second  argument is the optional address of a structure that specifies the  syntax of the time/date string. Since it is omitted, ConvertTextToTIMEDATE uses the  default syntax. <br>
<br>
Note that the third argument is the address of a pointer to the time/date string, not the address of the string.<br>
<br>
The call to NSFDbCopy above copies the help document only if it was modified after the beginning of 1996.
---
