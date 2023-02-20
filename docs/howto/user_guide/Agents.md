##### Chapter 8-5
##### Agents

<br>
<b><font size="5" color="#000080">Introduction</font></b><br>
<br>
Agent notes, like form and view notes, are design notes of class NOTE_CLASS_FILTER that reside in databases. Domino application developers design agents to automate operations on documents in a database.<br>
<br>
Agent notes consist of a document selection formula, a trigger, and one or more actions.  An action can be a Domino-supplied action, an @function formula, a LotusScript program or a Java program. The actions work on a preselected set of documents, triggered by a predetermined time or event. You can create personal (private) agents and shared agents. For complete information on types of agents and how they are used, refer to the Domino or Notes user documentation or help.<br>
<br>
The agent interface provides a facility to create, test, execute, and view the results of agents for a particular database. This interface introduces several on-disk structures required to properly manage the note via the C API. The queryods.h and stdnames.h include files define the associated data types and constants that comprise the agent note. When you inspect these include files, note that the terms &quot;assistant&quot; and &quot;agent&quot; are synonymous. Domino and Notes also provide a set of C API functions that support the execution of<font color="#FF0000"> </font>agent notes (it is important to note that agents that run through the C API are unknown to the Agent Manager). The agents.h include file defines the function prototypes and supporting data types and constants. <br>
<br>
<b><font size="5" color="#000080">Thread Support</font></b><br>
<br>
Agents may run on more than one thread but should be given a run context per thread.  Each run context can be used for multiple agents. <br>
<br>
This chapter describes the kinds of agents, details the components that make up the corresponding design notes, and illustrates how to properly execute an agent and report any results.<br>
<br>
<b><font size="5" color="#000080">Cross-Platform implementation</font></b><br>
<br>
C API programs that run on non-Intel based platforms such as UNIX, must convert certain types of data between host-specific format and Domino canonical format when creating or accessing item data.  Please refer to the &quot;Domino Cannonical Format&quot; chapter and to the sample source file agents.c for detailed explanations.<br>
<br>
<b><font size="5" color="#000080">The AGENTS Sample Programs</font></b><br>
<br>
The sample programs in dbdesign\agents illustrate how to use the C API to create, execute, and view the results for a subset of agent types and agent note variations. <br>
<br>
The sample program agents.exe (agents in UNIX) creates four agent notes that reside in the sample database problems.nsf, including: <br>

<ul type="disc">
<li>A manual (menu command), shared, Formula-based agent action run against the currently selected document
<li>A disabled, private, background, LotusScript agent action triggered and run against new and/or modified documents
<li>An enabled, shared, scheduled, Formula-based agent action run against all documents once a month
<li>A manual (menu command), shared, Java agent action run against all documents in the database</ul>
<br>
The sample uses general purpose subroutines to create the various agent note items. Subroutine arguments support the settings for a particular agent type. The sample routines AddManualAgent, AddBackgroundAgent,  AddScheduledAgent, and AddJavaAgent drive the appropriate settings for the four sample agent types.<br>
<br>
The sample program ragents.exe (ragents in UNIX) executes the background and scheduled agents created by agents and reads and displays the results. It calls the sample routine RunTriggeredAgents to call the general purpose routines for executing the agent notes and analyzing the results, based on the agent action type. <br>
<br>
We recommend that you refer to the agents and ragents programs code (agents.c and ragents.c) as you read this chapter.<br>
<br>
<br>
<b><font size="5" color="#000080">Components of Agent Notes</font></b><br>
<br>
Agents are design notes that reside in a database. Use NSFNoteCreate to create them. Shared agent notes are of class NOTE_CLASS_FILTER; private agent notes are of class<font color="#FF0000"> </font>NOTE_CLASS_FILTER | NOTE_CLASS_PRIVATE.<br>
<br>
The following items comprise an agent note and are required to manage and execute an agent note from the agent interface.   <br>
<br>
<b>Field Name	Description	Sample Reference</b><br>
$TITLE	Agent name	SetAgentTitle<br>
$Comment	Agent description	SetAgentComment<br>
$Flags	Design flags	SetAgentDesignFlags<br>
$MachineName	Server name where agent runs	SetAgentMachineName<br>
$UpdatedBy	Agent owner	via NSFNoteUpdate<br>
$Signature	Agent owner signature	via NSFNoteSign<br>
$AssistVersion	Agent version stamp	SetAgentVersion<br>
$AssistType	Action type	SetAgentType<br>
$AssistLastRun	Last run time-date	SetAgentLastInfo<br>
$AssistDocCount	Number of processed documents	SetAgentLastInfo<br>
$AssistFlags	Agent flags	SetAgentAssistFlags<br>
$AssistTrigger	Agent trigger type	SetAgentTrigger<br>
$AssistInfo	Selection and execution information	SetAgentInfo<br>
$AssistQuery	Document selection query formula	SetAgentAction         	<br>
$AssistAction	Action formula or script	SetAgentAction<br>
$AssistAction_Ex	Extended action script	SetAgentAction<br>
$AssistRunInfo	Agent run data object	SetAgentRunInfo, GetAgentRunInfo
<ul></ul>
The following sections describe each field and how to configure each field for<font color="#FF0000"> </font>the type of agent being created.    <br>
<br>
<b><font size="4" color="#000080">$TITLE</font></b><br>
The $TITLE item (FIELD_TITLE) is of type TYPE_TEXT and contains a string specifying the agent name.   <br>
<br>
<b><font size="4" color="#000080">$Comment</font></b><br>
The $Comment item (FILTER_COMMENT_ITEM) is of type TYPE_TEXT and contains a<font color="#FF0000"> </font>string describing the agent.<br>
<br>
<b><font size="4" color="#000080">$Flags</font></b><br>
The $Flags item (DESIGN_FLAGS) is of type TYPE_TEXT and contains a character sequence of the constant values (defined in stdnames.h) that describe the agent design. You must use the related constants as follows, based on the desired agent type:<br>

