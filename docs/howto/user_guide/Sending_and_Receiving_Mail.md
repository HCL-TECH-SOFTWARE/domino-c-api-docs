##### Chapter 10-3
##### Sending and Receiving Mail

This chapter explains how to use NSF functions and Mail Gateway API functions to send and receive Domino mail messages. <br>
<br>
<b><font size="5" color="#000080">Sending Mail</font></b><br>
<br>
The required steps for sending a document using the HCL C API for Domino and Notes are:<br>

<ol type="1">
<li>Create a document in the mail.box file on a Domino mail server or locally.
<li>Append a valid Recipients field to the document.
<li>Update the document in an active mail.box file.</ol>
<br>
For details about what constitutes a valid Recipients field, see the &quot;Domino Mail Architecture&quot; chapter. The Recipients field is the only field required by the router. The document may contain any number of other fields.<br>
<br>
Most mail programs perform more than the minimum steps listed above. Typical mail messages contain fields named From, SendTo, Subject, Date, and Body. The example mail programs described below append these other items to the document before sending the document as a mail message.<br>
<br>
<br>
<b><font size="4" color="#000080">Example Using NSF Functions</font></b><br>
<br>
The sample program SENDMEMO, a standalone API program, uses NSF functions to create and send a mail message. <br>
<br>
SENDMEMO is a character-mode program. Its source code is in the directory \samples\mail\sendmemo.<br>
<br>
<b><font color="#000080">SENDMEMO: Initialization</font></b><br>
<b><font color="#000080"> </font></b> <br>
SENDMEMO uses the following algorithm:<br>

<ol type="1">
<li>Obtain SendTo, Subject, and Body from the command line.
<li>Use SECKFMUserInfo to obtain the name of the user running the program. Use this name in the From field.
<li>Use OSGetEnvironmentString to get the name of the mail server from the environment variable &quot;MailServer&quot; stored in notes.ini.
<li>Use OSGetEnvironmentInt to see if, in the event of multiple mail.box files, the &quot;mail.box&quot; is active. 
<li>Use OSPathNetConstruct to construct the network path to a mail.box file. 
<li>Call NSFDbOpen to open the mail file on the mail server or locally. This yields &lt;hMailBox&gt;, the handle to the open mail box.
<li>Get the current time/date to use in the ComposedDate item.
<li>Call NSFNoteCreate to create a message document in the mail file. This yields &lt;hMemo&gt;, the handle to the message document.</ol>

