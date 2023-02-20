##### Chapter 9-13
##### Activity Logging

<b><font size="5" color="#000080">Overview</font></b><br>
<br>
Notes/Domino 6 provides a new activity logging feature which replaces and surpasses the previous billing functionality.  There are many types of server activity that can be logged by the Domino server.  For a complete description of the activity logging services, including configuration instructions, please refer to the <i>Domino Administration Help</i> documentation.<br>
<br>
Domino logs all activity to the Log file (log.nsf).  For efficiency, records are written in a binary format, and many records are written to one note.  To access these records, a set of activity logging APIs are provided.<br>
<br>
The basic steps for working with activity records are the following:
<ul><br>
1. Open a stream of records with the LogOpenActivityStream function, optionally specifying a subset of activity records to read.<br>
<br>
2. Enumerate through the records in the stream using the LogEnumActivityStream function.  Each record can be processed with an action routine that you provide.<br>
<br>
3. Close the stream with the LogCloseActivityStream function.</ul>
<br>
<br>
For example:<br>

<ul><tt><font size="2">&nbsp; &nbsp;/* Open the stream. */</font></tt><br>
<tt><font size="2">&nbsp; if (error = LogOpenActivityStream(</font></tt><br>
<tt><font size="2">&nbsp; 		&amp;pstreamctx, 	/* Return the stream context */</font></tt><br>
<tt><font size="2">&nbsp; 		pserver, 		/* Server name or NULL */</font></tt><br>
<tt><font size="2">		ADMIN_LOG_FILE, 	/* LogPath -- &quot;log.nsf&quot; */</font></tt><br>
<tt><font size="2">&nbsp; 		NULL, 		/* NULL means ALL activity types. */</font></tt><br>
<tt><font size="2">&nbsp; 		0, 			/* No flags */</font></tt><br>
<tt><font size="2">&nbsp; 		NULL)) 		/* No date restriction */</font></tt><br>
<tt><font size="2">	return (ERR(error));</font></tt><br>
<br>
<tt><font size="2">&nbsp; /* Read the records */</font></tt><br>
<tt><font size="2">&nbsp; if (error = LogEnumActivityStream(</font></tt><br>
<tt><font size="2">&nbsp; 		pstreamctx, 	/* Open activity stream context */</font></tt><br>
<tt><font size="2">&nbsp; 		ActionRoutine, 	/* User defined callback */</font></tt><br>
<tt><font size="2">&nbsp; 		&amp;recordcount, 	/* Some example user data */</font></tt><br>
<tt><font size="2">&nbsp; 		NULL, 		/* Not saving the stream position. NULL OK here */</font></tt><br>
<tt><font size="2">&nbsp; 		0)) 			/* Not saving the stream position. 0 OK here */</font></tt><br>
<tt><font size="2">	return (ERR(error));</font></tt><br>
<br>
<tt><font size="2">&nbsp; /* Close the stream */</font></tt><br>
<tt><font size="2">&nbsp; LogCloseActivityStream(pstreamctx);</font></tt><br>
</ul>
<br>
<br>
<b><font size="4" color="#000080">Enumerating and processing the Activity Records</font></b><br>
<br>
After obtaining a stream of records with the LogOpenActivityStream function, you can process the records in the stream by calling the LogEnumActivityStream function, passing it a pointer to an action routine that you provide.  This action routine will then be called for each activity record as it is enumerated in the stream.  The action routine must conform to the following calling syntax (as defined in ACTIVITYSTREAMACTION)<br>

