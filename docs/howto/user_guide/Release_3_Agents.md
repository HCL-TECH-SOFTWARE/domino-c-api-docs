##### Chapter 8-4
##### Release 3 Agents

<b><font size="5" color="#000080">Introduction</font></b><br>
<br>
Agents in Domino and Notes were preceeded by macros in Notes Release 3.  As of Release 4, macros have been replaced by agents. For backward compatibility, Domino still supports macro notes and refers to them as Release 3 agents. This chapter explains how to create, read, and run Notes Release 3 agents from a C API program. It describes different types of Release 3 agents and how you can use the C API to manipulate them, identifies the components of Release 3 agent notes, and describes how to interpret these items.<br>
<br>
<br>
<b><font size="5" color="#000080">Sample Programs</font></b><br>
<br>
This chapter refers to the two sample programs ADDMACRO and RUNMACRO. The source code files for ADDMACRO reside in the directory samples\dbdesign\addmacro. The source code files for RUNMACRO reside in the directory samples\dbdesign\runmacro.<br>
<br>
<br>
<b><font size="5" color="#000080">Release 3 Agent Notes</font></b><br>
<br>
Release 3 agent notes are notes of class NOTE_CLASS_FILTER. Like form and view notes, agent notes are design notes that reside in Domino databases. Domino application developers design agents to perform custom operations on documents in a database.<br>
<br>
Release 3 agent notes contain formulas and control information. The formulas select documents to process and calculate values to store in the documents. The control information tells Domino or Notes when to execute the agent, which documents to consider for selection, and what operation to perform.<br>
<br>
Some Release 3 agents -- for example, Button and SmartIcon agents -- do not reside in agent notes. This chapter focuses on Release 3 agents that do reside in agent notes.<br>
<br>
<br>
<b><font size="5" color="#000080">Types of Release 3 Agents</font></b><br>
<br>
Domino and Notes supports a wide variety of agents. This section identifies different types of Release 3 agents and discusses how you can use the C API to manipulate each type.<br>
<br>
<b><font color="#000080">Release 3 Agents that C API Programs Can Create</font></b><br>
<br>
A C API program can create any type of agent except <b>SmartIcons.</b> <br>
<br>
<b><font color="#000080">Release 3 Agents that C API Programs Can Run </font></b><br>
<br>
A C API program can execute any agent that does not depend on Notes user interface functionality. The following functions depend on Notes user interface functionality. Any Release 3 agent that uses one of these functions has no effect when run from a C API program:<br>

<ul>
<ul>@DbLookup<br>
@DbColumn<br>
@Command<br>
@MailSend<br>
@DDEInitiate<br>
@DDETerminate<br>
@DDEExecute<br>
@DDEPoke</ul>
</ul>
<br>
<b><font size="4" color="#000080">Release 3 Filter Agents</font></b><br>
<br>
Filter agents normally update a series of documents in a database automatically. You can execute most filter agents from a C API program. <br>
<br>
There are three types of filter agents, based on when the agent is executed: menu agents, background agents, and mail/paste agents.<br>
<br>
<b><font color="#000080">Menu Agents</font></b><br>
<br>
A menu agent runs when a Notes user selects it from the Actions menu or when a C API program runs it. Menu agents do not run automatically. C API programs can run most menu agents. <br>
<br>
<b><font color="#000080">Background Agents</font></b><br>
<br>
Background agents run at predetermined intervals or when a Notes user selects the View, Agents and selects Run from the Actions menu. C API programs can run most background agents. <br>
<br>
The Domino or Notes background program automatically runs background agents at the predetermined interval specified in the agent. The control information in the agent note specifies the frequency -- hourly, daily, weekly, or never. For details, see the description of the $Period item below.<br>
<br>
<b><font color="#000080">Mail/Paste Agents</font></b><br>
<br>
Mail/paste agents run whenever the router delivers a document to the database or a user pastes the document into the database from<font color="#FF0000"> </font>the clipboard.  <br>
<br>
C API programs cannot intercept documents delivered to a database by the router or pasted into a database by a Notes user. Therefore, C API programs cannot run mail/paste agents when Notes would. However, C API programs can run mail/paste agents on documents in a database just as they can run menu and background agents.<br>
<br>
<b><font size="4" color="#000080">Release 3 Search Agents</font></b><br>
<br>
Search agents operate on the set of documents selected by a full-text search query. Search agents can be activated from the full text search bar or run in the background at predetermined intervals. C API programs can execute most search agents.<br>
<br>
<b><font size="4" color="#000080">Release 3 Execute-Once Agents</font></b><br>
<br>
Execute-once agents perform a single operation and then stop. The operation may process a single document or a set of documents. It does not repeat the operation for each document. C API programs can execute most execute-once agents.<br>
<br>
<b><font size="4" color="#000080">Buttons</font></b><br>
<br>
Buttons are agents that reside in forms (like fields) or in documents. They operate on the current document. When a Notes user clicks a button, it evaluates a formula and performs actions just like other agents. However, buttons do not reside in agent notes. <br>
<br>
Since most buttons perform functions that depend on Notes user interface functionality, (for example, they use the @Command function) C API programs cannot execute most button agents.   For more information about buttons, see the &quot;Hotspots&quot;<font color="#FF0000"> </font>chapter in this guide.<br>
<br>
<b><font size="4" color="#000080">SmartIcons</font></b><br>
<br>
SmartIcons are agents associated with the icons on the SmartIcons palette. SmartIcons reside in a smarticons file (.smi). The C API does not expose the format of .smi files, so C API programs can not access SmartIcons.<br>
<br>
<br>
<b><font size="5" color="#000080">Components of Release 3 Agent Notes</font></b><br>
<br>
This sections describes the items stored in a Release 3 agent note and how to interpret these items.<br>
<br>
A Release 3 agent note must contain the following fields:<br>
<br>
<b>Field Name</b>	<b>Symbolic Constant</b>		<b>Data Type</b>	<b>Description</b><br>
$TITLE		FIELD_TITLE			TYPE_TEXT	Name of the agent<br>
$Type		FILTER_TYPE_ITEM		TYPE_TEXT	Agent run options<br>
$Operation	FILTER_OPERATION_ITEM	TYPE_TEXT	Operation setting<br>
$Scan		FILTER_SCAN_ITEM		TYPE_TEXT	Run agent on setting<br>
$Flags		DESIGN_FLAGS		TYPE_TEXT	Design flags<br>
<br>
Certain types of agents require additional fields. Most agents (except full-text search queries) require a field named $Formula that contains the compiled formula. Background agents must have a field named $Period that specifies how frequently Domino or Notes should run the agent. Background agents also have a field named $MachineName that identifies what machine an agent should run on. Search agents must have either a field named $SimpleQuery or a field named $BuilderQuery.<br>
<br>
Use the symbolic constants defined in the C API header file stdnames.h when referring to the field names of agent note items. stdnames.h also defines symbolic constants for many of the standard values normally stored in these items.<br>
<br>
Generally, $Type encodes the &quot;When should this agent run&quot; options, $Operation encodes the operation settings (on the lower right of the dialog if the &quot;Formula&quot; radio button is selected), and $Scan encodes the &quot;Which documents should it act on&quot; settings. These three fields represent the settings specified in the Create - Design - Agent dialog box at agent design time.<br>
<br>
   <br>