<ul type="disc">
<li>Specify one of the base flags, DESIGN_FLAG_V4AGENT or DESIGN_FLAG_HIDE_FROM_V3. Specify only a base flag to describe a manually-executed, shared agent.
<li>To specify<font color="#FF0000"> </font>a LotusScript agent, add<font color="#FF0000"> </font>DESIGN_FLAG_LOTUSSCRIPT_AGENT<font color="#FF0000">.</font>
<li>To specify<font color="#FF0000"> </font>a private agent, add<font color="#FF0000"> </font>DESIGN_FLAG_PRIVATE_IN_DB<font color="#FF0000">.</font>
<li>To specify<font color="#FF0000"> </font>a scheduled agent or a background agent triggered by a created/modified document, add<font color="#FF0000"> </font>DESIGN_FLAG_V4BACKGROUND_MACRO<font color="#FF0000">.</font>
<li>To specify<font color="#FF0000"> </font>a background agent triggered by a pasted document, add<font color="#FF0000"> </font>DESIGN_FLAG_V4PASTE_AGENT<font color="#FF0000">.</font>
<li>If the search query of the agent is to be shown in the search bar, add<font color="#FF0000"> </font>DESIGN_FLAG_AGENT_SHOWINSEARCH<font color="#FF0000">.</font></ul>
<br>
<b><font size="4" color="#000080">$MachineName</font></b><br>
The $MachineName item (FILTER_MACHINE_ITEM) is of  type TYPE_TEXT and contains the canonical name of the location where the agent runs. This item only applies to scheduled and mail triggered agents and does not need to exist in the design note for other agent types.<br>
<br>
If a scheduled agent runs on the local machine, set the $MachineName value to the user name in canonical format (for example, &quot;CN=John Doe/OU=CAM/O=Lotus&quot;). If it runs on a server, set the $MachineName value to the server name in canonical format.<br>
<br>
For mail triggered agents, set the $MachineName value to the &quot;MailServer&quot; setting from the workstation's notes.ini file. Use OSGetEnvironmentString to read the setting.<br>
<br>
<b><font size="4" color="#000080">$UpdatedBy</font></b><br>
The $UpdatedBy item contains the name of the agent owner, displayed by the Notes agent UI for private agents. This item is automatically appended to the agent note when you use NSFNoteUpdate to write it to the database.<br>
<br>
<b><font size="4" color="#000080">$Signature</font></b><br>
An agent design note requires the signature of its creator. Call NSFNoteSign before adding the note to the database to automatically add this item to the note.<br>
<br>
<b><font size="4" color="#000080">$AssistVersion</font></b><br>
The $AssistVersion item (ASSIST_VERSION_ITEM) is of type TYPE_TIME and contains a time/date stamp for the agent. Update this field with the current time/date every time the agent is modified.<br>
<br>
<b><font size="4" color="#000080">$AssistType</font></b><br>
The $AssistType item (ASSIST_TYPE_ITEM) is of type TYPE_NUMBER and contains a signature constant value appropriate to the type of agent action:<br>
   <br>