<ul><tt><font size="2">STATUS LNCALLBACK ActionRoutine(</font></tt>
<ul><tt><font size="2">	const char *DescName, </font></tt><br>
<tt><font size="2">	DWORD DescIdx,</font></tt><br>
<tt><font size="2">	DWORD Flags,</font></tt><br>
<tt><font size="2">	WORD &nbsp;PrimaryKey,</font></tt><br>
<tt><font size="2">&nbsp; &nbsp;	const TIMEDATE* TimeStamp,</font></tt><br>
<tt><font size="2">	void *pActivityRecord,</font></tt><br>
<tt><font size="2">	void *pUserData);</font></tt></ul>
</ul>
<br>
The data for each activity record is returned in the summary buffer pointed to by pActivityRecord.  The information in this buffer is in the format of an ITEM_TABLE structure, that is, it consists of: 
<ul>
<ul type="disc">
<li>A USHORT specifying the total length of the buffer
<li>A USHORT specifying the number of fields in the buffer
<li>An array of ITEMs describing the fields in the buffer
<li>An array containing the packed data for each field</ul>
<br>
</ul>
Knowing the total length of the buffer, as well as the number of items it contains, it is possible to iterate through the buffer and copy the item values to a separate array that you allocate.  <br>
<br>
The following is an example of an action routine that demonstrates how to read the buffer for each activity record.  In this example, all available information for every activity record is parsed to standard output.  Also, the pUserData structure is used to keep a running count of all the records.  For a complete sample program, please refer to the sample ACTIVITY in the directory samples\admin\activity.<br>
<br>
<br>
<tt><font size="2">STATUS LNCALLBACK ActionRoutine(</font></tt><br>
<tt><font size="2">	const char *DescName,</font></tt><br>
<tt><font size="2">	DWORD DescIdx,</font></tt><br>
<tt><font size="2">	DWORD Flags,</font></tt><br>
<tt><font size="2">	WORD &nbsp;PrimaryKey,</font></tt><br>
<tt><font size="2">	const TIMEDATE* TimeStamp,</font></tt><br>
<tt><font size="2">	void *pActivityRecord,</font></tt><br>
<tt><font size="2">	void *pUserData)</font></tt><br>
<tt><font size="2">{</font></tt><br>
<tt><font size="2">	char *pactivitybuf = (char *)pActivityRecord;</font></tt><br>
<tt><font size="2">	ITEM_TABLE itemtable;</font></tt><br>
<tt><font size="2">	ITEM* items;</font></tt><br>
<tt><font size="2">	char* name;</font></tt><br>
<tt><font size="2">	char timestr[MAXALPHATIMEDATE + 1];</font></tt><br>
<tt><font size="2">	WORD timelen;</font></tt><br>
<tt><font size="2">	char numstr[MAXALPHANUMBER + 1];</font></tt><br>
<tt><font size="2">	WORD numlen;</font></tt><br>
<tt><font size="2">	LIST *plist;</font></tt><br>
<tt><font size="2">	WORD listentries;</font></tt><br>
<tt><font size="2">	USHORT type;</font></tt><br>
<tt><font size="2">	int* pcounter = (int *)pUserData;</font></tt><br>
<tt><font size="2">	USHORT i;</font></tt><br>
<tt><font size="2">	WORD j;</font></tt><br>
<br>
<tt><font size="2">	/* Increment the record counter */</font></tt><br>
<tt><font size="2">	(*pcounter)++;</font></tt><br>
<br>
<tt><font size="2">	/* Make a local ITEM_TABLE copy */</font></tt><br>
<tt><font size="2">	memmove(&amp;itemtable, pActivityRecord, sizeof(ITEM_TABLE));</font></tt><br>
<br>
<tt><font size="2">	/* Move past to the ITEM array */</font></tt><br>
<tt><font size="2">	pactivitybuf += sizeof(ITEM_TABLE);</font></tt><br>
<br>
<tt><font size="2">	/* Allocate our own copy of the item array */</font></tt><br>
<tt><font size="2">	items = (ITEM* )malloc(itemtable.Items * sizeof(ITEM));</font></tt><br>
<br>
<tt><font size="2">	memmove(items, (char *)pactivitybuf, itemtable.Items * sizeof(ITEM)); &nbsp;</font></tt><br>
<br>
<tt><font size="2">	/* Move to the start of the actual data */</font></tt><br>
<tt><font size="2">	pactivitybuf += itemtable.Items * sizeof(ITEM);</font></tt><br>
<br>
<tt><font size="2">	ConvertTIMEDATEToText(NULL, NULL, TimeStamp, timestr, MAXALPHATIMEDATE, &amp;timelen);</font></tt><br>
<tt><font size="2">	/* Output the record header */</font></tt><br>
<tt><font size="2">	printf(&quot;Record #: %d, Name: %s, DescIdx: %d, Timestamp: %.*s\n{\n&quot;, </font></tt><br>
<tt><font size="2">		 &nbsp; *pcounter, DescName, DescIdx, timelen, timestr);</font></tt><br>
<br>
<tt><font size="2">	/* Step through all of the items */</font></tt><br>
<tt><font size="2">	for (i = 0; i &lt; itemtable.Items; i++)</font></tt><br>
<tt><font size="2">	{</font></tt><br>
<tt><font size="2">		/* Note that it's possible to have an existing item with a value length of 0 */</font></tt><br>
<tt><font size="2">		if (!items[i].ValueLength)</font></tt><br>
<tt><font size="2">			continue;</font></tt><br>
<tt><font size="2">		/* Point to the item name */</font></tt><br>
<tt><font size="2">		name = pactivitybuf;</font></tt><br>
<br>
<tt><font size="2">		pactivitybuf += items[i].NameLength; &nbsp;</font></tt><br>
<tt><font size="2">		/* Get the type of the item */</font></tt><br>
<tt><font size="2">		memmove(&amp;type, pactivitybuf, sizeof(USHORT)); &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; </font></tt><br>
<tt><font size="2">		/* Point to the value */</font></tt><br>
<tt><font size="2">		pactivitybuf += sizeof(USHORT); &nbsp; &nbsp; </font></tt><br>
<br>
<tt><font size="2">		switch (type)</font></tt><br>
<tt><font size="2">		{</font></tt><br>
<tt><font size="2">			case TYPE_TEXT:</font></tt><br>
<tt><font size="2">				{</font></tt><br>
<tt><font size="2">					printf(</font></tt><br>
<tt><font size="2">						 &nbsp;&quot;\t%.*s: %.*s\n&quot;, </font></tt><br>
<tt><font size="2">						 &nbsp;items[i].NameLength, </font></tt><br>
<tt><font size="2">						 &nbsp;name, </font></tt><br>
<tt><font size="2">						 &nbsp;items[i].ValueLength - sizeof(USHORT),</font></tt><br>
<tt><font size="2">						 &nbsp;pactivitybuf); &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;</font></tt><br>
<tt><font size="2">					break;</font></tt><br>
<tt><font size="2">				} &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; </font></tt><br>
<tt><font size="2">			case TYPE_TIME:</font></tt><br>
<tt><font size="2">				{</font></tt><br>
<tt><font size="2">					ConvertTIMEDATEToText(NULL, NULL, (TIMEDATE* )pactivitybuf, timestr, MAXALPHATIMEDATE, &amp;timelen);</font></tt><br>
<tt><font size="2">					printf(</font></tt><br>
<tt><font size="2">						 &nbsp;&quot;\t%.*s: %.*s\n&quot;, </font></tt><br>
<tt><font size="2">						 &nbsp;items[i].NameLength, </font></tt><br>
<tt><font size="2">						 &nbsp;name,</font></tt><br>
<tt><font size="2">						 &nbsp;timelen,</font></tt><br>
<tt><font size="2">						 &nbsp;timestr); &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; </font></tt><br>
<tt><font size="2">					break;</font></tt><br>
<tt><font size="2">				}</font></tt><br>
<tt><font size="2">			case TYPE_NUMBER:</font></tt><br>
<tt><font size="2">				{ &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; </font></tt><br>
<tt><font size="2">					ConvertFLOATToText(NULL, NULL, (NUMBER *)pactivitybuf, numstr, MAXALPHANUMBER, &amp;numlen);</font></tt><br>
<tt><font size="2">					printf(</font></tt><br>
<tt><font size="2">						 &nbsp;&quot;\t%.*s: %.*s\n&quot;, </font></tt><br>
<tt><font size="2">						 &nbsp;items[i].NameLength, </font></tt><br>
<tt><font size="2">						 &nbsp;name, </font></tt><br>
<tt><font size="2">						 &nbsp;numlen,</font></tt><br>
<tt><font size="2">						 &nbsp;numstr); &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;</font></tt><br>
<tt><font size="2">					break;</font></tt><br>
<tt><font size="2">				}</font></tt><br>
<tt><font size="2">			case TYPE_TEXT_LIST:</font></tt><br>
<tt><font size="2">				{</font></tt><br>
<tt><font size="2">					plist = (LIST* ) pactivitybuf;</font></tt><br>
<tt><font size="2">					listentries = ListGetNumEntries(plist, FALSE);</font></tt><br>
<tt><font size="2">					printf(</font></tt><br>
<tt><font size="2">						 &nbsp;&quot;\t%.*s:\n\t\t{\n&quot;, </font></tt><br>
<tt><font size="2">						 &nbsp;items[i].NameLength, </font></tt><br>
<tt><font size="2">						 &nbsp;name);</font></tt><br>
<br>
<tt><font size="2">					for (j = 0; j &lt; listentries; j++)</font></tt><br>
<tt><font size="2">					{</font></tt><br>
<tt><font size="2">						char *ptext;</font></tt><br>
<tt><font size="2">						WORD len;</font></tt><br>
<tt><font size="2">						ListGetText(plist, FALSE, j, &amp;ptext, &amp;len); </font></tt><br>
<tt><font size="2">						printf(&quot;\t\t%.*s\n&quot;, len, ptext);</font></tt><br>
<tt><font size="2">					}</font></tt><br>
<tt><font size="2">					printf(&quot;\t\t}\n&quot;);</font></tt><br>
<tt><font size="2">					break;</font></tt><br>
<tt><font size="2">				}</font></tt><br>
<br>
<tt><font size="2">			default:</font></tt><br>
<tt><font size="2">				printf(&quot;type not implemented: %*.s\n&quot;, items[i].NameLength, name); &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;</font></tt><br>
<tt><font size="2">		}</font></tt><br>
<tt><font size="2">		/* Point to the start of the next item. */ &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;</font></tt><br>
<tt><font size="2">		pactivitybuf += (items[i].ValueLength - sizeof(USHORT));</font></tt><br>
<tt><font size="2">	} &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; </font></tt><br>
<br>
<tt><font size="2">	printf(&quot;}\n&quot;);</font></tt><br>
<br>
<tt><font size="2">	free(items);</font></tt><br>
<br>
<tt><font size="2">	return NOERROR;</font></tt><br>
<tt><font size="2">}</font></tt><br>
<br>
<br>
<br>
<b><font size="4" color="#000080">Activity Record Field Names, Types and Descriptions</font></b><br>
<br>
Depending on which logging types have been enabled by the Domino configuration (i.e. Domino.Notes.Session, Domino.Notes.Database, Domino.AGENT, etc.), the data for each activity record retrieved by the C API functions may contain the following fields:<br>
<br>