<b><font size="4" color="#000080">$TITLE</font></b><br>
<br>
The $TITLE field is required in all Release 3 agent notes. The data type is TYPE_TEXT. The value of the $TITLE field is the agent name.<br>
<br>
When you create an agent with the Notes user interface, you specify the name in the Create - Design - Agent dialog box. Notes needs the name to list the agent in menus and dialog boxes. C API programs need the name so that end users can specify the agent by name.<br>
<br>
When you use the C API to create an agent, the agent name must not exceed DESIGN_LEVEL_MAX bytes unless it is a cascading agent name.<br>
<br>
<br>
<b><font size="4" color="#000080">$Type</font></b><br>
<br>
The $Type field is required in all Release 3 agent notes. The data type is TYPE_TEXT. The value is a character digit -- '0', '1', '2', or '3' -- corresponding to one of the filter types defined in stdnames.h.<br>
<br>
The value stored in the $Type field encodes the &quot;When should this agent run&quot; options. When you create an agent with the Notes user interface, you specify the &quot;When should this agent run&quot; options in the Create - Design - Agent dialog box. The following table maps the filter type symbolic constants to the run options in the dialog box:<br>
<br>
<b>Filter Type Symbol</b>		<b>Run Option</b><br>
<tt>FILTER_TYPE_MENU</tt>	Run manually from Actions menu<br>
<tt>FILTER_TYPE_BACKGROUND</tt>	Run periodically in the background<br>
<tt>FILTER_TYPE_MAIL</tt>	Run when documents are pasted/mailed into database<br>
<tt>FILTER_TYPE_ONCE</tt>	Run once<br>
<br>
The symbolic constants are defined as numbers between 0 and 3, but the value stored in the item is a character. The code fragment below shows how to translate the symbolic filter type constant to the corresponding character before setting the $Type field. <br>
<br>

