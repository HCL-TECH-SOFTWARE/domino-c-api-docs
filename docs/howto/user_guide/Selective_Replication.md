##### Chapter 9-7
##### Selective Replication

In Domino and Notes, you can restrict the amount of information exchanged between replicas. You can select documents to replicate by document type, according to a selection formula, or both. You can use selective replication to conserve disk space or reduce connection time on dial-up lines.<br>
<br>
You can store replicas on a number of different servers. A server containing a database replica that will receive new or updated documents is called a destination server. A server containing a database replica from which documents are pulled is called a source server.<br>
<br>
Domino and Notes stores selective replication information in a replication formula note, one replication formula note for each specified destination server.  For a locally administered database, the local server is the only destination server, so there is only one replication formula note. For a centrally administered database, the manager of the master database may specify the replication criteria for replicas stored on a number of different servers. There would then be a replication formula note for each specified destination server.<br>
<br>
NOTE:  The selective replication note is valid only for the database in which it is stored; the formula only affects what gets pulled into the database whenever its server is the destination server during replication.<br>
<br>
<br>
<b><font size="5" color="#000080">Components of a Replication Formula Note</font></b><br>
<br>
A replication formula note is a note of class NOTE_CLASS_REPLFORMULA. It contains a $TITLE item, a $ReplVersion item, a $ReplSrcServers item, a $ReplClassMasks item, and one or more $ReplFormula items.<br>
<br>
<br>
<b><font size="4" color="#000080">$TITLE</font></b><br>
<br>
The $TITLE item is a text item that contains a string specifying the name of the destination server to which this note applies. This is usually the server on which the current instance of the database resides. If the replication formula note is in a database on a workstation and defines server-to-workstation replication, this item contains the workstation name.<br>
<br>
<br>
<b><font size="4" color="#000080">$ReplVersion</font></b><br>
<br>
The $ReplVersion item is a text item that contains the character '1' followed by a null terminator.<br>
<br>
<br>
<b><font size="4" color="#000080">$ReplSrcServers</font></b><br>
<br>
The $ReplSrcServers item is of type TYPE_TEXT_LIST.  It contains a list of the names of servers from which notes will be replicated using the replication formula.  If you want to use the default value (&quot;- Any Server -&quot;), enter a dash (&quot;-&quot;) in the text list as shorthand.<br>
<br>
<br>
<b><font size="4" color="#000080">$ReplClassMasks</font></b><br>
<br>
The $ReplClassMasks item is a text list item that specifies the types of notes that will be replicated with each of the source servers. Each entry in the $ReplClassMasks list specifies the document types that will be pulled from the corresponding server in the $ReplSrcServers list.<br>
<br>
The bitmasks in NOTECLASS define the types of notes that will be replicated. The string stored in the text list for each source server is a character representation of the decimal value of the bitmask. For example, if only Icon notes are to be replicated, the text string &quot;16&quot; is stored in the text list, since NOTE_CLASS_ICON is defined as 0x0010 (16 decimal).<br>
<br>
<br>
 <b><font size="4" color="#000080">$ReplFormula</font></b><br>
<br>
The $ReplFormula item is of type TYPE_FORMULA and consists of a compiled selection formula. There is one $ReplFormula item for each member of the $ReplSrcServers list. Each $ReplFormula item specifies the selection formula used to replicate documents from the corresponding member of the server list.<br>
<br>
<br>
 <b><font size="4" color="#000080">$ReplView</font></b><br>
<br>
The $ReplView item is of type TYPE_TEXT_LIST.  It contains either an explicit list of shared folders and views to be replicated, or it is NULL, which means that all shared folders and views are to be replicated.<br>
<br>
<br>
 <b><font size="4" color="#000080">$ReplPrivateFolder</font></b><br>
<br>
The $ReplPrivateFolder item is of type TYPE_TEXT_LIST.  It contains either an explicit list of private folders and views to be replicated, or it is NULL, which means that all private folders and views are to be replicated.<br>
<br>
<br>
 <b><font size="4" color="#000080">$ReplFields</font></b><br>