<table border="1">
<tr valign="top"><td width="648"><b>sendmemo.c - Initialization Steps</b></td></tr>
</table>
<tt>int main(int argc, char * argv[])</tt><tt><font size="2"><br>
{<br>
 &nbsp; &nbsp;STATUS &nbsp; &nbsp; &nbsp;error = NOERROR;<br>
 &nbsp; &nbsp;char &nbsp; &nbsp; &nbsp; *szSendTo;<br>
 &nbsp; &nbsp;char &nbsp; &nbsp; &nbsp; *szSubject;<br>
 &nbsp; &nbsp;char &nbsp; &nbsp; &nbsp; *szBody;<br>
 &nbsp; &nbsp;char &nbsp; &nbsp; &nbsp; &nbsp;szFrom[MAXUSERNAME+1];<br>
 &nbsp; &nbsp;char &nbsp; &nbsp; &nbsp; &nbsp;szMailServerName[MAXUSERNAME+1];<br>
 &nbsp; &nbsp;char &nbsp; &nbsp; &nbsp; &nbsp;szMailFileName[MAXUSERNAME+1] = MAILBOX_NAME;<br>
 &nbsp; &nbsp;char &nbsp; &nbsp; &nbsp; &nbsp;szMailBoxPath[MAXPATH+1];<br>
 &nbsp; &nbsp;DBHANDLE &nbsp; &nbsp;hMailBox;<br>
 &nbsp; &nbsp;NOTEHANDLE &nbsp;hMemo;<br>
 &nbsp; &nbsp;TIMEDATE &nbsp; &nbsp;tdCurrent;<br>
 &nbsp; &nbsp;BLOCKID &nbsp; &nbsp; bidItem;<br>
 &nbsp; &nbsp;WORD &nbsp; &nbsp; &nbsp; &nbsp;wDataType;<br>
 &nbsp; &nbsp;BLOCKID &nbsp; &nbsp; bidValue;<br>
 &nbsp; &nbsp;DWORD &nbsp; &nbsp; &nbsp; dwValueLen;<br>
 &nbsp; &nbsp;HANDLE &nbsp; &nbsp; &nbsp;hRichTextBody;<br>
 &nbsp; &nbsp;DWORD &nbsp; &nbsp; &nbsp; dwRichTextLen;<br>
 &nbsp; &nbsp;BYTE &nbsp; &nbsp; &nbsp;* pRichTextBody;</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; if (argc != 4)<br>
 &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp; &nbsp;printf (&quot;Error: incorrect syntax.\n&quot;);<br>
 &nbsp; &nbsp; &nbsp; &nbsp;printf (&quot;%s &nbsp;\&quot;to\&quot; \&quot;subject\&quot; \&quot;body\&quot;\n&quot;, argv[0]);<br>
 &nbsp; &nbsp; &nbsp; &nbsp;return (NOERROR);<br>
 &nbsp; &nbsp;}<br>
 &nbsp; &nbsp;szSendTo = argv[1];<br>
 &nbsp; &nbsp;szSubject = argv[2];<br>
 &nbsp; &nbsp;szBody = argv[3];</font></tt><br>
<br>
<font face="Courier New">    </font><tt>if (error = NotesInitExtended (argc, argv))</tt><br>
<tt>&nbsp; &nbsp; {</tt><br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; printf(&quot;\n Unable to initialize Notes.\n&quot;);</tt><br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; return (1);</tt><br>
<tt>&nbsp; &nbsp; }</tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; if (error = SECKFMUserInfo(KFM_ui_GetUserInfo, szFrom, NULL))<br>
 &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp; &nbsp;printf (&quot;Error: unable to get user name.\n&quot;);<br>
 &nbsp; &nbsp; &nbsp; &nbsp;</font></tt><font face="Courier New">goto Done;</font><tt><font size="2"><br>
 &nbsp; &nbsp;}<br>
 &nbsp; &nbsp;if (!OSGetEnvironmentString(&quot;MAILSERVER&quot;, szMailServerName, MAXUSERNAME))<br>
 &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp; &nbsp;printf (&quot;\nUnable to get mail server name ...\n\n Adding message local 'mail.box' file ...\n\n&quot;);<br>
 &nbsp; &nbsp; &nbsp; &nbsp;strcpy(szMailServerName,&quot;&quot;);</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; /* In the event of multiple &quot;mail.box&quot; files, if the NOTES.INI parameter<br>
 &nbsp; &nbsp; &nbsp; &nbsp;&quot;MAIL_ENABLE_MAILBOX_COMPATIBILITY =1&quot; is set, then the file &quot;mail.box&quot; will be used,<br>
 &nbsp; &nbsp; &nbsp; &nbsp;otherwise &quot;mail2.box&quot; will be used. */<br>
 &nbsp; &nbsp; &nbsp; &nbsp;if (!OSGetEnvironmentInt(&quot;MAIL_ENABLE_MAILBOX_COMPATIBILITY&quot;))<br>
 &nbsp; &nbsp; &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; printf (&quot;\nEnable mailbox parameter is not set ...\n\n Adding message to local 'mail2.box' file ...\n\n&quot;);<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; strcpy(szMailFileName, &quot;mail2.box&quot;);<br>
 &nbsp; &nbsp; &nbsp; &nbsp;}<br>
 &nbsp; &nbsp;}</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; /* In the event of multiple &quot;mail.box&quot; databases, ensure message is successfully deposited. */<br>
 &nbsp; &nbsp;do<br>
 &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp; &nbsp;OSPathNetConstruct( NULL, &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; /* port name &nbsp;*/<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;szMailServerName,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;szMailFileName,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;szMailBoxPath);</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; if (error = NSFDbOpen (szMailBoxPath, &amp;hMailBox))<br>
 &nbsp; &nbsp; &nbsp; &nbsp;{</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; /* If multiple mail.box files do not exist, place memo in standard &quot;mail.box&quot; file. */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;if ((error == ERR_NOEXIST) &amp;&amp; (!strcmp (szMailFileName, &quot;mail2.box&quot;)))<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; strcpy(szMailFileName, &quot;mail.box&quot;);<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;}<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;else<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; printf (&quot;Error: unable to open '%s'.\n&quot;, szMailBoxPath);<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; </font></tt><tt>goto Done;</tt><tt><font size="2"><br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;}<br>
 &nbsp; &nbsp; &nbsp; &nbsp;}<br>
 &nbsp; &nbsp;}<br>
 &nbsp; &nbsp;while (error);</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; OSCurrentTIMEDATE(&amp;tdCurrent);</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; if (error = NSFNoteCreate(hMailBox, &amp;hMemo))<br>
 &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp; &nbsp;printf (&quot;Error: unable to create memo in %s.\n&quot;, szMailBoxPath);<br>
 &nbsp; &nbsp; &nbsp; &nbsp;</font></tt><tt>goto Done1;</tt><tt><font size="2"><br>
 &nbsp; &nbsp;}</font></tt><br>