<table width="100%" border="1">
<tr valign="top"><td width="100%"><b>addmacro.c - Setting the $Type Field</b></td></tr>
</table>
<tt><font size="2">/* wType must be one of FILTER_TYPE_MENU, FILTER_TYPE_BACKGROUD,</font></tt><br>
<tt><font size="2">&nbsp; &nbsp;FILTER_TYPE_MAIL, or FILTER_TYPE_ONCE.</font></tt><br>
<tt><font size="2">*/<br>
</font></tt><br>
<tt><font size="2">STATUS &nbsp;LNPUBLIC &nbsp;SetMacroType( NOTEHANDLE hMacro, WORD wType )</font></tt><br>
<tt><font size="2">{<br>
 &nbsp; &nbsp;STATUS &nbsp; &nbsp; &nbsp;error;<br>
 &nbsp; &nbsp;CHAR &nbsp; &nbsp; &nbsp; &nbsp;cType;</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; cType = (CHAR)('0' + wType);<br>
 &nbsp; &nbsp;if (error = NSFItemSetText(hMacro,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;FILTER_TYPE_ITEM,	/* &quot;$Type&quot; */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&amp;cType, 1))<br>
 &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp; &nbsp;printf (&quot;Error: unable to set Type field in macro note.\n&quot;);<br>
 &nbsp; &nbsp;}<br>
 &nbsp; &nbsp;return(error); &nbsp; &nbsp;<br>
}</font></tt><br>
<br>
<br>
<b><font size="4" color="#000080">$Operation</font></b><br>
<br>
The $Operation field is required in all Release 3 agent notes. The data type is TYPE_TEXT. The value is a character digit -- '0', '1',  or '2' -- corresponding to one of the filter operations defined in stdnames.h.<br>
<br>
The value stored in the $Operation field encodes the agent operation setting. When you create an agent with the Notes user interface, you specify the operation setting in the Create - Design - Agent dialog box. The following table maps the filter operation symbolic constants to the operation settings in the dialog box:<br>
<br>
<b>Filter Operation Symbol</b>	<b>Operation Setting</b><br>
<tt>FILTER_OP_UPDATE</tt>		Update existing document when run<br>
<tt>FILTER_OP_SELECT</tt>		Select document when run<br>
<tt>FILTER_OP_NEW_COPY</tt>	Create new document when run<br>
<br>
The symbolic constants are defined as numbers between 0 and 2, but the value stored in the item is a character. The code fragment below shows how to translates the filter operation symbolic constant to the corresponding character before setting the $Operation field. 
<table width="100%" border="1">
<tr valign="top"><td width="100%"><b>addmacro.c - Setting the $Operation Field</b></td></tr>
</table>
<tt><font size="2">/* &nbsp;wOperation must be one of FILTER_OP_UPDATE, </font></tt><br>
<tt><font size="2">&nbsp; &nbsp; FILTER_OP_SELECT, or FILTER_OP_NEW_COPY.</font></tt><br>
<tt><font size="2">*/</font></tt><br>
<br>
<tt><font size="2">STATUS &nbsp;LNPUBLIC &nbsp;SetMacroOperation( NOTEHANDLE hMacro, WORD wOperation )<br>
{<br>
 &nbsp; &nbsp;STATUS &nbsp; &nbsp; &nbsp;error;<br>
 &nbsp; &nbsp;CHAR &nbsp; &nbsp; &nbsp; &nbsp;cOperation;<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; <br>
 &nbsp; &nbsp;cOperation = (CHAR)('0' + wOperation);<br>
 &nbsp; &nbsp;if (error = NSFItemSetText(hMacro,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;FILTER_OPERATION_ITEM, &nbsp;/* &quot;$Operation&quot; */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&amp;cOperation, 1))<br>
 &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp; &nbsp;printf (&quot;Error: unable to set Operation field in macro note.\n&quot;);<br>
 &nbsp; &nbsp;}</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; return(error);<br>
}</font></tt><br>
<br>
<br>
<b><font size="4" color="#000080">$Scan</font></b><br>
<br>
The $Scan field is required in all Release 3 agent notes. The data type is TYPE_TEXT. The value is a character digit -- '0', '1', '2', '3', '4', or '5' -- corresponding to one of the filter operations defined in stdnames.h.<br>
<br>
The value stored in the $Scan field encodes the &quot;Which document(s) should it act on&quot; setting. When you create an agent with the Notes user interface, you specify this setting in the Create - Design - Agent dialog box. The following table maps the filter scan option symbolic constants in stdnames.h to the &quot;Which document(s) should it act on&quot; settings in the dialog box:<br>
<br>
<b>Filter Scan Option Symbol</b>	<b>&quot;Which document(s)&quot; Setting</b><br>
<tt>FILTER_SCAN_ALL</tt>		Run on all documents in database<br>
<tt>FILTER_SCAN_UNREAD</tt>	Run on documents not yet marked read by you<br>
<tt>FILTER_SCAN_VIEW</tt>		Run on all documents in view<br>
<tt>FILTER_SCAN_SELECTED</tt>	Run on selected documents in view<br>
<tt>FILTER_SCAN_MAIL</tt>		Not used<br>
<br>
The symbolic constants are defined as numbers between 0 and 5, but the value stored in the item is a character. The code fragment below shows how to translate the filter scan option symbolic constant to the corresponding character before setting the $Scan field. 
<table width="100%" border="1">
<tr valign="top"><td width="100%"><b>addmacro.c - Setting the $Scan Field</b></td></tr>
</table>
<tt><font size="2">/* &nbsp;wScan must be one of FILTER_SCAN_ALL, FILTER_SCAN_UNREAD,<br>
 &nbsp; &nbsp;FILTER_SCAN_VIEW, FILTER_SCAN_SELECTED, FILTER_SCAN_MAIL,</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; or FILTER_SCAN_NEW.</font></tt><br>
<tt><font size="2">*/</font></tt><br>
<br>
<tt><font size="2">STATUS &nbsp;LNPUBLIC &nbsp;SetMacroScan( NOTEHANDLE hMacro, WORD wScan )<br>
{<br>
 &nbsp; &nbsp;STATUS &nbsp; &nbsp; &nbsp;error;<br>
 &nbsp; &nbsp;CHAR &nbsp; &nbsp; &nbsp; &nbsp;cScan;<br>
 &nbsp; &nbsp; <br>
 &nbsp; &nbsp;cScan = (CHAR)('0' + wScan);<br>
 &nbsp; &nbsp;if (error = NSFItemSetText(hMacro,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;FILTER_SCAN_ITEM,	/* &quot;$Scan&quot; */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&amp;cScan, 1))<br>
 &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp; &nbsp;printf (&quot;Error: unable to set Scan field in macro note.\n&quot;);<br>
 &nbsp; &nbsp;}<br>
 &nbsp; &nbsp;return(error);<br>
}</font></tt><br>
<br>
Domino and Notes requires all Background and Mail agents to have the &quot;Which document(s) should it act on&quot; setting set to &quot;Run on  all new and modified documents since last run.&quot; At the C API level, this means that all agents whose $Type items are set to FILTER_TYPE_BACKGROUND or FILTER_TYPE_MAIL must have their $Scan items set to FILTER_SCAN_NEW.<br>
<br>
<br>
<b><font size="4" color="#000080">$Formula and $Formula2</font></b><br>
<br>
All Release 3 agents except full-text search queries require a field named $Formula (FILTER_FORMULA_ITEM) that contains the compiled agent formula. Some agents also contain a field named $Formula2 (FILTER_FORMULA2_ITEM) that contains an extended agent formula. <br>
<br>
The $Formula and $Formula2 fields have data type TYPE_FORMULA. Create these fields by expressing the formula as a character string and then using NSFFormulaCompile to compile the string. This yields a formula handle and the length of the compiled formula. Append this data to the note by locking the handle to obtain a pointer, then calling NSFItemAppend to append the compiled formula -- as specified by the pointer -- to an open note. <br>
<br>
The code fragment below shows how to compile a character string into a formula, then append the formula as the $Formula field to an open agent note.
<table width="100%" border="1">
<tr valign="top"><td width="100%"><b>addmacro.c - Setting the $Formula Field</b></td></tr>
</table>
<tt>STATUS far &nbsp;PASCAL &nbsp;SetMacroFormula( NOTEHANDLE hMacro, PCHAR szFormula )<br>
{<br>
 &nbsp; &nbsp;STATUS &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;error;<br>
 &nbsp; &nbsp;FORMULAHANDLE &nbsp; hFormula;<br>
 &nbsp; &nbsp;WORD &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;wFormulaLen;<br>
 &nbsp; &nbsp;WORD &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;wdc;</tt><br>
<br>
<tt>&nbsp; &nbsp; if (error = NSFFormulaCompile( &nbsp;NULL, 0, szFormula, strlen(szFormula),<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&amp;hFormula, &amp;wFormulaLen, &amp;wdc, &amp;wdc, <br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&amp;wdc, &amp;wdc, &amp;wdc))<br>
 &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp; &nbsp;printf (&quot;Error compiling formula.\n&quot;);<br>
 &nbsp; &nbsp; &nbsp; &nbsp;return(error);<br>
 &nbsp; &nbsp;}</tt><br>