<ul><b>Notes Session Activity <br>
Name: Domino.NOTES.Session</b><br>
<b>Checkpointed: Yes</b><br>
<br>

<table border="1">
<tr valign="top"><td width="192"><b>Field Name</b></td><td width="126"><b>Type</b></td><td width="286"><b>Description</b></td></tr>

<tr valign="top"><td width="192">OrgName</td><td width="126">Text</td><td width="286">If running on a tiered server, this is the name of the user's organization</td></tr>

<tr valign="top"><td width="192">UserName</td><td width="126">Text</td><td width="286">Name of the session user.</td></tr>

<tr valign="top"><td width="192">ServerName</td><td width="126">Text</td><td width="286">Name of the server that produced the record.</td></tr>

<tr valign="top"><td width="192">SessionId</td><td width="126">Text</td><td width="286">Uniquely identifies this session on a server.</td></tr>

<tr valign="top"><td width="192">EventType</td><td width="126">Number</td><td width="286">There are three events, Open, Checkpoint and Close. A record is written with an Open event when a session is open. A record is written with a Checkpoint event on a configured interval. When the session closes,  a record is written with a Close event. The values are assigned as follows:<br>
Open = 1<br>
Checkpoint = 2<br>
Close=4</td></tr>

<tr valign="top"><td width="192">ClientAddress</td><td width="126">Text</td><td width="286">Network address of the client</td></tr>

<tr valign="top"><td width="192">BytesFromServer</td><td width="126">Number</td><td width="286">The number of bytes the client has read from the server.</td></tr>

<tr valign="top"><td width="192">BytesToServer</td><td width="126">Number</td><td width="286">The number of bytes the client has sent to the server.</td></tr>

<tr valign="top"><td width="192">DocumentsRead</td><td width="126">Number</td><td width="286">The number of documents read during the session.</td></tr>

<tr valign="top"><td width="192">DocumentsWritten</td><td width="126">Number</td><td width="286">The number of documents written during the session</td></tr>

<tr valign="top"><td width="192">Transactions</td><td width="126">Number</td><td width="286">The number of transactions executed by this session.</td></tr>

<tr valign="top"><td width="192">Duration</td><td width="126">Number</td><td width="286">Length of time that the session was open. (1/100 second interval).</td></tr>

<tr valign="top"><td width="192">Port</td><td width="126">Text</td><td width="286">The port used by this session.</td></tr>
</table>
</ul>

<ul><br>
<b>Notes Database Activity</b><br>
<b>Name: Domino.NOTES.Database</b><br>
<b>Checkpointed: Yes</b><br>
Essentially, this is the same information as the session records but associated with a specific database. Event types are different, however.<br>
<br>

<table border="1">
<tr valign="top"><td width="192"><b>Field Name</b></td><td width="126"><b>Type</b></td><td width="286"><b>Description</b></td></tr>

<tr valign="top"><td width="192">OrgName</td><td width="126">Text</td><td width="286">If running on a tiered server, this is the name of the user's organization</td></tr>

<tr valign="top"><td width="192">DatabaseName</td><td width="126">Text</td><td width="286">The name of the database.</td></tr>

<tr valign="top"><td width="192">CheckpointId</td><td width="126">Text</td><td width="286">Identifies a particular instance of an open database for a session. </td></tr>

<tr valign="top"><td width="192">UserName</td><td width="126">Text</td><td width="286">Name of the session user.</td></tr>

<tr valign="top"><td width="192">ServerName</td><td width="126">Text</td><td width="286">Name of the server that produced the record.</td></tr>

<tr valign="top"><td width="192">SessionId</td><td width="126">Text</td><td width="286">Uniquely identifies this session on a server.</td></tr>

<tr valign="top"><td width="192">EventType</td><td width="126">Number</td><td width="286">EventType - There are five events. Open, Checkpoint, Close, CloseEnd and Mail Deposit. <br>
Open = 1 - The database has been opened.<br>
Checkpoint = 2 - Written at configured intervals<br>
Close=4 - The database has been closed. Note that if the database is opened again during this session, the values for a database will not be reset but will instead continue to increment.<br>
CloseEnd=8 - The database is being closed because the session is being closed.<br>
MailDeposit=16 - Mail has been placed in one of the server's mail. boxes. Since the database is not remotely opened or closed, there will be no corresponding Open, Close or CloseEnd events associated with this event.</td></tr>

<tr valign="top"><td width="192">ClientAddress</td><td width="126">Text</td><td width="286">Network address of the client</td></tr>

<tr valign="top"><td width="192">BytesFromServer</td><td width="126">Number</td><td width="286">The number of bytes the client has read from the server.</td></tr>

<tr valign="top"><td width="192">BytesToServer</td><td width="126">Number</td><td width="286">The number of bytes the client has sent to the server.</td></tr>

<tr valign="top"><td width="192">DocumentsRead</td><td width="126">Number</td><td width="286">The number of documents read during the session.</td></tr>

<tr valign="top"><td width="192">DocumentsWritten</td><td width="126">Number</td><td width="286">The number of documents written during the session</td></tr>

<tr valign="top"><td width="192">Transactions</td><td width="126">Number</td><td width="286">The number of transactions executed by this session.</td></tr>

<tr valign="top"><td width="192">Duration</td><td width="126">Number</td><td width="286">Length of time that the session was open. (1/100 second interval).</td></tr>

<tr valign="top"><td width="192">Port</td><td width="126">Text</td><td width="286">The port used by this session.</td></tr>
</table>

<p><b>Passthru Activity</b><br>
<b>Name: Domino.NOTES.Passthru</b><br>
<b>Checkpointed: Yes</b><br>
Passthru activity logging records record information about both ends of the connection. The incoming connection end is referred to as the client and the outgoing connection end is referred to as the server.<br>
<br>

<table border="1">
<tr valign="top"><td width="192"><b>Field Name</b></td><td width="126"><b>Type</b></td><td width="286"><b>Description</b></td></tr>

<tr valign="top"><td width="192">ClientName</td><td width="126">Text</td><td width="286">The user name associated with the incoming connection.</td></tr>

<tr valign="top"><td width="192">ClientBytesSent</td><td width="126">Number</td><td width="286">The number of bytes sent to the client end of the connection.</td></tr>

<tr valign="top"><td width="192">ClientBytesReceived</td><td width="126">Number</td><td width="286">Name of the session user.</td></tr>

<tr valign="top"><td width="192">TargetName</td><td width="126">Text</td><td width="286">The server name associated with the outgoing connection.</td></tr>

<tr valign="top"><td width="192">SessionId</td><td width="126">Text</td><td width="286">A value that uniquely identifies a passthru session.</td></tr>

<tr valign="top"><td width="192">HopList</td><td width="126">Text List</td><td width="286"> Path that the connection makes to the endpoint.</td></tr>

<tr valign="top"><td width="192">Duration</td><td width="126">Number</td><td width="286">Length of time that the session was open (1/100 second interval)</td></tr>

<tr valign="top"><td width="192">EventType</td><td width="126">Number</td><td width="286">Either 1,2 or 4 (ASCII digit) where 1=Session Open, 2=Checkpoint, 4=Session Close. When a passthru session opens, a record gets logged with EventType=1. If a session is active past a configurable checkpoint interval, another record is written with EventType=2. When the session terminates, a record is written with EventType=4. We write the checkpoint records so that in the unlikely event of a server crash, there is some record of a user's activity</td></tr>