<ul><br>
</ul>
<b><font color="#000080">SENDMEMO: Form, SendTo, and Recipients</font></b><br>
<br>
After obtaining all the inputs and creating a document in a mail.box file, SENDMEMO appends data items to the document, including the Form, SendTo, and Recipients fields.<br>

<ol type="1">
<li>Append the Form item to the document. The standard memo form is Memo. 
<li>Append the SendTo item (obtained from the command line) to the document.
<li>Call NSFItemSetText to append the Recipients item to the message. If more than one recipient were supported, you would need to call NSFItemCreateTextList. </ol>

<table border="1">
<tr valign="top"><td width="648"><b>sendmemo.c - Form, SendTo, and Recipients Items</b></td></tr>
</table>
<br>
<tt><font size="2">&nbsp; &nbsp; if (error = NSFItemSetText( hMemo, <br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;FIELD_FORM, &nbsp; &nbsp; /* &quot;Form&quot; */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;MAIL_MEMO_FORM, /* &quot;Memo&quot; = Standard memo */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;MAXWORD))<br>
 &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp; &nbsp;printf (&quot;Error: unable to set item '%s' into memo.\n&quot;, FIELD_FORM);<br>
 &nbsp; &nbsp; &nbsp; &nbsp;</font></tt><tt>goto Done2;</tt><tt><font size="2"><br>
 &nbsp; &nbsp;}</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; if (error = NSFItemSetText( hMemo, <br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;MAIL_SENDTO_ITEM, &nbsp;/* &quot;SendTo&quot; */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;szSendTo, <br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;MAXWORD))<br>
 &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp; &nbsp;printf (&quot;Error: unable to set item '%s' into memo.\n&quot;, <br>
 &nbsp; &nbsp; &nbsp; &nbsp;</font></tt><tt>goto Done2;</tt><tt><font size="2"><br>
 &nbsp; &nbsp;}</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; if (error = NSFItemSetText( hMemo, /* use NSFItemCreateTextList if &gt; 1*/<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;MAIL_RECIPIENTS_ITEM, &nbsp; /* &quot;Recipients&quot; */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;szSendTo, <br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;MAXWORD))<br>
 &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp; &nbsp;printf (&quot;Error: unable to set item '%s' into memo.\n&quot;, <br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;MAIL_RECIPIENTS_ITEM);<br>
 &nbsp; &nbsp; &nbsp; &nbsp;</font></tt><tt>goto Done2;</tt><tt><font size="2"><br>
 &nbsp; &nbsp;}</font></tt>