<br>
<tt>&nbsp; &nbsp; error = NSFItemAppend(<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;hMacro, &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; /* handle to note to append to */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;ITEM_SUMMARY, &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; /* item flags */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;FILTER_FORMULA_ITEM, &nbsp; &nbsp;/* item name: &quot;$Formula&quot; */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;strlen(FILTER_FORMULA_ITEM),<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;TYPE_FORMULA, &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; /* item type */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;OSLockObject(hFormula), /* item value */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;wFormulaLen); &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; /* value length */</tt><br>
<br>
<tt>&nbsp; &nbsp; OSUnlockObject(hFormula);<br>
 &nbsp; &nbsp;OSMemFree(hFormula);</tt><br>
<br>
<tt>&nbsp; &nbsp; if (error)<br>
 &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp; &nbsp;printf (&quot;Error: unable to append formula item to macro note.\n&quot;);<br>
 &nbsp; &nbsp;}<br>
 &nbsp; &nbsp;return (error);<br>
}</tt><br>
<br>
<br>
<b><font size="4" color="#000080">$Query</font></b><br>
<br>
Full Text Search agents are distinguished by the presence of the field named $Query (FILTER_QUERY_ITEM). The $Query field has data type TYPE_TEXT. The value of the $Query field is the text of the query. When performing a full-text search from the Notes user interface, you specify the query text in the query text box in the upper left corner of the search bar.<br>
<br>
<br>
<b><font size="4" color="#000080">$LeftToDo</font></b><br>
<br>
The $LeftToDo field (FILTER_LEFTTODO_ITEM) is a required field in certain types of Release 3 agents, including those that run only on new documents or documents that have been modified since the last time the agent ran. At the Notes user interface level, this includes all agents with &quot;Which document(s) should it act on&quot; set to &quot;All new and modified documents since last run.&quot;  At the C API level, this includes all agents whose $Scan item is set to FILTER_SCAN_NEW.<br>
<br>
The $LeftToDo item has data type TYPE_OBJECT. It contains a table of note IDs that identifies all the documents that the agent has not yet processed. Domino or Notes maintains this ID table each time it runs an agent containing this field.<br>
<br>
Before running an agent containing a $LeftToDo object, Domino or Notes retrieves the ID table from the object and updates the table with the IDs of all documents that have been updated or modified since the last time the agent ran. The resulting ID table identifies the set of documents that the agent needs to process this time. <br>
<br>
After running the agent, the ID table is updated by deleting the IDs of all documents processed, then it is stamped with the time and date it was updated, and then it is saved in the $LeftToDo object in the agent note. <br>
<br>
This mechanism lets the agent itself store the list of documents it has processed so that Domino, Notes or C API programs that run agents can avoid processing documents unnecessarily.<br>
<br>
The $LeftToDo object consists of an ID table followed by theTIMEDATE the agent was last modified and the DBID of the database in which the agent resided when it last ran. The Time field  of the ID table records when the table was last updated. Domino and Notes uses this information to evaluate the relevance of the ID table. The agent should discard the ID table and reprocess all notes in the database if:<br>