<b>Agent Action		$AssistType Value			Include File</b><br>
None			ASSIST_SIG_ACTION_NONE		agents.h<br>
Formula		SIG_ACTION_FORMULA		ods.h<br>
LotusScript		SIG_ACTION_LOTUSSCRIPT    	ods.h<br>
Java			SIG_ACTION_JAVAAGENT		ods.h
<ul>
<ul></ul>
</ul>
<b><font size="4" color="#000080">$AssistLastRun</font></b><br>
The $AssistLastRun item (ASSIST_LASTRUN_ITEM) is of TYPE_TIME and contains the time/date stamp of the last execution of the agent. When you create the agent, you should clear this item, setting the two Innards elements of the TIMEDATE variable to (DWORD) 0. Domino or Notes automatically updates this item for each agent execution.  <br>
<br>
<b><font size="4" color="#000080">$AssistDocCount</font></b><br>
The $AssistDocCount item (ASSIST_DOCCOUNT_ITEM) is of type TYPE_NUMBER and contains the number of documents processed by the last execution of the agent. When you create the agent, initialize this item to zero. Domino or Notes automatically updates this item for each agent execution.<br>
<br>
<b><font size="4" color="#000080">$AssistFlags</font></b><br>
The $Assist Flags item (ASSIST_FLAGS_ITEM) is of type TYPE_TEXT and contains a character sequence of constant values (defined in stdnames.h) used to describe miscellaneous agent attributes that are used by the Notes agent UI. Use the related constants as follows:   <br>

<ul type="disc">
<li>If the agent is manually executed, an enabled background agent, or an enabled scheduled agent, use ASSIST_FLAG_ENABLED.
<li>If the agent is not a shared agent, use ASSIST_FLAG_PRIVATE.
<li>If the agent is manually executed from the agent list only (that is, it is called by a different agent), use ASSIST_FLAG_HIDDEN.
<li>If the agent is disabled, shared, and unhidden, specify an empty string (&quot;&quot;). </ul>
<br>
<b><font size="4" color="#000080">$AssistTrigger</font></b><br>
The $AssistTrigger item (ASSIST_TRIGGER_ITEM) is of type TYPE_TEXT and contains a constant value that describes the event that triggers the agent. The associated literals are defined in queryods.h and assigned to the item as follows:<br>
<br>
<b>Agent Trigger	$AssistTrigger Value</b><br>
Manual		ASSISTTRIGGER_TYPE_MANUAL<br>
If Document is pasted	ASSISTTRIGGER_TYPE_PASTED<br>
If Document is updated	ASSISTTRIGGER_TYPE_DOCUPDATE		<br>
If New Mail has arrived 	ASSISTTRIGGER_TYPE_NEWMAIL<br>
If Scheduled event	ASSISTTRIGGER_TYPE_SCHEDULED<br>
Not defined (empty)	ASSISTTRIGGER_TYPE_NONE
<ul>
<ul></ul>
</ul>
<b><font size="4" color="#000080">$AssistQuery</font></b><br>
The $AssistQuery item (ASSIST_QUERY_ITEM) is of type TYPE_QUERY and consists of a CD record sequence that defines a front end search query, used to narrow the document selection against which the agent runs. Even if you do not want a search query, this item still requires an appended CDQUERYHEADER record (SIG_QUERY_HEADER signature). If you include<font color="#FF0000"> </font>a search query, append one of the following CD records and related packed data to the $AssistQuery item:<br>
<br>
<b>Query type	CD Record	CD Signature	Packed Data</b><br>
By field	CDQUERYBYFIELD	SIG_QUERY_BYFIELD	Field name, field value<br>
By folder	CDQUERYBYFOLDER	SIG_QUERY_BYFOLDER	Folder name<br>
By form	CDQUERYBYFORM	SIG_QUERY_BYFORM	ODS_ASSISTSTRUCT records, form name<br>
Formula 	CDQUERYFORMULA	SIG_QUERY_FORMULA	Compiled formula<br>
Text search	CDQUERYTEXTTERM	SIG_QUERY_TEXTTERM	Text strings<br>
Uses form	CDQUERYUSESFORM	SIG_QUERY_USESFORM	Form name LIST
<ul></ul>
<b><font size="4" color="#000080">$AssistInfo</font></b><br>
The $AssistInfo item (ASSIST_INFO_ITEM) is of  TYPE_ASSISTANT_INFO and provides the control information Domino or Notes uses to determine when and against which documents the agent should run. This corresponds to the data entered in the Notes agent dialogs &quot;When should this agent run?&quot; and &quot;Which document(s) should it act on?&quot;<br>
<br>
The ODS_ASSISTSTRUCT structure contains the information for the $AssistInfo item. It is defined in queryods.h and described as follows:<br>
<br>
<tt><font size="2">typedef struct<br>
	{<br>
	WORD wVersion;	/* Structure version */</font></tt><br>
<tt><font size="2">	WORD wTriggerType;	/* Type of trigger */<br>
	WORD wSearchType;	/* Type of search */<br>
	WORD wIntervalType;	/* Type of interval */<br>
	WORD wInterval;	/* Interval */<br>
	DWORD dwTime1;	/* depends on interval type */<br>
	DWORD dwTime2;	/* depends on interval type */</font></tt><br>
<tt><font size="2">	TIMEDATE StartTime;	/* Agent does not run before this time */<br>
	TIMEDATE EndTime;	/* Agent does not run after this time */</font></tt><br>
<tt><font size="2">	DWORD dwFlags;			</font></tt><br>
<tt><font size="2">	DWORD dwSpare[16];<br>
	} ODS_ASSISTSTRUCT;</font></tt><br>