<br>
The $ReplFields item is of type TYPE_TEXT_LIST.  It contains either an explicit list of field names to be replicated, or it is NULL, which means that all fields are to be replicated.<br>
<br>
<br>
<b><font size="5" color="#000080">The SEL_REP</font></b><b><font size="5" color="#000080"> Sample Program</font></b><b><font size="5" color="#000080"> </font></b><br>
<br>
The sample program SEL_REP opens a database located on a HCL Domino Server and creates a replica copy of it on the workstation. SEL_REP then creates a replication formula note in the local copy of the database. This replication note specifies that when receiving documents from replicas located on any server, only documents with a value less than 100 stored in the numberfield item will be pulled from the server replica.  SEL_REP is in the directory  samples\admin\sel_rep.<br>
<br>
The program creates a new note in the database and sets the note class to NOTE_CLASS_REPLFORMULA.<br>
<br>

<table width="100%" border="1">
<tr valign="top"><td width="100%"><b>SEL_REP: Adding the $TITLE and $ReplVersion items.</b></td></tr>
</table>
<tt><font size="2">/*<br>
 * &nbsp;Set the name of the destination for replicated notes. ($TITLE item).<br>
 * &nbsp;In this case, the destination is the local workstation.<br>
 * &nbsp;First, get the name of the workstation's user.<br>
 */</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; if (!OSGetEnvironmentString (&quot;KeyFileName&quot;, IDFileSpec,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;MAXENVVALUE))</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; {<br>
 &nbsp; &nbsp; &nbsp; &nbsp;NSFDbClose(hDB); &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* Close database &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;*/<br>
 &nbsp; &nbsp; &nbsp; &nbsp;API_RETURN (ERR(sError));<br>
 &nbsp; &nbsp;}<br>
 &nbsp; &nbsp;if (sError = REGGetIDInfo (IDFileSpec, REGIDGetName, UserName,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; MAXUSERNAME+1, &amp;retUserNameLen))<br>
 &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp; &nbsp;NSFDbClose(hDB); &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* Close database &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;*/<br>
 &nbsp; &nbsp; &nbsp; &nbsp;API_RETURN (ERR(sError));<br>
 &nbsp; &nbsp;}</font></tt><br>
<br>
<tt><font size="2">/*<br>
 * &nbsp;Now set the $TITLE item.<br>
 */<br>
 &nbsp; &nbsp;if (sError = NSFItemSetText(hNote,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;REPLFORMULA_SERVER_ITEM,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;UserName,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;MAXWORD))<br>
 &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp; &nbsp;NSFDbClose(hDB); &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* Close database &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;*/<br>
 &nbsp; &nbsp; &nbsp; &nbsp;</font></tt><tt><font size="2">API_RETURN</font></tt><tt><font size="2">&nbsp;(ERR(sError));<br>
 &nbsp; &nbsp;}</font></tt><br>
<tt><font size="2">/*<br>
 * &nbsp;Set the REPLFORMULA_VERSION_ITEM.<br>
 */</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; if (sError = NSFItemSetText(hNote,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;REPLFORMULA_VERSION_ITEM,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&quot;1&quot;,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;MAXWORD))<br>
 &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp; &nbsp;NSFDbClose(hDB); &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* Close database &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;*/<br>
 &nbsp; &nbsp; &nbsp; &nbsp;</font></tt><tt><font size="2">API_RETURN</font></tt><tt><font size="2">&nbsp;(ERR(sError));<br>
 &nbsp; &nbsp;}</font></tt><br>
<br>
<br>
The above code first sets the $TITLE item, which specifies the destination for replication. Since we are replicating from a server to the workstation, the destination is the user's name. The code calls SECKFMGetUserName to get the name of the user and adds this to the note as an item of TYPE_TEXT.<br>
<br>
Next, the code adds the $ReplVersion item. This must be the text string &quot;1&quot;.<br>
<br>
<br>

