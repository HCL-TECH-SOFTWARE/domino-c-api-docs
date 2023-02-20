##### Chapter 10-5
##### Unified Messaging Solutions

<b><font size="5" color="#000080">Introduction</font></b><br>
<br>
Unified Messaging (UM) is the ability to combine voice, mail, fax, paging, etc. into one central place allowing all types of messages to become accessible from one source.  In the Domino and Notes environment this source could be an &quot;inbox&quot; folder in a mail database where incoming messages of the above types are sent.  <br>
<br>
You can implement Unified Messaging functionality within an Extension Manager application.  The Extension Manager notifications, EM_NSFADDTOFOLDER and EM_NSFMARKREAD, and the C API function, NSFFolderGetIDTable, are useful for Unified Messaging solutions.<br>
<br>
<b><font size="4" color="#000080">Extension Manager Notification EM_NSFADDTOFOLDER</font></b><br>
<br>
An Extension Manager application can be notified every time a note is added or removed from a folder by trapping the EM_NSFADDTOFOLDER notification.  In a Unified Messaging scenario, the incoming note can be a Fax (or any other type of message) to an inbox folder in a mail database.  The Extension Manager code for this notification could check the incoming note for any Fax property, identify the note as a Fax, and then perhaps send a user notification that a Fax has been received.  This type of processing can be extended to many other types of messages.<br>
<br>
<b><font size="4" color="#000080">Extension Manager Notification EM_NSFMARKREAD</font></b><br>
<br>
The Extension Manager notification, EM_NSFMARKREAD is called when a note is opened by the Notes client and marked READ.  This notification can be used in a Unified Messaging scenario that implements a &quot;Message Wait Indicator&quot; (MWI).  A &quot;Message Wait Indicator&quot; can be a notification to a user  that  &quot; a message is waiting&quot; for them, and then be removed when the message has been read.<br>
<br>
<br>
<b><font size="5" color="#000080">Extension Manager Sample Code</font></b><br>
<br>
The following Extension Manager code illustrates how to trap the EM_NSFADDTOFOLDER notification and detect if a FAX has been received in the &quot;inbox&quot; of a mail database. <br>
<br>
<tt><font size="2">STATUS LNPUBLIC EMHandlerProc( EMRECORD FAR * theData )</font></tt><br>
<tt><font size="2">{ <br>
	VARARG_PTR &nbsp;argPtr;<br>
	STATUS &nbsp; &nbsp; &nbsp;error; <br>
	<br>
	argPtr = theData-&gt;Ap;<br>
<br>
	/* do nothing if there is an error. */<br>
	if ( theData-&gt;Status ) <br>
	{<br>
		goto Exit0;<br>
	} <br>
<br>
<br>
	switch (theData-&gt;EId)<br>
	{<br>
		<br>
		case EM_NSFADDTOFOLDER:<br>
		</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; /* declare the arguments */</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; DBHANDLE hViewDB = NULLHANDLE;</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; DBHANDLE hDataDB = NULLHANDLE;</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; NOTEID FolderNoteID, InboxNoteID;</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; NOTEID NoteID;</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; UNID &nbsp; *NoteUNID</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; BOOL &nbsp; IsAddOperation;</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; TIMEDATE *RevisionTime;</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; </font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; HANDLE hNote = NULLHANDLE;</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; char &nbsp; DesignName[512];</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; char &nbsp; Dbinfo[NSF_INFO_SIZE];</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; char &nbsp; MailDatabase60[]=&quot;StdR6Mail&quot;;</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; char &nbsp; MailDatabase50[]=&quot;StdR50Mail&quot;;</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; char &nbsp; MailDatabase45[]=&quot;StdR45Mail&quot;;</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; BOOL &nbsp; IsMailDB = FALSE;</font></tt><br>
<tt><font size="2">&nbsp;</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; /* get the arguments */</font></tt><br>
<tt><font size="2"><br>
 		hViewDB = VARARG_GET( argPtr, DBHANDLE );<br>
 		hDataDB = VARARG_GET( argPtr, DBHANDLE );	<br>
		FolderNoteID = VARARG_GET( argPtr, NOTEID ); </font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; NoteID = VARARG_GET( argPtr, NOTEID ); </font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; NoteUNID = VARARG_GET( argPtr, UNID * );</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; IsAddOperation = VARARG_GET( argPtr, BOOL ); &nbsp;</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; RevisionTime = VARARG_GET( argPtr, TIMEDATE * ); </font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; </font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; /* process post Notes Notification */</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; if (theData-&gt;NotificationType == EM_AFTER)</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; {</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; </font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;if (error = NSFDbInfoGet (hViewDB, Dbinfo))</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;goto Exit0;</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* check to see if this is a 4.5 or later mail database */</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;NSFDbInfoParse(Dbinfo, INFOPARSE_DESIGN_CLASS, DesignName,</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; sizeof(DesignName));</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;if (strcmp(DesignName, MailDatabase45) == 0)</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;IsMailDB = TRUE;</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;else if (strcmp(DesignName, MailDatabase50) == 0)</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;</font></tt><tt><font size="2">IsMailDB = TRUE; </font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;else if (strcmp(DesignName, MailDatabase60) == 0)</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;IsMailDB = TRUE; &nbsp; </font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;else </font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;goto Exit0;</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* check to see if this is the &quot;Inbox&quot; Folder */</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;if (error = NIFFindView (hViewDB, &quot;Inbox&quot;, &amp;InboxNoteID))</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;goto Exit0;</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;if (InboxNoteID != FolderNoteID)</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;goto Exit0;</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* open the note */</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;if (error = NSFNoteOpenExt (hViewDB, NoteID, </font></tt><tt>OPEN_RAW_MIME</tt><tt><font size="2">, &amp;hNote))</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;goto Exit0;</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* check to see if this note is a FAX */</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;if (NSFItemIsPresent (hNote, &quot;Fax_Status&quot;, (WORD)strlen(&quot;Fax_Status&quot;)))</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;{ &nbsp;</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* send notification that a FAX has been received...*/</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;}</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;NSFNoteClose(hNote);</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;error = ERR_EM_CONTINUE;</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; }</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; 		</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; break;<br>
		<br>
 			<br>
 &nbsp; &nbsp;} /* END SWITCH */<br>
	 	<br>
	<br>
Exit0:<br>
<br>
	return( ERR_EM_CONTINUE );</font></tt><br>
<tt><font size="2">}	</font></tt>
---