<br>
Set the reserved wVersion and dwSpare fields to 0.<br>
<br>
The wTriggerType field describes the event that triggers the agent. The ASSISTTRIGGER_TYPE_xxx  constants define the valid values for this field. The value must be identical to the one assigned to the $AssistTrigger item.<br>
<br>
The wSearchType field describes the method for determining which documents are applied to the agent action for a particular type of trigger. The ASSISTSEARCH_TYPE_xxx constants define the valid values for this field. The following table identifies the valid values, based on the trigger type specified in the wTriggerType field.
<ul></ul>
<b>If</b><b><u>	wTriggerType	</u></b><b>   Use</b><b><u>	wSearchType 	</u></b><b>To Run Agent Against</b>
<ul>ASSISTTRIGGER_	ASSISTSEARCH_	<br>
TYPE_MANUAL	TYPE_ALL	All documents in the database<br>
		TYPE_NEW	Newly added documents <br>
		TYPE_MODIFIED	Newly modified documents<br>
		TYPE_SELECTED	Selected documents in the view<br>
		TYPE_VIEW	All documents in the view<br>
		TYPE_UNREAD	All unread documents in the view	<br>
		TYPE_UI	Current document (run once)
<ul></ul>
TYPE_PASTED	TYPE_NONE	Newly pasted documents	
<ul></ul>
TYPE_DOCUPDATE	TYPE_NONE	Newly updated documents
<ul></ul>
TYPE_NEWMAIL	TYPE_NONE	Newly received mail documents
<ul></ul>
TYPE_SCHEDULED	TYPE_ALL	All documents in the database 
<ul>	TYPE_NEW	All new documents<br>
	TYPE_MODIFIED	All modified documents<br>