<table width="100%" border="1">
<tr valign="top"><td width="100%"><b>SEL_REP: Adding the $ReplSrcServers item.</b></td></tr>
</table>
<tt><font size="2">/*<br>
 * &nbsp;Create the $ReplSrcServers. This is a text list containing the<br>
 * &nbsp;names of all source servers.<br>
 *<br>
 * &nbsp;First, allocate a buffer in which the TEXT_LIST will be built.<br>
 */</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; if (sError = OSMemAlloc (0, wTextBufferLength, &amp;hMem))<br>
 &nbsp; &nbsp; &nbsp; &nbsp;</font></tt><tt><font size="2">API_RETURN</font></tt><tt><font size="2">&nbsp;(FALSE);<br>
/*<br>
 * &nbsp;Lock global buffer.<br>
 */<br>
 &nbsp; &nbsp;if ((pBuffer = OSLockObject(hMem)) == NULL)<br>
 &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp; &nbsp;OSMemFree (hMem);<br>
 &nbsp; &nbsp; &nbsp; &nbsp;</font></tt><tt><font size="2">API_RETURN</font></tt><tt><font size="2">&nbsp;(FALSE);<br>
 &nbsp; &nbsp;}</font></tt><br>
<tt><font size="2">/*<br>
 * &nbsp;Set start length to zero, and point the item pointer to the<br>
 * &nbsp;start of the buffer.<br>
 */ &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; </font></tt><br>
<tt><font size="2">&nbsp; &nbsp; wItemLength = 0;<br>
 &nbsp; &nbsp;pItem = pBuffer;</font></tt><br>
<tt><font size="2">/*<br>
 * &nbsp;Now fill in text list of server names containing database replicas that<br>
 * &nbsp;documents could be pulled from. &nbsp;In this example, there is only<br>
 * &nbsp;one entry, the default &quot;- Any Server -&quot;, represented by a single dash<br>
 * &nbsp;(&quot;-&quot;). &nbsp;This is the required shorthand for specifying &quot;- Any Server -&quot;.<br>
 * &nbsp;This means that when replicating from any server, use the<br>
 * &nbsp;information in this note.<br>
 *<br>
 * &nbsp;If different replication criteria were desired for documents being pulled<br>
 * &nbsp;from a specific server, that server's name would be added as another entry<br>
 * &nbsp;in the text list.<br>
 */</font></tt><tt><font size="2"><br>
 &nbsp; &nbsp;*((USHORT *)pItem) = 1; &nbsp; &nbsp; &nbsp; /* &nbsp;Set number of entries. &nbsp;*/<br>
 &nbsp; &nbsp;pItem += sizeof(WORD);<br>
 &nbsp; &nbsp;wItemLength += sizeof(WORD);</font></tt><br>
<tt><font size="2">&nbsp;/*<br>
 &nbsp;* &nbsp;Set length of first source server.<br>
 &nbsp;*/</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; *((WORD *)pItem) = sizeof(SrcServerName)-1; <br>
 &nbsp; &nbsp;pItem += sizeof(WORD);<br>
 &nbsp; &nbsp;wItemLength += sizeof(WORD);</font></tt><br>
<tt><font size="2">&nbsp;/*<br>
 &nbsp;* &nbsp;First source server name.<br>
 &nbsp;*/<br>
 &nbsp; &nbsp;memcpy(pItem, SrcServerName, sizeof(SrcServerName) -1);<br>
 &nbsp; &nbsp;pItem += (sizeof(SrcServerName) - 1);<br>
 &nbsp; &nbsp;wItemLength += (sizeof(SrcServerName) - 1);</font></tt><br>
<tt><font size="2">/*<br>
 * &nbsp;Append the $ReplSrcServers item to the note.<br>
 */</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; if (sError = NSFItemAppend(hNote,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ITEM_SUMMARY,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; REPLFORMULA_SOURCE_SERVERS,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; sizeof (REPLFORMULA_SOURCE_SERVERS)-1,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; TYPE_TEXT_LIST,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; pBuffer,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; wItemLength))<br>
 &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp; &nbsp;OSUnlockObject (hMem);<br>
 &nbsp; &nbsp; &nbsp; &nbsp;OSMemFree (hMem);<br>
 &nbsp; &nbsp; &nbsp; &nbsp;NSFDbClose(hDB); &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; /* Close database &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;*/<br>
 &nbsp; &nbsp; &nbsp; &nbsp;</font></tt><tt><font size="2">API_RETURN </font></tt><tt><font size="2">(ERR(sError));<br>
 &nbsp; &nbsp;}</font></tt><br>