<ul></ul>
For simplicity, SENDMEMO assumes that the SendTo string specified on the command line constitutes a valid Recipients field. More sophisticated mail programs might parse the specified string to handle multiple recipients. To handle more than one recipient, the Recipients field must be a text list field. Also, more sophisticated mail programs should verify that the SendTo string matches a name in the Domino Directory. Note that SENDMEMO does not check the SendTo field.<br>
<br>
<b><font color="#000080">SENDMEMO: The Body Field</font></b>
<ul></ul>

<ol type="1">
<li>Append the following fields to the document: <br>
	- From<br>
	- Subject<br>
	- DeliveryPriority<br>
	- DeliveryReport<br>
	- ReturnReceipt<br>
	- ComposedDate<br>
The source code for this step is not shown here. 
<li>Create a rich text body item by first creating a temporary text body item, then converting the item to type composite. Append the composite item to the document as the Body field, then delete the temporary text item.
<table border="1">
<tr valign="top"><td width="648"><b>sendmemo.c - The Body Field</b></td></tr>
</table>
</ol>
<tt><font size="2">&nbsp; &nbsp; if (error = NSFItemSetText( hMemo, <br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;TEMP_MAIL_BODY_ITEM, &nbsp;/* &quot;TempBody&quot; */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;szBody, <br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;MAXWORD))<br>
 &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp; &nbsp;printf (&quot;Error: unable to set item '%s' into memo.\n&quot;, <br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;TEMP_MAIL_BODY_ITEM);<br>
 &nbsp; &nbsp; &nbsp; &nbsp;</font></tt><tt>goto Done2;</tt><tt><font size="2"><br>
 &nbsp; &nbsp;}</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; if (error = NSFItemInfo(hMemo, <br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;TEMP_MAIL_BODY_ITEM, <br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;strlen(TEMP_MAIL_BODY_ITEM),<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&amp;bidItem, &amp;wDataType, &amp;bidValue, &amp;dwValueLen))<br>
 &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp; &nbsp;printf (&quot;Error: unable to get info re item '%s'.\n&quot;, <br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;TEMP_MAIL_BODY_ITEM);<br>
 &nbsp; &nbsp; &nbsp; &nbsp;</font></tt><tt>goto Done2;</tt><tt><font size="2">&nbsp; &nbsp; &nbsp; <br>
 &nbsp; &nbsp;}</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; if (error = ConvertItemToComposite(bidValue, dwValueLen, <br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;DEFAULT_FONT_ID, &quot;&quot;, PARADELIM_BLANKLINE, <br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&amp;hRichTextBody, &amp;dwRichTextLen, <br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;FALSE, NULL, 0, FALSE))<br>
 &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp; &nbsp;printf (&quot;Error: unable to convert text item to composite.\n&quot;);<br>
 &nbsp; &nbsp; &nbsp; &nbsp;</font></tt><tt>goto Done2;</tt><tt><font size="2">&nbsp; &nbsp;<br>
 &nbsp; &nbsp;}</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; pRichTextBody = OSLockObject(hRichTextBody) ;<br>
 &nbsp; &nbsp;pRichTextBody += sizeof(WORD);<br>
 &nbsp; &nbsp;dwRichTextLen -= sizeof(WORD);</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; if (error = NSFItemAppend(hMemo, 0, MAIL_BODY_ITEM, <br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;strlen(MAIL_BODY_ITEM), TYPE_COMPOSITE, pRichTextBody,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;dwRichTextLen))<br>
 &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp; &nbsp;printf (&quot;Error: unable to append item '%s' to note.\n&quot;, <br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;MAIL_BODY_ITEM);<br>
 &nbsp; &nbsp; &nbsp; &nbsp;OSUnlockObject(hRichTextBody);</font></tt><br>