</ul>
TYPE_NONE	TYPE_NONE	No documents</ul>
<br>
The wIntervalType and wInterval fields only apply to scheduled agents. Together, they define how often Domino runs the agent. The wIntervalType field describes the interval type (minutes, days, weeks, or months) and the wInterval field describes the interval amount between executions of the scheduled agent. The  ASSISTINTERVAL_TYPE_xxx constants define the valid wIntervalType values. Both fields are ignored if wTriggerType does not equal ASSISTTRIGGER_TYPE_SCHEDULED.<br>
<br>
For example, if wIntervalType = ASSISTINTERVAL_TYPE_DAYS and wInterval = 2, Domino executes the agent once every two days.  <br>
<br>
The dwTime1 and dwTime2 fields also apply only to scheduled agents. Together, they further refine the schedule for the wIntervalType value, as described in the following table. Both of these fields are ignored if wTriggerType does not equal ASSISTTRIGGER_TYPE_SCHEDULED.
<ul>
<ul></ul>
</ul>
<b>wIntervalType	dwTime1	dwTime2</b><br>
ASSISTINTERVAL_TYPE_<br>
MINUTES	Starting time 	Ending time 		<br>
DAYS	Time of day 	Ignored	<br>
WEEK	Time of day 	Day of the week (Sunday == 1)<br>
MONTH	Time of day  	Day of the month	<br>
<br>
Note that the time units are in ticks since midnight GMT. Use the appropriate TICKS_IN_xxx constant values, declared in the misc.h include file, to determine this value. For example, if wIntervalType = ASSISTINTERVAL_TYPE_MONTH, wInterval = 1, dwTime1 = 5*TICKS_IN_HOUR, and dwTime2 = 1, Domino executes the agent on the first day of every month at 5 AM.   <br>
<br>
The StartTime and EndTime fields apply to all scheduled agents and background agents triggered by new or modified documents. They define the starting and ending time/dates on which Domino executes the agent. Use the relevant C API routines, declared in the misc.h and ostime.h include files, to set the values for these fields. If you do not want to set a starting and/or ending time, set the field's TIMEDATE structure to 0. Both of these fields are ignored if wTriggerType is not set to ASSISTTRIGGER_TYPE_SCHEDULED or ASSISTTRIGGER_TYPE_DOCUPDATE.<br>
<br>
The dwFlags field contains miscellaneous information about the agent. The ASSISTODS_FLAG_xxx constants, declared in queryods.h, provide the valid values for this field. The following table describes each constant with respect to the types of agents that apply. This field must be set to 0 if none of the constants apply.<br>
<br>
<b>ASSISTODS_FLAG_	Description	Applicable agent $AssistInfo values</b><br>
HIDDEN	Hidden agent (that is, 	ASSISTTRIGGER_TYPE_MANUAL
<ul> 	ASSIST_FLAG_HIDDEN)<br>
</ul>
NOWEEKENDS	Do not run on weekends	ASSISTTRIGGER_TYPE_DOCUPDATE;
<ul>		ASSISTTRIGGER_TYPE_SCHEDULED <br>
		and ASSISTINTERVAL_TYPE_HOURS;<br>
		ASSISTTRIGGER_SCHEDULED <br>
		and ASSISTINTERVAL_TYPE_DAYS<br>
</ul>
CHOOSEWHENENABLED	Force server dialog when 	ASSISTTRIGGER_TYPE_DOCUPDATE;
<ul>	agent is enabled by the user 	ASSISTTRIGGER_TYPE_SCHEDULED<br>
</ul>
STOREHIGHLIGHTS	Store search query highlights	All agent notes
<ul>	in the document</ul>
<br>
<b><font size="4" color="#000080">$AssistAction</font></b><br>
The $AssistAction item (ASSIST_ACTION_ITEM) is of type TYPE_ACTION and consists of one or two CD records that define what the agent should do when it executes. The sequence consists of one CDACTIONHEADER header record followed by one CDACTIONFORMULA action record, one CDACTIONLOTUSSCRIPT action record, or no action record, depending on the type of action specified by the value for $AssistType item.<br>
<br>
<b><font color="#000080">CDACTIONHEADER</font></b><br>
The CDACTIONHEADER record is the first CD record in the agent action item. It has a CD record signature of SIG_ACTION_HEADER. If the value for the $AssistType item is ASSIST_SIG_ACTION_NONE, no other CD records are appended to the agent action item. <br>
<br>
<b><font color="#000080">CDACTIONFORMULA</font></b><br>
If the value for the $AssistType item is SIG_ACTION_FORMULA, the CDACTIONFORMULA record is the second CD record appended to the agent action item. This structure has a CD header record signature of SIG_ACTION_FORMULA and a header length equal to the structure size plus the length of the packed formula object that follows. The dwFlags field specifies additional formula options, if any, as defined by the ACTIONFORMULA_FLAG_xxx constant values in queryods.h. The wFormulaLen field is set to the even byte boundary length of the compiled formula object that follows this structure.<br>
<br>
<b><font color="#000080">CDACTIONLOTUSSCRIPT</font></b><br>
If the value for the $AssistType item is SIG_ACTION_LOTUSSCRIPT, the CDACTIONLOTUSSCRIPT record is the second CD record appended to the agent action item.    This structure has a CD header record signature of SIG_ACTION_LOTUSSCRIPT and a header length equal to the structure size plus the length of the packed LotusScript subroutine that follows. Set the reserved dwFlags field to 0. The dwScriptLen field is set to the even byte boundary length of the LotusScript subroutine source that follows this structure.<br>
<br>
NOTE: A background agent should not refer to the UI (front-end) classes, because it has no knowledge of the context.  See the <b>Running Agent </b>section below for possible errors.<br>
<br>
NOTE: To execute properly, the LotusScript source appended to the agent action item must be contained in the Initialize event subroutine. Once the agent is attached, you can view this source from the Notes agent UI by selecting the Initialize event. You can manually select the agent for test and execution from the Notes UI. Since the Notes LotusScript IDE expects the script source to be formatted with specific event comments, the error message box &quot;Generic LSE Failure&quot; will appear when you exit the Notes UI Agent view of the script source. Likewise, you cannot edit and save the agent action script through the agent UI. This limitation is due to the missing API support for importing generic LotusScript source into the IDE format. A future Notes release will support agent integration with the Notes Agent UI and the<font color="#FF0000"> </font>LotusScript IDE.
<ul>
<ul></ul>
</ul>
<b><font color="#000080">CDACTIONJAVAAGENT</font></b><br>
If the value for the $AssistType item is SIG_ACTION_JAVAAGENT, the CDACTIONJAVAAGENT record is the second CD record appended to the agent action item.    This structure has a CD header record signature of SIG_ACTION_JAVAAGENT and a header length equal to the structure size plus the length of the java class name, java class code path, java class file list plus two null fields that follow. Set the reserved dwSpare[2] fields to 0. <br>
<br>
<b><font size="4" color="#000080">$FILE</font></b><br>
The $FILE item (ITEM_NAME_ATTACHMENT) required only for a Java Agent, is of type TYPE_OBJECT and contains information related to the Java Agent executable file.  The value of this item is a structure of type FILE_OBJECT.  Use NSFNoteAttachFile to add this item to the database.<br>
 <br>