<ul type="disc">
<li>The agent was modified (that is, the formula was changed) since the last time it ran
<li>The agent was in a different database the last time it ran (that is, the agent note was copied from one database and pasted into the current database) </ul>
<br>
Because $LeftToDo is an item of type TYPE_OBJECT, you must use the NSFDbReadObject and NSFDbWriteObject functions to access the ID Table.<br>
<br>
The code fragment below shows how to read the $LeftToDo object and return a handle to the ID table, the TIMEDATE the agent was last modified, and the DBID of the database in which the agent resided when it last ran.<br>
<br>

<table width="100%" border="1">
<tr valign="top"><td width="100%"><b>runmacro.c - Reading the $LeftToDo Object</b></td></tr>
</table>
<br>
<tt>/* &nbsp;*pObject &nbsp; &nbsp; &nbsp; &nbsp; gets the OBJECT_DESCRIPTOR structure</tt><br>
<tt>&nbsp; &nbsp; *phLeftToDo &nbsp; &nbsp; &nbsp;gets the handle to the $LeftToDo ID Table</tt><br>
<tt>&nbsp; &nbsp; *ptdLeftToDoTime gets the Time member of the ID Table<br>
 &nbsp; &nbsp;*pwLeftToDoFlags gets the Flags member of the ID Table</tt><br>
<tt>*/</tt><br>
<br>
<tt>STATUS &nbsp;LNPUBLIC &nbsp;ReadLeftToDoObject( DBHANDLE &nbsp; &nbsp;hDb,</tt><br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; NOTEHANDLE &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;hMacro,</tt><br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; OBJECT_DESCRIPTOR &nbsp;*pObject,</tt><br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; HANDLE &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; *phLeftToDo,</tt><br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; TIMEDATE &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; *ptdLeftToDoTime,</tt><br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; WORD &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; *pwLeftToDoFlags )</tt><br>
<tt>{</tt><br>
<tt>&nbsp; &nbsp; STATUS &nbsp; &nbsp; &nbsp;error;</tt><br>
<tt>&nbsp; &nbsp; WORD &nbsp; &nbsp; &nbsp; &nbsp;wDataType;</tt><br>
<tt>&nbsp; &nbsp; BLOCKID &nbsp; &nbsp; bidValue;</tt><br>
<tt>&nbsp; &nbsp; DWORD &nbsp; &nbsp; &nbsp; dwValueLength;</tt><br>
<tt>&nbsp; &nbsp; void &nbsp; &nbsp; &nbsp; &nbsp;*ptable;</tt><br>
<tt>	OBJECT_DESCRIPTOR &nbsp;tempObjectPtr;</tt><br>
<tt>	OBJECT_DESCRIPTOR *tempPtr;</tt><br>
<tt>	</tt><br>
<tt>&nbsp; &nbsp; error = NSFItemInfo(hMacro, FILTER_LEFTTODO_ITEM, </tt><br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; sizeof(FILTER_LEFTTODO_ITEM)-1,</tt><br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; NULL, &amp;wDataType, &amp;bidValue, &amp;dwValueLength);</tt><br>
<br>
<tt>&nbsp; &nbsp; if ( ERR(error) == ERR_ITEM_NOT_FOUND )</tt><br>
<tt>&nbsp; &nbsp; {</tt><br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; return (error);</tt><br>
<tt>&nbsp; &nbsp; }</tt><br>
<tt>&nbsp; &nbsp; else if (error)</tt><br>
<tt>&nbsp; &nbsp; {</tt><br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; printf(&quot;Error: unable get '%s' from Macro.\n&quot;, FILTER_LEFTTODO_ITEM);</tt><br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; return(error);</tt><br>
<tt>&nbsp; &nbsp; }</tt><br>
<tt>&nbsp; &nbsp; if (wDataType != TYPE_OBJECT)</tt><br>
<tt>&nbsp; &nbsp; {</tt><br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; printf (&quot;Error: item '%s' not TYPE_OBJECT.\n&quot;, FILTER_LEFTTODO_ITEM);</tt><br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; return(error);</tt><br>
<tt>&nbsp; &nbsp; }</tt><br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; </tt><br>
<tt>&nbsp; &nbsp; *pObject = *((OBJECT_DESCRIPTOR*)(OSLockBlock(char,bidValue)+sizeof(WORD)));</tt><br>
<br>
<tt>	tempPtr = pObject;</tt><br>
<br>
<tt>&nbsp; &nbsp; ODSReadMemory( &amp;tempPtr, _OBJECT_DESCRIPTOR, &amp;tempObjectPtr, 1 );</tt><br>
<br>
<tt>&nbsp; &nbsp; memcpy(pObject,&amp;tempObjectPtr, ODSLength(_OBJECT_DESCRIPTOR)); </tt><br>
<br>
<tt>&nbsp; &nbsp; if (pObject-&gt;ObjectType != OBJECT_FILTER_LEFTTODO)</tt><br>
<tt>&nbsp; &nbsp; { &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; </tt><br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; printf (&quot;Error: object '%s' unknown type.\n&quot;,FILTER_LEFTTODO_ITEM);</tt><br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; OSUnlockBlock(bidValue);</tt><br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; return (ERR_RUNMACRO_BADOBJECTTYPE);</tt><br>
<tt>&nbsp; &nbsp; }</tt><br>
<br>
<tt>&nbsp; &nbsp; error = NSFDbReadObject(hDb, pObject-&gt;RRV, 0, MAXDWORD, phLeftToDo);</tt><br>
<tt>&nbsp; &nbsp; OSUnlockBlock(bidValue);</tt><br>
<tt>&nbsp; &nbsp; if (error)</tt><br>
<tt>&nbsp; &nbsp; {</tt><br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; printf (&quot;Error: unable to read object '%s'.\n&quot;,FILTER_LEFTTODO_ITEM);</tt><br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; return (error);</tt><br>
<tt>&nbsp; &nbsp; }</tt><br>
<br>
<tt>&nbsp; &nbsp; ptable = OSLock(void, *phLeftToDo);</tt><br>
<tt>&nbsp; &nbsp; *ptdLeftToDoTime = IDTableTime(ptable);</tt><br>
<tt>&nbsp; &nbsp; *pwLeftToDoFlags = IDTableFlags(ptable);</tt><br>
<tt>&nbsp; &nbsp; OSUnlock(*phLeftToDo); &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* unlock handle we are done with */</tt><br>
<br>
<tt>&nbsp; &nbsp; return NOERROR;</tt><br>
<tt>}</tt><br>