<font face="Courier New">        </font><tt>OSMemFree(hRichTextBody);</tt><br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; goto Done2;</tt><tt><font size="2">&nbsp; </font></tt><tt><font size="2">&nbsp; &nbsp; <br>
 &nbsp; &nbsp;}<br>
 &nbsp; &nbsp; &nbsp; &nbsp;<br>
 &nbsp; &nbsp;OSUnlockObject(hRichTextBody) ;</font></tt><br>
<tt>&nbsp; &nbsp; OSMemFree(hRichTextBody);</tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; if (error = NSFItemDelete(hMemo, TEMP_MAIL_BODY_ITEM, <br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;strlen(TEMP_MAIL_BODY_ITEM)))<br>
 &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp; &nbsp;printf (&quot;Error: unable to delete item '%s' to note.\n&quot;, <br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;TEMP_MAIL_BODY_ITEM);<br>
 &nbsp; &nbsp; &nbsp; &nbsp;</font></tt><tt>goto Done2;</tt><tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<br>
 &nbsp; &nbsp;}</font></tt><br>
<br>
Note that the technique SENDMEMO uses to create a rich text Body field only works if the resulting message body is smaller than 64 kilobytes. Also, it creates a Body field that contains only text, with no bitmaps, tables, or links.<br>
<br>
<b><font color="#000080">SENDMEMO: Transfer to the Router</font></b><br>

<ol type="1">
<li>Use NSFNoteUpdate to update the document to the mail.box file. This transfers the document to the router.
<li>Close the document.
<li>Close the mail.box file.</ol>

<table border="1">
<tr valign="top"><td width="648"><b>sendmemo.c - Transfer to the Router</b></td></tr>
</table>
<tt><font size="2">&nbsp; &nbsp; if (error = NSFNoteUpdate(hMemo, 0))<br>
 &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp; &nbsp;printf (&quot;Error: unable to update note in mail.box.\n&quot;);<br>
 &nbsp; &nbsp; &nbsp; &nbsp;</font></tt><tt>goto Done2;</tt><tt><font size="2">&nbsp; <br>
 &nbsp; &nbsp;}</font></tt><br>
<br>
<tt>Done2:</tt><br>
<tt>&nbsp; &nbsp; NSFNoteClose(hMemo);</tt><br>
<br>
<tt>Done1:</tt><br>
<tt>&nbsp; &nbsp; NSFDbClose(hMailBox);</tt><br>
<br>
<tt>Done:</tt><br>
<tt>&nbsp; &nbsp; if (error)</tt><br>
<tt>&nbsp; &nbsp; &nbsp; 	PrintAPIError (error); &nbsp;</tt><br>
<tt>&nbsp; &nbsp; else</tt><br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; printf (&quot;%s: successfully deposited memo '%s' in '%s'.\n&quot;,</tt><br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; argv[0], szSubject, szMailBoxPath);</tt><br>
<br>
<tt>&nbsp; &nbsp; NotesTerm();</tt><br>
<tt>&nbsp; &nbsp; return (error); </tt><tt><font size="2"><br>
}</font></tt>
<ul></ul>
Note that a mail program of any greater complexity than SENDMEMO should create the document first in a local database, open the mail.box file, copy the message document to the mail.box file, and close the mail.box file as soon as possible. API programs should keep the mail.box file open for a minimum amount of time.
<ul><br>
</ul>
<b><font size="4" color="#000080">Example Using Mail Gateway API Functions</font></b><br>
<br>
The sample program SENDMAIL sends a Mail message using primarily Domino Mail Gateway API functions, along with a few NSF functions.<br>
<br>
SENDMAIL is a standalone API program.<br>
<br>
The source code for SENDMAIL resides in the appropriate platform directory in the subdirectory \samples\mail\sendmail.<br>
<br>
The Domino Mail Gateway API functions help to make the algorithm for SENDMAIL simpler than the algorithm for SENDMEMO.<br>
<br>
SENDMAIL differs from SENDMEMO in the following ways:<br>