<tr valign="top"><td width="192">ClientAddress</td><td width="126">Text</td><td width="286">Network address of the client</td></tr>

<tr valign="top"><td width="192">BytesFromServer</td><td width="126">Number</td><td width="286">The number of bytes the client has read from the server.</td></tr>

<tr valign="top"><td width="192">BytesToServer</td><td width="126">Number</td><td width="286">The number of bytes the client has sent to the server.</td></tr>

<tr valign="top"><td width="192">DocumentsRead</td><td width="126">Number</td><td width="286">The number of documents read during the session.</td></tr>

<tr valign="top"><td width="192">DocumentsWritten</td><td width="126">Number</td><td width="286">The number of documents written during the session</td></tr>

<tr valign="top"><td width="192">Transactions</td><td width="126">Number</td><td width="286">The number of transactions executed by this session.</td></tr>

<tr valign="top"><td width="192">Port</td><td width="126">Text</td><td width="286">The port used by this session.</td></tr>
</table>
</ul>

<ul><br>
<b>MAIL Activity</b><br>
<b>Name: Domino.MAIL</b><br>
<b>Checkpointed: No</b><br>
Mail logging records the activity generated by mail passing through the server. <br>
<br>

<table border="1">
<tr valign="top"><td width="192"><b>Field Name</b></td><td width="126"><b>Type</b></td><td width="286"><b>Description</b></td></tr>

<tr valign="top"><td width="192">ServerName</td><td width="126">Text</td><td width="286">The name of the server that produced the record.</td></tr>

<tr valign="top"><td width="192">SessionId</td><td width="126">Text</td><td width="286">Present for deposits only. This is the session identifier of the network session that processed the message. If enabled, there will be a Domino.Notes.Session record that corresponds to this value for Notes mail deposits and a Domino.SMTP.Session record that corresponds to this value for SMTP mail deposits.</td></tr>

<tr valign="top"><td width="192">MessageId</td><td width="126">Text</td><td width="286">A unique identifier for the message. Note that there will be many activity records generated for one message.</td></tr>

<tr valign="top"><td width="192">PostedDate</td><td width="126">Text</td><td width="286">The date that the message was sent.</td></tr>

<tr valign="top"><td width="192">EventType</td><td width="126">Number.</td><td width="286">1 = Deposit<br>
2 = Delivery<br>
4 = Delivery error<br>
8 = Transfer<br>
16 = Transfer error</td></tr>

<tr valign="top"><td width="192">Originator</td><td width="126">Text</td><td width="286">The sender of the message.</td></tr>

<tr valign="top"><td width="192">Recipients</td><td width="126">Text List</td><td width="286">The recipients of the message.</td></tr>

<tr valign="top"><td width="192">PrevHop</td><td width="126">Text</td><td width="286">The server name (or user name) that deposited the message. Only present for deposits.</td></tr>

<tr valign="top"><td width="192">NextHop</td><td width="126">Text</td><td width="286">The name of the server to which the message is being sent.</td></tr>

<tr valign="top"><td width="192">Size</td><td width="126">Text</td><td width="286">The size of the message.</td></tr>

<tr valign="top"><td width="192">ErrorMsg</td><td width="126">Text</td><td width="286">Text generated by the mail router explaining the reason for a failure. Present only if there's an error.</td></tr>
</table>
<br>
<br>
<b>POP3 Activity</b><br>
<b>Name: Domino.POP3</b><br>
<b>Checkpointed: Yes</b><br>
Sessions that terminate before the authentication step generate a Close event only. The user name in this case will be Anonymous. <br>
<br>

<table border="1">
<tr valign="top"><td width="192"><b>Field Name</b></td><td width="126"><b>Type</b></td><td width="286"><b>Description</b></td></tr>

<tr valign="top"><td width="192">OrgName</td><td width="126">Text</td><td width="286">If running on a tiered server, this is the name of the user's organization</td></tr>

<tr valign="top"><td width="192">UserName</td><td width="126">Text</td><td width="286">The name of the authenticated user or Anonymous if the session terminates before authentication.</td></tr>

<tr valign="top"><td width="192">ServerName</td><td width="126">Text</td><td width="286">The name of the server.</td></tr>

<tr valign="top"><td width="192">SessionId</td><td width="126">Text</td><td width="286">Uniquely identifies a session on the server.</td></tr>

<tr valign="top"><td width="192">EventType</td><td width="126">Number</td><td width="286">There are three possible events:<br>
Authorization = 8<br>
Checkpoint = 2<br>
Close = 4</td></tr>

<tr valign="top"><td width="192">RemoteIP</td><td width="126">Text</td><td width="286">The IP address of the client.</td></tr>

<tr valign="top"><td width="192">BytesFromServer</td><td width="126">Number</td><td width="286">The number of bytes that the client has read from the server.</td></tr>

<tr valign="top"><td width="192">BytesToServer</td><td width="126">Number</td><td width="286">The number of bytes that the client has sent to the server.</td></tr>

<tr valign="top"><td width="192">MessagesSent</td><td width="126">Number</td><td width="286">The number of messages sent to the client.</td></tr>

<tr valign="top"><td width="192">MessagesDeleted</td><td width="126">Number</td><td width="286">The number of messages deleted from the client.</td></tr>

<tr valign="top"><td width="192">TotalOpenTime</td><td width="126">Number</td><td width="286">The length of time that the session was in use. (1/100 second interval).</td></tr>
</table>
</ul>

<ul><br>
<b>SMTP Server</b><br>
<b>Name: Domino.SMTP.Session</b><br>
<b>Checkpointed: Yes</b><br>
SMTP activity is logged at the session level and at the message level. <br>
<br>

<table border="1">
<tr valign="top"><td width="192"><b>Field Name</b></td><td width="126"><b>Type</b></td><td width="286"><b>Description</b></td></tr>

<tr valign="top"><td width="192">OrgName</td><td width="126">Text</td><td width="286">If running on a tiered server, this is the organization name of the connected user.</td></tr>

<tr valign="top"><td width="192">ServerName</td><td width="126">Text</td><td width="286">The name of the server</td></tr>

<tr valign="top"><td width="192">SessionId</td><td width="126">Text</td><td width="286">Unique identifier of the session</td></tr>

<tr valign="top"><td width="192">EventType</td><td width="126">Number</td><td width="286">Open = 1<br>
Checkpoint = 2<br>
Close=4</td></tr>

<tr valign="top"><td width="192">RemoteIP</td><td width="126">Text</td><td width="286">IP address of the connected user.</td></tr>

<tr valign="top"><td width="192">BytesFromServer</td><td width="126">Number</td><td width="286">Number of bytes sent from the server.</td></tr>

<tr valign="top"><td width="192">BytesToServer</td><td width="126">Number</td><td width="286">Number of bytes sent to the server.</td></tr>

<tr valign="top"><td width="192">MessageCount</td><td width="126">Number</td><td width="286">The number of messages sent to the server.</td></tr>

<tr valign="top"><td width="192">RecipientCount</td><td width="126">Number</td><td width="286">The total number of recipients processed during the session</td></tr>

<tr valign="top"><td width="192">TotalOpenTime</td><td width="126">Number</td><td width="286">The length of time that the session was in use. (1/100 second interval).</td></tr>
</table>
</ul>

<ul><b>HTTP activity</b><br>
<b>Name: Domino.HTTP</b><br>
<b>Checkpointed: No</b><br>
We log the things typically logged for HTTP access.  Note that every HTTP request generates an activity record.<br>
<br>