<b><font size="4" color="#000080">$AssistAction_Ex</font></b><br>
The $AssistAction_Ex item (ASSIST_EXACTION_ITEM) is of type TYPE_LSOBJECT and contains the compiled LotusScript object for a LotusScript agent action type. Domino and Notes uses the compiled object in lieu of run-time compilation of the script during agent execution. This item is required for all Agent types, although it<font color="#FF0000"> </font>only contains<font color="#FF0000"> </font>usable information in the case of LotusScript agent actions. In previous releases of Domino and Notes, you could not programmatically compile LotusScript source, and his item contained the address of the $AssistAction agent action item.<br>
 <br>
<b><font size="4" color="#000080">$AssistRunInfo</font></b><br>
The $AssistRunInfo item (ASSIST_RUNINFO_ITEM) is of type TYPE_OBJECT and attaches a run information object used by Domino and Notes to store execution data. Call NSFDbAllocObject to allocate the attached object. If the agent is shared, the object is a public note and has a note class of NOTE_CLASS_DOCUMENT. If the agent is private, access to the object is restricted to the owner and it has a note class of NOTE_CLASS_FILTER | NOTES_CLASS_PRIVATE. The object contains<font color="#FF0000"> </font>the object descriptor item followed by<font color="#FF0000"> </font>the object run data.   <br>
<br>
The object descriptor item consists of the TYPE_OBJECT object type followed by an OBJECT_DESCRIPTOR structure, in which the RRV field is set to the allocated object ID and the ObjectType field is set to the OBJECT_ASSIST_RUNDATA constant (defined in nsfdata.h). Call NSFDbItemAppendObject to assign the object descriptor item to the $AssistRunInfoItem.<br>
<br>
The object run data consists of a sequence of CD records that contain the run data information.   When you create an agent note, you must provide an initial placeholder for the first two CD records of the object run data -- specifically, one ODS_ASSISTRUNOBJECTHEADER structure followed by one ODS_ASSISTRUNOBJECTENTRY structure. Domino or Notes adds and/or modifies the remaining CD records after subsequent agent executions. Call NSFDbWriteObject and NSFDbReadObject to write and read all of the object run data records.<br>
<br>
<b><font color="#000080">ODS_ASSISTRUNOBJECTHEADER</font></b><br>
The ODS_ASSISTRUNOBJECTHEADER structure contains the number of run data object entries, as specified by the wEntries field. When you create the agent note (that is, the agent has not executed), set the wEntries field to 1. After the agent note executes, Domino or Notes updates the wEntries field to the actual number of run data object entries. By default, Domino or Notes creates five run data object entries. Set the reserved dwFlags and wSpare elements to 0. <br>
<br>
<b><font color="#000080">ODS_ASSISTRUNOBJECTENTRY</font></b><br>
At least one ODS_ASSISTRUNOBJECTENTRY structure entry follows the run data object header record. It is defined as follows:  <br>
<br>
When creating the agent, there should be a single entry with a length of zero, as specified by the dwLength field. Domino or Notes creates and reserves at least five (the default number) run data object entries. The first run data entry contains the run information structure ODS_ASSISTRUNINFO and the third run data entry contains the agent log string that is displayed after executing the agent from the Notes UI. To determine that the agent has executed, you should verify that the length specified by the dwLength field for both the first and third entry is greater than 0. The remaining entries<font color="#FF0000"> </font>are reserved for luse by Domino or Notes.<br>
<br>
Set the reserved dwFlags field to 0.   <br>
<br>
<b><font color="#000080">ODS_ASSISTRUNINFO</font></b><br>
The ODS_ASSISTRUNINFO record is the first run data object to follow the run data object entry record sequence created by Domino or Notes. If available, this structure (defined in queryods.h) contains the following run information for the last execution of the agent:    <br>
<br>
<tt><font size="2">typedef struct<br>
	{<br>
	TIMEDATE LastRun;	/* Time of last agent run */<br>
	DWORD dwProcessed;	/* Number of documents processed on last run */<br>
	TIMEDATE AssistMod;	/* Time date of last assistant modification */<br>
	TIMEDATE DbID;	/* DbID on which assistant was last run */<br>
	LONG dwExitCode;	/* Exit code when assistant was last run */<br>
	DWORD dwSpare[4];<br>
	} ODS_ASSISTRUNINFO;</font></tt><br>