<p>
<p><b><font size="4" color="#000080">$Period</font></b><br>
<br>
The $Period field (FILTER_PERIOD_ITEM) is required in all Release 3 Background agents. The data type is TYPE_TEXT. The value is a character digit -- '0', '1',  '2', or '3' -- corresponding to one of the filter periods defined in stdnames.h.<br>
<br>
The value stored in the $Period field encodes one of the schedule settings in the &quot;When should this agent run&quot; setting. When you create an agent with the Notes user interface, you specify this setting in the Create - Design - Agent dialog box. The following table maps the filter period symbolic constants in stdnames.h to this setting in the dialog box:<br>
<br>
<b>Filter Period Symbol</b>		<b>Frequency Setting</b><br>
<tt>PERIOD_HOURLY</tt>	hourly<br>
<tt>PERIOD_DAILY</tt>	daily<br>
<tt>PERIOD_WEEKLY</tt>	weekly<br>
<tt>FILTER_DISABLED</tt>	Never<br>
<br>
The symbolic constants are defined as numbers between 0 and 3, but the value stored in the item is a character. The code fragment below translates the filter period symbolic constant to the corresponding character before setting the $Period field. 
<table width="100%" border="1">
<tr valign="top"><td width="100%"><b>addmacro.c - Setting the $Period Field</b></td></tr>
</table>
<tt><font size="2">/*</font></tt><tt><font size="2">&nbsp;wPeriod must be PERIOD_HOURLY, PERIOD_DAILY,</font></tt><br>
<tt><font size="2">&nbsp; &nbsp;PERIOD_WEEKLY, or PERIOD_DISABLED</font></tt><br>
<tt><font size="2">*/</font></tt><br>
<br>
<tt><font size="2">STATUS &nbsp;LNPUBLIC &nbsp;SetMacroPeriod( NOTEHANDLE hMacro, WORD wPeriod )<br>
{<br>
 &nbsp; &nbsp;STATUS &nbsp; &nbsp; &nbsp;error;<br>
 &nbsp; &nbsp;CHAR &nbsp; &nbsp; &nbsp; &nbsp;cPeriod;<br>
 &nbsp; &nbsp; <br>
 &nbsp; &nbsp;cPeriod = (CHAR)('0' + wPeriod);<br>
 &nbsp; &nbsp;if (error = NSFItemSetText(hMacro,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;FILTER_PERIOD_ITEM, &nbsp; &nbsp; /* &quot;$Period&quot; */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&amp;cPeriod, 1))<br>
 &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp; &nbsp;printf (&quot;Error: unable to set Scan field in macro note.\n&quot;);<br>
 &nbsp; &nbsp;}</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; return(error);<br>
}</font></tt><br>
<br>
<br>
<b><font size="4" color="#000080">$Flags</font></b><br>
<br>
The $Flags field is required in all Release 3 agent notes. The data type is TYPE_TEXT. The value is a string consisting of from one to four characters corresponding to the design flags defined in stdnames.h.The $Flags field is used to manage design components of databases.<br>
<br>
The table below indicates the set of design flags to set for various types of agents:<br>
<br>
<b>Agent Type</b>		<b>Design Flags</b><br>
Menu		DESIGN_FLAG_PRESERVE<br>
Background	DESIGN_FLAG_PRESERVE and 	<br>
			DESIGN_FLAG_BACKGROUND_FILTER<br>