<table border="1">
<tr valign="top"><td width="192"><b>Field Name</b></td><td width="126"><b>Type</b></td><td width="286"><b>Description</b></td></tr>

<tr valign="top"><td width="192">ServerName</td><td width="126">Text</td><td width="286">The name of the HTTP server creating the record.</td></tr>

<tr valign="top"><td width="192">ContentLength</td><td width="126">Number</td><td width="286">The number of bytes returned in response to a request.</td></tr>

<tr valign="top"><td width="192">ReqTimeMs</td><td width="126">Number</td><td width="286">The time in milliseconds needed to service a request.</td></tr>

<tr valign="top"><td width="192">StatusCode</td><td width="126">Text</td><td width="286">The HTTP status code returned in response to a request.</td></tr>

<tr valign="top"><td width="192">TimeStamp</td><td width="126">Text</td><td width="286">The curent time when the request occurred.  (Note that all activity records contain a timestamp in Notes TIMEDATE format passed via the API when reading activity records.)</td></tr>

<tr valign="top"><td width="192">AuthUser</td><td width="126">Text</td><td width="286">The name of the authenticated user.</td></tr>

<tr valign="top"><td width="192">Partner</td><td width="126">Text</td><td width="286">***Don't know how to define this***</td></tr>

<tr valign="top"><td width="192">Referer</td><td width="126">Text</td><td width="286">A URL indicating the source of the link to this request</td></tr>

<tr valign="top"><td width="192">UserAgent</td><td width="126">Text</td><td width="286">The name of the browser making the request.</td></tr>

<tr valign="top"><td width="192">RequestLine</td><td width="126">Text</td><td width="286">The HTTP request sent by the user agent.</td></tr>

<tr valign="top"><td width="192">ContentType</td><td width="126">Text</td><td width="286">The MIME type of the resource returned in response to a request.</td></tr>
</table>
</ul>

<ul><br>
<b>IMAP Activity</b><br>
<b>Name: Domino.IMAP</b><br>
<b>Checkpointed: Yes</b><br>
IMAP activity is logged at the session level. <br>
<br>

<table border="1">
<tr valign="top"><td width="192"><b>Field Name</b></td><td width="126"><b>Type</b></td><td width="286"><b>Description</b></td></tr>

<tr valign="top"><td width="192">OrgName</td><td width="126">Text</td><td width="286">If running on a tiered server, this is the name of the user's organization</td></tr>

<tr valign="top"><td width="192">UserName</td><td width="126">Text</td><td width="286">The name of the authenticated user or Anonymous if the session terminates before authentication.</td></tr>

<tr valign="top"><td width="192">ServerName</td><td width="126">Text</td><td width="286">The name of the server.</td></tr>

<tr valign="top"><td width="192">SessionId</td><td width="126">Text</td><td width="286">Uniquely identifies a session on the server.</td></tr>

<tr valign="top"><td width="192">EventType</td><td width="126">Number</td><td width="286">There are three possible events:<br>
Authorization = 8<br>
Checkpoint = 2<br>
Close = 4</td></tr>

<tr valign="top"><td width="192">RemoteIP</td><td width="126">Text</td><td width="286">The IP address of the client.</td></tr>

<tr valign="top"><td width="192">BytesFromServer</td><td width="126">Number</td><td width="286">The number of bytes that the client has read from the server.</td></tr>

<tr valign="top"><td width="192">BytesToServer</td><td width="126">Number</td><td width="286">The number of bytes that the client has sent to the server.</td></tr>

<tr valign="top"><td width="192">TotalOpenTime</td><td width="126">Number</td><td width="286">The length of time that the session was in use. (1/100 second interval).</td></tr>
</table>
</ul>

<ul><br>
<b>NNTP Activity</b><br>
<b>Name: Domino.NTTP</b><br>
<b>Checkpointed: Yes</b><br>
There are two types records logged for NNTP. The first record type, Domino.NNTP.Session captures session activity generated by a client (either a news reader or another NNTP server). The other record type, Domino.NNTP.Feed, captures activity generated by the server connecting to another server and exchanging news articles.  The information recorded in both cases is identical but the different record names exist so that server initiated sessions can be differentiated from client initiated sessions. 
<p>An ACTIVITY_SESSION_OPEN record is logged in the following cases: (Note that user could be another server in cases 1-3)
<ol type="1">
<li>A user connects and no authentication is required. The record will contain a user name of Anonymous. <i>Or</i>
<li>A user connects and password authentication is required. The record will contain the authenticated user name. <i>Or</i>
<li>A user connects via SSL. The record will contain the authenticated user name. <i>Or</i>
<li>The server starts initiates a newsfeed with another server.</ol>
<br>
An ACTIVITY_SESSION_CHECKPOINT record is logged if the session is active and the length of activity exceeds the activity checkpoint interval.
<p>An ACTIVITY_SESSION_CLOSE record is logged when the session closes.<br>
<br>

<table border="1">
<tr valign="top"><td width="192"><b>Field Name</b></td><td width="126"><b>Type</b></td><td width="286"><b>Description</b></td></tr>

<tr valign="top"><td width="192">OrgName</td><td width="126">Text</td><td width="286">If running on a tiered server, this is the name of the user's organization</td></tr>

<tr valign="top"><td width="192">UserName</td><td width="126">Text</td><td width="286">The name of the authenticated user or Anonymous if the session terminates before authentication.</td></tr>

<tr valign="top"><td width="192">ServerName</td><td width="126">Text</td><td width="286">The name of the server.</td></tr>

<tr valign="top"><td width="192">SessionId</td><td width="126">Text</td><td width="286">Uniquely identifies a session on the server.</td></tr>

<tr valign="top"><td width="192">EventType</td><td width="126">Number</td><td width="286">There are three possible events:<br>
Open = 1<br>
Checkpoint = 2<br>
Close = 4</td></tr>

<tr valign="top"><td width="192">RemoteIP</td><td width="126">Text</td><td width="286">The IP address of the client.</td></tr>

<tr valign="top"><td width="192">BytesFromServer</td><td width="126">Number</td><td width="286">The number of bytes that the client has read from the server.</td></tr>

<tr valign="top"><td width="192">BytesToServer</td><td width="126">Number</td><td width="286">The number of bytes that the client has sent to the server.</td></tr>

<tr valign="top"><td width="192">TotalOpenTime</td><td width="126">Number</td><td width="286">The length of time that the session was in use. (1/100 second interval).</td></tr>
</table>
</ul>

<ul><br>
<b>LDAP Activity</b><br>
The LDAP server has been instrumented to log information about every request. Since each LDAP request has a different structure, every request uses a different activity logging type. 
<p><b>Bind Activity</b><br>
<b>Activity Name: Domino.LDAP.Bind</b><br>
<b>Checkpointed: No</b><br>
<br>

<table border="1">
<tr valign="top"><td width="192"><b>Field Name</b></td><td width="126"><b>Type</b></td><td width="488"><b>Description</b></td></tr>

<tr valign="top"><td width="192">OrgName</td><td width="126">Text</td><td width="488">If running on a tiered server, this is the name of the user's organization</td></tr>

<tr valign="top"><td width="192">UserName</td><td width="126">Text</td><td width="488">The name of the authenticated user or Anonymous if the session terminates before authentication.</td></tr>

<tr valign="top"><td width="192">ServerName</td><td width="126">Text</td><td width="488">Name of the server.</td></tr>