<ul type="disc">
<li>SENDMAIL creates the document in the user's message file. It appends all the fields to the document before opening the mail.box file. This allows SENDMAIL to open the mail.box file, copy the document into the mail.box file, and close the mail.box file with the minimum number of intermediate steps.
<li>SENDMAIL saves the document in the user's message file, as well as sending it via the Domino router. 
<li>SENDMAIL handles the case where the workstation running the program is not connected directly to the mail server by a LAN. If the LAN is not available, SENDMAIL copies the document into a local copy of the mail.box file for later delivery to the router.
<li>SENDMAIL handles multiple names in the SendTo and CopyTo fields. It creates SendTo, CopyTo, and Recipients fields as text lists. However, like SENDMEMO, SENDMAIL does not look up the names provided as input to verify that they exist in the Domino Directory.</ul>
<br>
<b><font color="#000080">SENDMAIL: Creating the Recipients field</font></b><br>
<br>
The code fragment below shows how SENDMAIL handles the SendTo and Recipients fields as text lists.
<table border="1">
<tr valign="top"><td width="648"><b>sendmail.c - Recipients as a Text List Field</b></td></tr>
</table>
<tt><font size="2">&nbsp; &nbsp; if (status = ListAllocate(0, 0, TRUE, &amp;hRecipientsList,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&amp;plistRecipients, &amp;wRecipientsSize))<br>
 &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp; &nbsp;/* Unable to allocate list */<br>
 &nbsp; &nbsp; &nbsp; &nbsp;error = ERR_SENDMAIL_CANTALLOCATELIST;<br>
 &nbsp; &nbsp; &nbsp; &nbsp;goto CloseMsg;<br>
 &nbsp; &nbsp;}<br>
 &nbsp; &nbsp;OSUnlockObject(hRecipientsList);</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; if (status = ListAllocate(0, 0, TRUE, &amp;hSendToList,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&amp;plistSendTo, &amp;wSendToSize))<br>
 &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp; &nbsp;error = ERR_SENDMAIL_CANTALLOCATELIST;<br>
 &nbsp; &nbsp; &nbsp; &nbsp;goto CloseMsg;<br>
 &nbsp; &nbsp;}<br>
 &nbsp; &nbsp;OSUnlockObject(hSendToList);</font></tt><br>
<br>
<tt><font size="2">/* ... code omitted ...*/ &nbsp; </font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp;/* Parse SendTo string. Add names to SendTo and Recipients lists. */</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; for (szNextName = strtok(szSendTo, &quot;:,&quot;);<br>
 &nbsp; &nbsp; &nbsp; &nbsp; szNextName != (char*)NULL;<br>
 &nbsp; &nbsp; &nbsp; &nbsp; szNextName = strtok(NULL, &quot;:,&quot;))<br>
 &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp; &nbsp;while (isspace(*szNextName)) &nbsp; &nbsp;// Skip white space before name<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;szNextName++;</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; if (status = ListAddEntry(hSendToList, TRUE, &amp;wSendToSize,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;wSendToCount++, szNextName,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;(WORD)lstrlen(szNextName)))<br>
 &nbsp; &nbsp; &nbsp; &nbsp;{ &nbsp; /* Unable to add name to SendTo list */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;error = ERR_SENDMAIL_CANTADDTOSENDLIST;<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;goto CloseMsg;<br>
 &nbsp; &nbsp; &nbsp; &nbsp;}</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; if (status = ListAddEntry(hRecipientsList, TRUE, &amp;wRecipientsSize,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;wRecipientsCount++, szNextName,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;(WORD)lstrlen(szNextName)))<br>
 &nbsp; &nbsp; &nbsp; &nbsp;{ &nbsp; /* Unable to add name to Recipients list */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;error = ERR_SENDMAIL_CANTADDTORECIPLIST;<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;goto CloseMsg;<br>
 &nbsp; &nbsp; &nbsp; &nbsp;}<br>
 &nbsp; &nbsp;}</font></tt><br>