<br>
The LastRun field is the time/date of the last execution.   <br>
<br>
The dwProcessed field specifies the number of documents modified by the last run of the agent. This value is  only valid for formula-based agent actions. Since LotusScript agent actions run once, Domino and Notes cannot determine the number of documents modified and the value is not reported to this field.<br>
<br>
The AssistMod field contains the time/date for the last modification of the agent.  <br>
<br>
The DbID field contains the replica ID<font color="#FF0000"> </font>of the database against which the agent last ran.<br>
<br>
The dwExitCode field holds the return code from the last agent execution.<br>
<br>
The dwSpare field is reserved and should be set to 0.<br>
<br>
<b><font color="#000080">Agent Log</font></b><br>
The agent log is the third run data object created and/or modified by Domino or Notes. It contains the null-terminated character string displayed by the Notes Agent UI after the agent executes.<br>
<br>
<br>
<b><font size="5" color="#000080">Running Agents</font></b><br>
<br>
The agents.h<font color="#FF0000"> </font>include file declares and defines the functions, data types, and symbolic constants used to properly execute an agent note residing in the database. This section describes how to use the C API to execute agent notes. For additional information, see the ExecuteAgent and GetAgentRunInfo routines from the AGENTS sample program in ragents.c.<br>
<br>
Follow these steps to use the C API to run an agent. For details, look for the subroutines in the AGENTS sample program, ragent.c, that are mentioned in parentheses below.   <br>
<br>
1. Open a run handle for the agent note. (OpenAgent) <br>
Call AgentOpen to return a handle of type HAGENT that is associated with the specifed agent note and database. Domino and Notes uses the resources provided by the agent run handle when you use AgentRun to<font color="#FF0000"> </font>execute the agent. To locate the agent note ID to pass to AgentOpen in an open database, call NIFFindDesignNote for shared agent notes or NIFFindPrivateDesignNote for private agent notes.  <br>
<br>
The agent run handle returned by AgentOpen is thread-safe but can only be referenced by the thread that created it. You must call AgentClose to free the agent run handle before reusing it with a different agent note or exiting.<br>
<br>
2. Create an agent run-time context handle. (SetRunContext)<br>
Call AgentCreateRunContext to create an agent run-time context handle of type HAGENTCTX that can be used with all subsequent agent executions. The agent run-time context maintains execution information for the agent run handle it is paired with when you call AgentRun. Note that, although required by AgentRunContext, the run handle input parameter is ignored<font color="#FF0000"> </font>by and not relevent to AgentCreateRunContext.   <br>
<br>
The run-time context handle is also thread-safe and can only be used by the thread that created it.   You must call AgentDestroyRunContext to free the runtime context handle before exiting.<br>
<br>
3. Set up a &quot;Parameter Document&quot; for LotusScript agent actions. (SetRunContext)<br>
If the agent to be run has a LotusScript action that uses subroutine input parameters, call AgentSetDocumentContext to assign the note handle to an open document with the current runtime context handle. A subsequent call to AgentRun will pass the note handle to LotusScript via a special property of the back-end NotesSession class, defined as follows:   <br>
<br>
NotesDocument = NotesSession.DocumentContext<br>
<br>
The NotesDocument can be instantiated by the action script routine and its field values can be read in as parameters to the LotusScript subroutine.   <br>
<br>
Since the document context is assigned to the current run-time context handle, you should reset it before each call to AgentRun.<br>
<br>
4. Set up PRINT statement output redirection for LotusScript agent actions. (SetRunContext)<br>
If the agent to be run has a LotusScript action that uses PRINT statements, call AgentRedirectStdout to either disable standard output or redirect it to the log.nsf file or an in-memory buffer. The output of the PRINT statements is assigned to the current run-time context handle and is controlled by the redirType argument of AgentRedirectStdout. You can set this argument to one of the following constant values, defined in agents.h:
<ul></ul>
<b>redirType Value	Redirected Standard Output</b><br>
AGENT_REDIR_NONE	Disabled<br>
AGENT_REDIR_LOG	LOG.NSF<br>
AGENT_REDIR_MEMORY	Memory buffer - reset with each call to AgentRun <br>
AGENT_REDIR_MEMAPPEND	Memory buffer - appended to with each call to AgentRun<br>
<br>
When redirecting to memory, you must call AgentQueryStdoutBuffer after the agent execution to read the output buffer.   <br>
<br>
Since this redirection is associated with the run-time context handle, you can change the desired action before each call to AgentRun.<br>
<br>
5. Execute the agent. (ExecuteAgent)<br>
Call AgentRun to make Domino or Notes run the agent note defined by the specified run handle and run-time context handle arguments. Set the reserved hSelection parameter to 0.  For the dwFlags parameter, if AGENT_REOPEN_DB is set, the AgentRun call will reopen the agent's database with the privileges of the signer of the agent.  If the flag is not set, the agent's &quot;context&quot; database will be open with the privileges of the current user (either the current Notes id, or the current Domino<br>
 web user). The AgentRun routine pends until the desired agent execution has completed.   <br>