<br>
<br>
The $ReplSrcServer item is a text list containing the names of the servers for which replication formulas are defined. In this example, the only entry  in the list is &quot;-&quot; (short for &quot;- Any Server -&quot;).  This means that the replication criteria specified in this note are to be used when pulling documents from a replica located on any server.  If you want to associate different replication criteria with a specific server, add that server's name to the text list and add corresponding entries in the other items.<br>
<br>
<br>

<table width="100%" border="1">
<tr valign="top"><td width="100%"><b>SEL_REP: Adding the $ReplClassMasks item</b></td></tr>
</table>
<br>
<tt><font size="2">/*<br>
 * &nbsp;Create the $ReplClassMask item. There is only one entry in the text<br>
 * &nbsp;list, since in this example the replication criteria are the same<br>
 * &nbsp;regardless of which server the documents are being pulled from. &nbsp;If<br>
 * &nbsp;more than one server were specified in $ReplSrcServers item,<br>
 * &nbsp;character strings representing the classes of documents to be replicated<br>
 * &nbsp;from the corresponding servers would need to be added to the text list.<br>
 */</font></tt><br>
<tt><font size="2">/*<br>
 * &nbsp;Reset start length to zero, and point the item pointer to the<br>
 * &nbsp;start of the buffer.<br>
 */ &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; </font></tt><br>
<tt><font size="2">&nbsp; &nbsp; wItemLength = 0;<br>
 &nbsp; &nbsp;pItem = pBuffer;</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; *((USHORT *)pItem) = 1; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* &nbsp;Set number of entries. &nbsp;*/<br>
 &nbsp; &nbsp;pItem += sizeof(WORD);<br>
 &nbsp; &nbsp;wItemLength += sizeof(WORD);</font></tt><br>
<tt><font size="2">/*<br>
 * &nbsp;Convert the note class mask to a character string.<br>
 */<br>
 &nbsp; &nbsp;iClasses = MY_NOTE_CLASSES;<br>
 &nbsp; &nbsp;_itoa (iClasses, ClassMaskString, 10);</font></tt><br>
<tt><font size="2">/*<br>
 * &nbsp;Set length of mask string.</font></tt><br>
<tt><font size="2">&nbsp;*/</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; *((WORD *)pItem) = strlen(ClassMaskString);<br>
 &nbsp; &nbsp;pItem += sizeof(WORD);<br>
 &nbsp; &nbsp;wItemLength += sizeof(WORD);</font></tt><br>
<tt><font size="2">&nbsp;/*<br>
 &nbsp;* &nbsp;Copy mask string.<br>
 &nbsp;*/<br>
 &nbsp; &nbsp;memcpy(pItem, ClassMaskString, strlen(ClassMaskString));<br>
 &nbsp; &nbsp;pItem += (strlen(ClassMaskString));<br>
 &nbsp; &nbsp;wItemLength += (strlen(ClassMaskString));</font></tt><br>
<tt><font size="2">/*<br>
 * &nbsp;Append the $ReplClassMasks item to the note.<br>
 */</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; if (sError = NSFItemAppend(hNote,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ITEM_SUMMARY,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; REPLFORMULA_NOTECLASS_ITEM,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; sizeof (REPLFORMULA_NOTECLASS_ITEM)-1,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; TYPE_TEXT_LIST,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; pBuffer,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; wItemLength))<br>
 &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp; &nbsp;OSUnlockObject (hMem);<br>
 &nbsp; &nbsp; &nbsp; &nbsp;OSMemFree (hMem);<br>
 &nbsp; &nbsp; &nbsp; &nbsp;NSFDbClose(hDB); &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; /* Close database &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;*/<br>
 &nbsp; &nbsp; &nbsp; &nbsp;</font></tt><tt><font size="2">API_RETURN</font></tt><tt><font size="2">&nbsp;(ERR(sError));<br>
 &nbsp; &nbsp;}</font></tt><br>