<tr valign="top"><td width="192">RemoteIP</td><td width="126">Text</td><td width="488">The IP address of the client.</td></tr>

<tr valign="top"><td width="192">Version</td><td width="126">Text</td><td width="488">The version of the LDAP protocol being used.[1]</td></tr>

<tr valign="top"><td width="192">Name</td><td width="126">Text</td><td width="488">The name that the client is using to bind.[1]</td></tr>

<tr valign="top"><td width="192">Method</td><td width="126">Text</td><td width="488">An ASCII encoding of the authentication method being used.<br>
&quot;80&quot; = Simple authentication<br>
&quot;81&quot; = Reserved for future use.<br>
&quot;82&quot; = Reserved for future use.<br>
&quot;a3&quot; = SASL authentication</td></tr>

<tr valign="top"><td width="192">ResultCode</td><td width="126">Text</td><td width="488">The LDAP result code returned to the client.[1]</td></tr>

<tr valign="top"><td width="192">ErrorMessage</td><td width="126">Text</td><td width="488">The LDAP error message returned to the client.[1]</td></tr>
</table>
</ul>

<ul><br>
<b>Unbind Activity</b><br>
<b>Activity Name: Domino.LDAP.Unbind</b><br>
<b>Checkpointed: No</b><br>
<br>

<table border="1">
<tr valign="top"><td width="192"><b>Field Name</b></td><td width="126"><b>Type</b></td><td width="488"><b>Description</b></td></tr>

<tr valign="top"><td width="192">OrgName</td><td width="126">Text</td><td width="488">If running on a tiered server, this is the name of the user's organization</td></tr>

<tr valign="top"><td width="192">UserName</td><td width="126">Text</td><td width="488">The name of the authenticated user or Anonymous if the session terminates before authentication.</td></tr>

<tr valign="top"><td width="192">ServerName</td><td width="126">Text</td><td width="488">The name of the server.</td></tr>

<tr valign="top"><td width="192">RemoteIP</td><td width="126">Text</td><td width="488">The IP address of the client.</td></tr>

<tr valign="top"><td width="192">ResultCode</td><td width="126">Text</td><td width="488">The LDAP result code returned to the client.[1]</td></tr>

<tr valign="top"><td width="192">ErrorMessage</td><td width="126">Text</td><td width="488">The LDAP error message returned to the client.[1]</td></tr>
</table>
</ul>

<ul><br>
<b>Search Activity</b><br>
<b>Activity name: Domino.LDAP.Search</b><br>
<b>Checkpointed: No</b><br>
<br>

<table border="1">
<tr valign="top"><td width="192"><b>Field Name</b></td><td width="126"><b>Type</b></td><td width="488"><b>Description</b></td></tr>

<tr valign="top"><td width="192">OrgName</td><td width="126">Text</td><td width="488">If running on a tiered server, this is the name of the user's organization</td></tr>

<tr valign="top"><td width="192">UserName</td><td width="126">Text</td><td width="488">The name of the authenticated user or Anonymous if the session terminates before authentication.</td></tr>

<tr valign="top"><td width="192">ServerName</td><td width="126">Text</td><td width="488">The name of the server.</td></tr>

<tr valign="top"><td width="192">RemoteIP</td><td width="126">Text</td><td width="488">The IP address of the client.</td></tr>

<tr valign="top"><td width="192">BaseObject</td><td width="126">Text</td><td width="488">The base object entry relative to which the search is performed. [1]</td></tr>

<tr valign="top"><td width="192">Scope</td><td width="126">Text</td><td width="488">ASCII digit indicating the type of search. '0' = base, '1' = single level, '2' = subtree. [1]</td></tr>

<tr valign="top"><td width="192">DerefAliases</td><td width="126">Text</td><td width="488">ASCII digit indicating how alias objects are handled. '0' - Never, '1' Deref in searching, '2 Deref finding base object. [1]</td></tr>

<tr valign="top"><td width="192">SizeLimit</td><td width="126">Number</td><td width="488">Indicates the max number entries that the client requested.[1]</td></tr>

<tr valign="top"><td width="192">TimeLimit</td><td width="126">Number</td><td width="488">Indicates the max time in seconds the client has requested.[1]</td></tr>

<tr valign="top"><td width="192">TypesOnly</td><td width="126">Text</td><td width="488">Indicator that the search should only contain attribute types. ASCII '1' if true, ASCII '0' if false.[1]</td></tr>

<tr valign="top"><td width="192">Filter</td><td width="126">Text</td><td width="488">LDAP query filter. [1]</td></tr>

<tr valign="top"><td width="192">Attributes</td><td width="126">Text</td><td width="488">A list of attributes to be returned for each entry found. [1]</td></tr>

<tr valign="top"><td width="192">SearchTime</td><td width="126">Number</td><td width="488">The time in milliseconds that the search operation (including returning all values) required.</td></tr>

<tr valign="top"><td width="192">DirectoryNames</td><td width="126">Text List</td><td width="488">A list of the directories searched.</td></tr>

<tr valign="top"><td width="192">EntriesSent</td><td width="126">Number</td><td width="488">The number of entries sent to the client.</td></tr>

<tr valign="top"><td width="192">BytesSent</td><td width="126">Number</td><td width="488">The total number of bytes sent to the client.</td></tr>

<tr valign="top"><td width="192">ResultCode</td><td width="126">Text</td><td width="488">The LDAP result code returned to the client.[1]</td></tr>

<tr valign="top"><td width="192">ErrorMessage</td><td width="126">Text</td><td width="488">The LDAP error message returned to the client.[1]</td></tr>
</table>
</ul>

<ul><br>
<b>Modify Activity</b><br>
<b>Activity name: Domino.LDAP.Modify</b><br>
<b>Checkpointed: No</b><br>
<br>

<table border="1">
<tr valign="top"><td width="192"><b>Field Name</b></td><td width="126"><b>Type</b></td><td width="488"><b>Description</b></td></tr>

<tr valign="top"><td width="192">OrgName</td><td width="126">Text</td><td width="488">If running on a tiered server, this is the name of the user's organization</td></tr>

<tr valign="top"><td width="192">UserName</td><td width="126">Text</td><td width="488">The name of the authenticated user or Anonymous if the session terminates before authentication.</td></tr>

<tr valign="top"><td width="192">ServerName</td><td width="126">Text</td><td width="488">The name of the server.</td></tr>

<tr valign="top"><td width="192">RemoteIP</td><td width="126">Text</td><td width="488">The IP address of the client.</td></tr>

<tr valign="top"><td width="192">Object</td><td width="126">Text</td><td width="488">The DN (Distinguished name) of the entry to be modified.[1]</td></tr>

<tr valign="top"><td width="192">Operations</td><td width="126">Text List</td><td width="488">A list of operations to be performed on the entry. Encoded as ASCII digits: '0' = add, '1' = delete, '2' = replace.[1]</td></tr>

<tr valign="top"><td width="192">Attributes</td><td width="126">Text List</td><td width="488">A list of attribute names that corresponds to the operations list.[1]</td></tr>

<tr valign="top"><td width="192">Values</td><td width="126">Text List</td><td width="488">A list of values that corresponds to the attributes list. Note that each of the values could be a list. Thus, the values themselves are encoded as comma separated lists. All strings are double quoted to avoid ambiguity arising from commas in the data. Note that values associated with the userPassword attribute are not logged. Binary fields are also not logged.</td></tr>