<br>
If a background agent erroneously refers to the UI (front-end) classes, you might get one of the following errors:<br>
   If the scripts were included in the Script Libraries, Notes returns <br>
      &quot;Error loading USE or USELSX module: &lt;modulename&gt;&quot; error message;<br>
   otherwise, the AgenRun API returns the &quot;Unknown LotusScript Error&quot; error message.<br>
<br>
6. Get the agent execution results and output. (GetAgentRunInfo, GetScriptRunInfo)<br>
After the agent has executed, retrieve the results and any redirected LotusScript agent output. The execution results are in the $AssistRunInfo item of the agent note. For details about this item and its use, refer to the previous section. If the agent action was LotusScript-based and the current run-time context handle was set to support standard output redirection to an in-memory buffer, you can call AgentQueryStdoutBuffer to retrieve this information. This routine returns a handle to the redirected output and its byte length that is assigned to the specified run-time context handle argument. You can then lock, read, and unlock the returned handle as desired.   Note that this handle is owned by Domino or Notes and must not be freed by the C API program.<br>
<br>
7. Close the agent run handle. (CloseAgent)<br>
When you are through executing a particular agent note, call AgentClose to close the associated run handle. This call also frees any resources associated with the run handle; subsequent calls that use this handle fail unless you perform another call to AgentOpen.   <br>
<br>
8. Close the agent run-time context handle. (CloseAgent)<br>
Call AgentDestroyRunContext to close the current agent run-time context handle. This call also frees the resources associated with the run-time context handle, including the LotusScript document context and redirected standard output handles. Subsequent calls that use this handle fail unless you perform another call to AgentCreateRunContext.<br>
<br>
Note:  On Unix platforms, if you have a C API program which expects to run LotusScript agents, you must either put the program in the Domino executable directory, or put the Domino resource directory on the Path. This must be done so that Unix can find Domino resource files at runtime.
---