<br>
$ReplClassMasks is a text list that specifies the classes of documents that will be replicated when pulling documents from the corresponding servers listed in the $ReplSrcServers list. The bitfields in NOTE_CLASS denote the list of document classes. The entries in the $ReplClassMasks text list are character representations of the decimal values of the bitmasks.<br>
<br>
This example replicates the same classes of documents with all servers. The bitmask specifying the server classes is defined in sel_rep.h. The code converts the mask to a character string and stores the string in the $ReplClassMask list for both entries.<br>
<br>
<br>

<table width="100%" border="1">
<tr valign="top"><td width="100%"><b>SEL_REP: Adding the $ReplFormula item.</b></td></tr>
</table>
<tt><font size="2"><br>
</font></tt><tt><font size="2">/*<br>
 * &nbsp;Create a $ReplFormula item. &nbsp;If more than one entry was specified for<br>
 * &nbsp;The $ReplSrcServers item, a $ReplFormula item would be needed for each<br>
 * &nbsp;server, and the order of the $ReplFormula items appeared would correspond<br>
 * &nbsp;to the order of server names in the text list.<br>
 *<br>
 * &nbsp;Compile the selection formula, get a pointer to it,and append<br>
 * &nbsp;it to the note.<br>
 */</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; if (sError = NSFFormulaCompile(NULL,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 0,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; szSelFormula,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; strlen(szSelFormula),<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &amp;hSelFormula,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &amp;wSelFormulaLen,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &amp;wdc, &amp;wdc, &amp;wdc,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &amp;wdc, &amp;wdc))<br>
 &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp; &nbsp;OSUnlockObject (hMem);<br>
 &nbsp; &nbsp; &nbsp; &nbsp;OSMemFree (hMem);<br>
 &nbsp; &nbsp; &nbsp; &nbsp;NSFDbClose(hDB); &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; /* Close database &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;*/<br>
 &nbsp; &nbsp; &nbsp; &nbsp;</font></tt><tt><font size="2">API_RETURN</font></tt><tt><font size="2">&nbsp;(ERR(sError));<br>
 &nbsp; &nbsp;}</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; pSelFormula1 = OSLockObject(hSelFormula);<br>
/*<br>
 * &nbsp;Append the $ReplFormula item to the note.<br>
 */</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; if (sError = NSFItemAppend(hNote,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ITEM_SUMMARY,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; REPLFORMULA_FORMULA_ITEM,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; sizeof (REPLFORMULA_FORMULA_ITEM)-1,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; TYPE_FORMULA,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; pSelFormula,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; wSelFormulaLen))<br>
 &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp; &nbsp;OSUnlockObject (hMem);<br>
 &nbsp; &nbsp; &nbsp; &nbsp;OSMemFree (hMem);<br>
 &nbsp; &nbsp; &nbsp; &nbsp;NSFDbClose(hDB); &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; /* Close database &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;*/<br>
 &nbsp; &nbsp; &nbsp; &nbsp;</font></tt><tt><font size="2">API_RETURN</font></tt><tt><font size="2">&nbsp;(ERR(sError));<br>
 &nbsp; &nbsp;}</font></tt><br>
<tt><font size="2">/*<br>
 * &nbsp;Unlock and free memory associated with this formula.<br>
 */</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; OSUnlockObject(hSelFormula);<br>
 &nbsp; &nbsp;OSMemFree(hSelFormula);</font></tt><br>
<br>
<br>
A $ReplFormula item is of type TYPE_FORMULA. It  defines the selection criteria for documents that will be replicated. There is one $ReplFormula item for each server with which the workstation will replicate, and they must appear in the same  order as their corresponding entries in the $ReplSrcServer item.<br>
<br>
In this sample, the formula stored in the $ReplFormula item is &quot;Select (numberfield &lt; 100)&quot;.  This means that the program replicates only documents containing a value less than 100 in the field named &quot;numberfield&quot;. All documents of the appropriate classes are replicated. <br>
<br>
After the program creates the replication formula note, it updates the note, closes the database, and exits.
---