Execute Once	DESIGN_FLAG_PRESERVE<br>
Paste/mail	DESIGN_FLAG_PRESERVE and DESIGN_FLAG_MAIL_FILTER<br>
Search		DESIGN_FLAG_QUERY_MACRO_FILTER<br>
Lotus Script Data	DESIGN_FLAG_V4AGENT_DATA<br>
<br>
<br>
<b><font size="4" color="#000080">Other Components of Release 3 Agent Notes</font></b><br>
<br>
The <b>$Comment</b> field is an optional TYPE_TEXT field in any Release 3 agent note. The $Comment field contains the text of the comment in the agent. Database designers can provide comments to help others understand or maintain their agents.<br>
<br>
Full text search agents can contain fields with the names $SimpleQuery, $BuilderQuery, and  $FormulaAction. These items contain values derived from settings in the search bar or the query builder dialog box.<br>
<br>
<br>
<b><font size="5" color="#000080">Running Release 3 Agents</font></b><br>
<br>
This section outlines the steps required to use the C API to run a Release 3 agent on a database. The exact functionality required depends on the agent itself and the context of the C API program.<br>
<br>
Generally, a C API program runs an agent on a database by implementing the following algorithm:<br>

<ol type="1">
<li>Read the agent note.
<li>Determine the documents to process.
<li>For each document:<br>
- Open the document.<br>
- Evaluate the agent formula.<br>
- Perform the agent operation (update or copy).<br>
- Close the document.
<li>If necessary, update the agent note.</ol>
<br>
<br>
<b><font size="4" color="#000080">Access the Agent Note</font></b><br>
<br>
Any C API program attempting to run an agent in a database must open the database, open the agent note, and read the required fields -- &amp;Type, $Operation, and $Scan. <br>
<br>
Most C API programs obtain the name of the agent as input from the user or from a parameter. Given the agent name, use NIFFindDesignNote (specifying NOTE_CLASS_FILTER) to obtain the note ID of the agent note.<br>
<br>
Given the note ID of the agent note, use NSFNoteOpen to open the agent note. Read the required fields &amp;Type, $Operation, and $Scan as shown in the code fragments in this chapter. Use the values of these fields to verify that the program can run the agent.<br>
<br>
All agents except full-text search queries contain a field named $Formula. They may also contain a field named $Formula2. If the agent is not a full-text search query, read the $Formula field and the $Formula2 field if it is available.<br>
<br>
<b><font size="4" color="#000080">Determine the Documents to Process</font></b><br>
<br>
Determine the set of documents to process -- the set of documents the agent should examine, not the set that matches the SELECT portion of the formula. Later, your program will evaluate the agent formula for each document in this set. Evaluating the formula determines whether a given document matches the SELECT criteria or not.<br>
<br>
This step normally yields an ID table containing the note IDs of all notes the agent should process.<br>
<br>
Use the value of the $Type item, the $Scan item, and other information to build this ID table. For example, if $Type is FILTER_TYPE_ONCE, your C API program must normally obtain a single note for the agent to process.<br>
<br>
If $Scan is FILTER_SCAN_ALL, the set of documents should include all documents in the database. If $Scan is FILTER_SCAN_VIEW, then your C API program must select -- or be given -- a particular view in the database. Build an ID table containing the IDs of all entries in this view.<br>
<br>
If $Scan is FILTER_SCAN_NEW, your program must determine what documents have been added to the database, modified, or removed from the database since the last time the agent ran. Start with the ID table stored in the $LeftToDo object. Evaluate whether this ID table applies in the context of the current database and agent note, then update the table as necessary. The sample program runmacro.c uses the function GetIDsOfAllNewDocs to demonstrate how to build an ID table of all the documents that need to be processed if $Scan is FILTER_SCAN_NEW.<br>
<br>
If the agent contains a $Query item, your C API program will need to perform a full-text query to determine the documents to process.<br>
<br>
<b><font size="4" color="#000080">Evaluate the Formulas</font></b><br>
<br>
Process all the documents in the set determined by the preceding step. However, before starting this process, call the C API function NSFComputeStart for the compiled agent formulas $Formula and -- if available -- $Formula2. Each call to NSFComputeStart yields an HCOMPUTE structure used later in NSFComputeEvaluate.<br>
<br>
Loop through the note IDs in the table of IDs to process. For each ID in the table, open the document and evaluate the agent formula. Call the C API function NSFComputeEvaluate to evaluate a formula on one document. This may change fields in the document or take other actions. It yields three pieces of information:<br>