<tr valign="top"><td width="192">DirectoryNames</td><td width="126">Text List</td><td width="488">The list of directories that this entry was modified in.</td></tr>

<tr valign="top"><td width="192">EntriesUpdated</td><td width="126">Number</td><td width="488">The total number of entries modified.</td></tr>

<tr valign="top"><td width="192">BytesReceived</td><td width="126">Number</td><td width="488">The number of bytes sent to the server.</td></tr>

<tr valign="top"><td width="192">ResultCode</td><td width="126">Text</td><td width="488">The LDAP result code returned to the client.[1]</td></tr>

<tr valign="top"><td width="192">ErrorMessage</td><td width="126">Text</td><td width="488">The LDAP error message returned to the client.[1]</td></tr>
</table>
</ul>

<ul><br>
<b>Add activity</b><br>
<b>Activity name:Domino.LDAP.Add</b><br>
<b>Checkpointed: No</b><br>
<br>

<table border="1">
<tr valign="top"><td width="192"><b>Field Name</b></td><td width="126"><b>Type</b></td><td width="488"><b>Description</b></td></tr>

<tr valign="top"><td width="192">OrgName</td><td width="126">Text</td><td width="488">If running on a tiered server, this is the name of the user's organization</td></tr>

<tr valign="top"><td width="192">UserName</td><td width="126">Text</td><td width="488">The name of the authenticated user or Anonymous if the session terminates before authentication.</td></tr>

<tr valign="top"><td width="192">ServerName</td><td width="126">Text</td><td width="488">The name of the server.</td></tr>

<tr valign="top"><td width="192">RemoteIP</td><td width="126">Text</td><td width="488">The IP address of the client.</td></tr>

<tr valign="top"><td width="192">Object</td><td width="126">Text</td><td width="488">The DN of the object to be added.[1]</td></tr>

<tr valign="top"><td width="192">Attributes</td><td width="126">Text List</td><td width="488">A list of attribute names that corresponds to the operations list.[1]</td></tr>

<tr valign="top"><td width="192">Values</td><td width="126">Text List</td><td width="488">A list of values that corresponds to the attributes list. Note that each of the values could be a list. Thus, the values themselves are encoded as comma separated lists. All strings are double quoted to avoid ambiguity arising from commas in the data. Note that values associated with the userPassword attribute are not logged. Binary fields are also not logged.</td></tr>

<tr valign="top"><td width="192">DirectoryNames</td><td width="126">Text List</td><td width="488">A list of directories that the object was added to.</td></tr>

<tr valign="top"><td width="192">EntriesUpdated</td><td width="126">Number</td><td width="488">The total number of entries modified.</td></tr>

<tr valign="top"><td width="192">BytesReceived</td><td width="126">Number</td><td width="488">The number of bytes sent to the server.</td></tr>

<tr valign="top"><td width="192">ResultCode</td><td width="126">Text</td><td width="488">The LDAP result code returned to the client.[1]</td></tr>

<tr valign="top"><td width="192">ErrorMessage</td><td width="126">Text</td><td width="488">The LDAP error message returned to the client.[1]</td></tr>
</table>
</ul>

<ul><br>
<b>ModifyDN Activity</b><br>
<b>Activity type: Domino.LDAP.ModifyDN</b><br>
<b>Checkpointed: No</b><br>
<br>

<table border="1">
<tr valign="top"><td width="192"><b>Field Name</b></td><td width="126"><b>Type</b></td><td width="488"><b>Description</b></td></tr>

<tr valign="top"><td width="192">OrgName</td><td width="126">Text</td><td width="488">If running on a tiered server, this is the name of the user's organization</td></tr>

<tr valign="top"><td width="192">UserName</td><td width="126">Text</td><td width="488">The name of the authenticated user or Anonymous if the session terminates before authentication.</td></tr>

<tr valign="top"><td width="192">ServerName</td><td width="126">Text</td><td width="488">The name of the server.</td></tr>

<tr valign="top"><td width="192">RemoteIP</td><td width="126">Text</td><td width="488">The IP address of the client.</td></tr>

<tr valign="top"><td width="192">Entry</td><td width="126">Text</td><td width="488">The directory entry to be modified.[1]</td></tr>

<tr valign="top"><td width="192">NewRDN</td><td width="126">Text</td><td width="488">The new RDN (Relative Distinguished Name) of the entry. [1]</td></tr>

<tr valign="top"><td width="192">DeleteOldRDN </td><td width="126">Text</td><td width="488">1 if the old entry is to be deleted, 0 if not. Encoded as an ASCII digit.[1]</td></tr>

<tr valign="top"><td width="192">NewSuperior</td><td width="126">Text</td><td width="488">Name of the new parent entry (if any).[1]</td></tr>

<tr valign="top"><td width="192">DirectoryNames</td><td width="126">Text List</td><td width="488">A list of directories that the object was added to.</td></tr>

<tr valign="top"><td width="192">EntriesUpdated</td><td width="126">Number</td><td width="488">The total number of entries modified.</td></tr>

<tr valign="top"><td width="192">BytesReceived</td><td width="126">Number</td><td width="488">The number of bytes sent to the server.</td></tr>

<tr valign="top"><td width="192">ResultCode</td><td width="126">Text</td><td width="488">The LDAP result code returned to the client.[1]</td></tr>

<tr valign="top"><td width="192">ErrorMessage</td><td width="126">Text</td><td width="488">The LDAP error message returned to the client.[1]</td></tr>
</table>
</ul>

<ul><br>
<b>Delete Activity</b><br>
<b>Activity type: Domino.LDAP.Delete</b><br>
<b>Checkpointed: No</b><br>
<br>

<table border="1">
<tr valign="top"><td width="192"><b>Field Name</b></td><td width="126"><b>Type</b></td><td width="488"><b>Description</b></td></tr>

<tr valign="top"><td width="192">OrgName</td><td width="126">Text</td><td width="488">If running on a tiered server, this is the name of the user's organization</td></tr>

<tr valign="top"><td width="192">UserName</td><td width="126">Text</td><td width="488">The name of the authenticated user or Anonymous if the session terminates before authentication.</td></tr>

<tr valign="top"><td width="192">ServerName</td><td width="126">Text</td><td width="488">The name of the server.</td></tr>

<tr valign="top"><td width="192">RemoteIP</td><td width="126">Text</td><td width="488">The IP address of the client.</td></tr>

<tr valign="top"><td width="192">Object</td><td width="126">Text</td><td width="488">The DN of the Object to be deleted[1]</td></tr>

<tr valign="top"><td width="192">DirectoryNames</td><td width="126">Text List</td><td width="488">A list of directories that the object was added to.</td></tr>

<tr valign="top"><td width="192">EntriesUpdated</td><td width="126">Number</td><td width="488">The total number of entries modified.</td></tr>

<tr valign="top"><td width="192">BytesReceived</td><td width="126">Number</td><td width="488">The number of bytes sent to the server.</td></tr>

<tr valign="top"><td width="192">ResultCode</td><td width="126">Text</td><td width="488">The LDAP result code returned to the client.[1]</td></tr>

<tr valign="top"><td width="192">ErrorMessage</td><td width="126">Text</td><td width="488">The LDAP error message returned to the client.[1]</td></tr>
</table>
</ul>

<ul><br>
<b>Compare Activity</b><br>
<b>Activity name: Domino.LDAP.Compare</b><br>
<b>Checkpointed: No</b><br>
<br>