<br>
<tt><font size="2">/* ... code omitted ...*/</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; if (status = MailAddRecipientsItem( hMsg, hRecipientsList,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;wRecipientsSize))<br>
 &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp; &nbsp;/* Unable to set Recipient item in memo */<br>
 &nbsp; &nbsp; &nbsp; &nbsp;error = ERR_SENDMAIL_CANTSETRECIPIENT;<br>
 &nbsp; &nbsp; &nbsp; &nbsp;goto CloseMsg;<br>
 &nbsp; &nbsp;}<br>
 &nbsp; &nbsp;/* &nbsp;MailAddRecipientsItem and MailAddHeaderItemByHandle both attach<br>
 &nbsp; &nbsp; &nbsp; &nbsp;the memory used by the list to the message. Set handle to NULL<br>
 &nbsp; &nbsp; &nbsp; &nbsp;after these functions succeed so the code at CloseMsg: below does<br>
 &nbsp; &nbsp; &nbsp; &nbsp;not attempt to free it.<br>
 &nbsp; &nbsp; */<br>
 &nbsp; &nbsp;hRecipientsList = NULLHANDLE;</font></tt><br>
<br>
<br>
<b><font color="#000080">Enhancing Mail Applications</font></b>
<ul></ul>
You may wish to enhance your mail programs by looking up in the Domino Directory each name provided as input, to ensure that the name is a valid recipient. Your mail program is responsible for building a valid list of recipients. The following suggestions may help you implement these enhancements:
<ul>
<li type="disc">You may want to use NAMELookup if you don't know whether a name is a user or a group.
<li type="disc">Add names with explicit path routing (for example, &quot;Sally@Z@Y&quot;) directly to the Recipients list without attempting to look them up.
<li type="disc">Look up other names to make sure they exist in one of the Domino Directories. Do not add names to the Recipients list if they cannot be found in the Domino Directory. You may wish to resolve unfound names by interacting with the user.
<li type="disc">To eliminate duplicates, you must expand all group names. Otherwise, you may place group names in the Recipients list as long as the group name is defined in the Local  Address Book(s).
<li type="disc">Expand names of recipients in foreign domains to a mail address in NAME@DOMAIN format. If your application is running on a server, you can use MailLookupAddress to do this. Otherwise, use NAMELookup. Do not alter the case of the domain name, since the router is case-sensitive<font color="#FF0000"> </font>for domain names.
<li type="disc">Build a multi-valued text list of recipients by calling the Mail Gateway API function MailAddRecipients<font color="#FF0000"> </font>to add each expanded recipient name (referred to as a &quot;full mail address&quot;) to the Recipients list.
<ul>
<ul>
<ul></ul>
</ul>
</ul>
</ul>
<br>
<b><font size="5" color="#000080">Receiving Domino Mail</font></b><br>
<br>
Receiving mail consists of opening the appropriate mail file and reading the documents in it. The router delivers messages to mail files, which are databases identified in the Domino Directory as belonging to a given user. Therefore, to receive mail documents, an API program simply opens the appropriate mail file and reads the documents it contains. <br>
<br>
<br>
<b><font size="4" color="#000080">Example Using Mail Gateway API Functions</font></b><br>
<br>
The Domino Mail Gateway API contains a number of functions that help you read, create, and manage large numbers of document in mail files. The Mail Gateway API provides functions that create and manage lists of documents. <br>
<br>
<b><font color="#000080">READMAIL</font></b><br>
<br>
The sample program READMAIL reads all the messages in a specified mail file and prints them on the screen.<br>
<br>
The source code for READMAIL is in the directory \samples\mail\readmail. READMAIL uses primarily Domino Mail Gateway API functions.<br>
<br>
<b><font color="#000080">MGATE Outbound</font></b><br>
<br>
The sample program MGATE is an example Domino Mail Gateway<font color="#FF0000"> </font>built as a server add-in task. The outbound module of MGATE shows how to use Domino Mail Gateway API routines to read and process documents in a mail file.<br>
<br>
The source code for the outbound portion of MGATE is in the file outbound.c in the directory \samples\server\mgate
---