<ul type="disc">
<li>Whether the document matches the SELECT criteria
<li>Whether the document should be deleted
<li>Whether the document has been modified as result of evaluating the formula</ul>
<br>
Call NSFComputeEvaluate to evaluate the second formula on the document if:<br>

<ul type="disc">
<li>The optional secondary formula $Formula2 was given in the agent note
<li>The document matches the SELECT criteria
<li>The document is not to be deleted</ul>
<br>
The code fragment below shows how to evaluate the two formulas for each document being processed.
<table width="100%" border="1">
<tr valign="top"><td width="100%"><b>runmacro.c - Evaluating the Formulas</b></td></tr>
</table>
<tt>/* Compute the first formula on the document. */<br>
 &nbsp; &nbsp;if (fCompute1Started)<br>
 &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp; &nbsp;if (error = NSFComputeEvaluate( <br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;hCompute1, &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* returned from NSFComputeStart */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;hDoc, &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; /* This note provides any additional<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; variable used by the formula. It<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; also gets FIELD variables assigned<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; during the evaluation. */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;NULLHANDLE, &nbsp; &nbsp; &nbsp; &nbsp; /* don't need the ComputeResult */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;NULL, &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; /* don't need Compute Result Len */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &amp;fDocMatchesFormula1,/* gets TRUE if note matches the<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; SELECT portion of the formula */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &amp;fDocShouldBeDeleted1,/* gets TRUE if formula <br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; indicates note should be deleted*/<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &amp;fDocModified1 )) &nbsp; &nbsp;/* gets TRUE if any of the fields<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; of hDoc were modified as result</tt><br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;of the formulat evaluation. */<br>
 &nbsp; &nbsp; &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;printf (&quot;Error: unable to compute forumula on document.\n&quot;);<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;goto Exit1;<br>
 &nbsp; &nbsp; &nbsp; &nbsp;}<br>
 &nbsp; &nbsp;}<br>
 &nbsp; /* <br>
 &nbsp; &nbsp;* Proceed to compute the second (optional) formula on the note if<br>
 &nbsp; &nbsp;* there is a second formula and the note matched the SELECT portion<br>
 &nbsp; &nbsp;* of the first formula and the first formula does not indicate that<br>
 &nbsp; &nbsp;* the note should be deleted.<br>
 &nbsp; &nbsp;*/<br>
 &nbsp; &nbsp;if (fCompute2Started &amp;&amp; fDocMatchesFormula1 &amp;&amp; !fDocShouldBeDeleted1)<br>
 &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp; &nbsp;if (error = NSFComputeEvaluate( hCompute2, hDoc, NULLHANDLE, NULL,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &amp;fDocMatchesFormula2,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &amp;fDocShouldBeDeleted2,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &amp;fDocModified2 ))<br>
 &nbsp; &nbsp; &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;printf (&quot;Error: unable to compute formula 2 on document.\n&quot;);<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;goto Exit1;<br>
 &nbsp; &nbsp; &nbsp; &nbsp;}<br>
 &nbsp; &nbsp;}</tt><br>
<br>
<b><font size="4" color="#000080">Perform the Operation</font></b><br>
<br>
After evaluating the formulas on the document, update the document as a new document or as the original, depending on the value of the $Operation field.<br>
<br>
If the $Operation field specifies FILTER_OP_NEW_COPY, zero out the NOTEID and generate a new OID in the header data of the document note. This causes NSFNoteUpdate to leave the original document unchanged and write the changed document in memory to disk as a new note.<br>
 <br>
Update and close the modified document.<br>
<br>
<br>
<b><font size="4" color="#000080">Maintain the $LeftToDo Object</font></b><br>
<br>
If $Scan is FILTER_SCAN_NEW, your program must maintain the $LeftToDo object in the agent note. <br>
<br>
To properly update the $LeftToDo object, your program must retrieve the original object from the agent note, update the ID table with any documents that were added to or deleted from the database while the agent was running, and remove from the table the IDs of all documents processed by the agent.<br>
<br>
The sample program RUNMACRO.C uses the function UpdateLeftToDo to demonstrate how to update the ID table in the $LeftToDo object and save the object back to disk after running an agent.
---