<table border="1">
<tr valign="top"><td width="192"><b>Field Name</b></td><td width="126"><b>Type</b></td><td width="488"><b>Description</b></td></tr>

<tr valign="top"><td width="192">OrgName</td><td width="126">Text</td><td width="488">If running on a tiered server, this is the name of the user's organization</td></tr>

<tr valign="top"><td width="192">UserName</td><td width="126">Text</td><td width="488">The name of the authenticated user or Anonymous if the session terminates before authentication.</td></tr>

<tr valign="top"><td width="192">ServerName</td><td width="126">Text</td><td width="488">The name of the server.</td></tr>

<tr valign="top"><td width="192">RemoteIP</td><td width="126">Text</td><td width="488">The IP address of the client.</td></tr>

<tr valign="top"><td width="192">Object</td><td width="126">Text</td><td width="488">The DN of the Object to be deleted[1]</td></tr>

<tr valign="top"><td width="192">Attribute</td><td width="126">Text</td><td width="488">The attribute portion of the attribute value assertion.[1]</td></tr>

<tr valign="top"><td width="192">Value</td><td width="126">Text</td><td width="488">The value portion of the attribute value assertion.[1]</td></tr>

<tr valign="top"><td width="192">DirectoryNames</td><td width="126">Text List</td><td width="488">A list of directories that the object was added to.</td></tr>

<tr valign="top"><td width="192">EntriesUpdated</td><td width="126">Number</td><td width="488">The total number of entries modified.</td></tr>

<tr valign="top"><td width="192">BytesReceived</td><td width="126">Number</td><td width="488">The number of bytes sent to the server.</td></tr>

<tr valign="top"><td width="192">ResultCode</td><td width="126">Text</td><td width="488">The LDAP result code returned to the client.[1]</td></tr>

<tr valign="top"><td width="192">ErrorMessage</td><td width="126">Text</td><td width="488">The LDAP error message returned to the client.[1]</td></tr>
</table>
</ul>

<ul><br>
<b>Abandon Activity</b><br>
<b>Activity name: Domino.LDAP.Abandon</b><br>
<b>Checkpointed: No</b><br>
<br>

<table border="1">
<tr valign="top"><td width="192"><b>Field Name</b></td><td width="126"><b>Type</b></td><td width="488"><b>Description</b></td></tr>

<tr valign="top"><td width="192">OrgName</td><td width="126">Text</td><td width="488">If running on a tiered server, this is the name of the user's organization</td></tr>

<tr valign="top"><td width="192">UserName</td><td width="126">Text</td><td width="488">The name of the authenticated user or Anonymous if the session terminates before authentication.</td></tr>

<tr valign="top"><td width="192">ServerName</td><td width="126">Text</td><td width="488">The name of the server.</td></tr>

<tr valign="top"><td width="192">RemoteIP</td><td width="126">Text</td><td width="488">The IP address of the client.</td></tr>

<tr valign="top"><td width="192">MsgId</td><td width="126">Text</td><td width="488">The message ID of the command to abandon.[1]</td></tr>

<tr valign="top"><td width="192">ResultCode</td><td width="126">Text</td><td width="488">The LDAP result code returned to the client.[1]</td></tr>

<tr valign="top"><td width="192">ErrorMessage</td><td width="126">Text</td><td width="488">The LDAP error message returned to the client.[1]</td></tr>
</table>
</ul>

<ul><br>
<b>Extended Activity</b><br>
<b>Activity name: Domino.LDAP.Extended</b><br>
<b>Checkpointed: No</b><br>
<br>

<table border="1">
<tr valign="top"><td width="192"><b>Field Name</b></td><td width="126"><b>Type</b></td><td width="488"><b>Description</b></td></tr>

<tr valign="top"><td width="192">OrgName</td><td width="126">Text</td><td width="488">If running on a tiered server, this is the name of the user's organization</td></tr>

<tr valign="top"><td width="192">UserName</td><td width="126">Text</td><td width="488">The name of the authenticated user or Anonymous if the session terminates before authentication.</td></tr>

<tr valign="top"><td width="192">ServerName</td><td width="126">Text</td><td width="488">The name of the server.</td></tr>

<tr valign="top"><td width="192">RemoteIP</td><td width="126">Text</td><td width="488">The IP address of the client.</td></tr>

<tr valign="top"><td width="192">RequestName</td><td width="126">Text</td><td width="488">The name of the extended command. [1]</td></tr>

<tr valign="top"><td width="192">ResultCode</td><td width="126">Text</td><td width="488">The LDAP result code returned to the client.[1]</td></tr>

<tr valign="top"><td width="192">ErrorMessage</td><td width="126">Text</td><td width="488">The LDAP error message returned to the client.[1]</td></tr>
</table>

<p><b>REPLICA activity</b><br>
<b>Activity name: Domino.REPLICA</b><br>
<b>Checkpointed: No</b><br>
The replica task creates an activity record for every database that it replicates with. 
<table border="1">
<tr valign="top"><td width="192"><b>Field Name</b></td><td width="126"><b>Type</b></td><td width="286"><b>Description</b></td></tr>

<tr valign="top"><td width="192">SessionId</td><td width="126">Text</td><td width="286">Unique identifier of the replication session.</td></tr>

<tr valign="top"><td width="192">SourceServer</td><td width="126">Text</td><td width="286">Server from which documents are being pulled.</td></tr>

<tr valign="top"><td width="192">SourcePath</td><td width="126">Text</td><td width="286">Database path and filename on source server.</td></tr>

<tr valign="top"><td width="192">DestServer</td><td width="126">Text</td><td width="286">Server to which documents are being written.</td></tr>

<tr valign="top"><td width="192">DestPath</td><td width="126">Text</td><td width="286">Database path and filename on source server.</td></tr>

<tr valign="top"><td width="192">ReplicaId</td><td width="126">Text</td><td width="286">Replica Id of the database.</td></tr>

<tr valign="top"><td width="192">BytesIn</td><td width="126">Number</td><td width="286">Number of bytes read by the replicator task.</td></tr>

<tr valign="top"><td width="192">BytesOut</td><td width="126">Number</td><td width="286">Number of bytes written by the replicator task</td></tr>

<tr valign="top"><td width="192">Priority</td><td width="126">Text</td><td width="286">The replication priority setting on the database. Encoded as an ASCII digit.</td></tr>
</table>
</ul>

<ul><b>AMGR (Agent Manager) activity</b><br>
<b>Activity name: Domino.AGENT</b><br>
<b>Checkpointed: No</b><br>
The agent manager creates an activity record every time a scheduled agent is run.<br>
<br>

<table border="1">
<tr valign="top"><td width="192"><b>Field Name</b></td><td width="126"><b>Type</b></td><td width="286"><b>Description</b></td></tr>

<tr valign="top"><td width="192">UserName</td><td width="126">Text</td><td width="286">The name of the user that created the agent.</td></tr>

<tr valign="top"><td width="192">TaskName</td><td width="126">Text</td><td width="286">The name of the agent.</td></tr>

<tr valign="top"><td width="192">DatabaseName</td><td width="126">Text</td><td width="286">The name of the database that contains the agent.</td></tr>

<tr valign="top"><td width="192">ElapsedRunTime</td><td width="126">Number</td><td width="286">The time in milliseconds that the agent ran.</td></tr>
</table>
</ul>
<br>
<br>
For a complete description of the activity logging services, including configuration instructions, please refer to the <i>Domino Administration Help</i> documentation.
---
