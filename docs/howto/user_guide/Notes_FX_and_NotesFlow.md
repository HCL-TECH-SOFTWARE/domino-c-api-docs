##### Chapter 12-8
##### Notes/FX and NotesFlow

<b><font size="5" color="#000080">Introduction</font></b><br>
 <br>
When an OLE object is embedded in a rich text field of a Domino document, Notes/FX (Notes Field Exchange) provides access to the fields of that document.  The OLE SetData and GetData functions are used to send Notes/FX messages between Domino or Notes and the OLE server.  Through the NotesDocInfo message, Domino or Notes provides a note handle that may be used to read fields in the containing document, and a second handle that is used for updates to or deletions of those fields.  If the OLE server supports the NoteshNote message, the server can also update fields in the active container document so that changes can appear immediately in Notes.<br>
<br>
NotesFlow is designed to support workflow applications built around Domino and Notes.  Actions may be included in the design of a Domino database.  More information on actions may be found in the &quot;Agents&quot; section in this <i>User Guide</i>.  The designer of a form specifies the actions that are available from that form, and identifies the actions that are published for use by OLE objects.  The list of actions is sent to the OLE server as part of the NotesDocInfo message.  When the user selects an action in the OLE server, the server sends a NotesDocAction message to Domino or Notes, which then performs the specified operation.  In addition, by supporting the NotesDocActionDone message the OLE server can also be notified when Domino or Notes completes the requested action.<br>
<br>
The following sections provide the details for how to add Notes/FX and NotesFlow support to an OLE server and the processing necessary for each message.<br>
<br>
<br>
<b><font size="5" color="#000080">Adding Notes/FX and NotesFlow to an OLE Server</font></b><br>
<br>
To add Notes/FX and NotesFlow support to an OLE server:<br>

<ul>1)  Add the supported messages to the SetDataFormats and RequestDataFormats keys in the system registry.  This allows Domino or Notes to determine which messages to exchange with the OLE server.<br>
<br>
2)  When the server starts, obtain a clipboard format ID for each supported message by calling RegisterClipFormat().<br>
<br>
3)  Add support for the NotesDocInfo and, if desired, the NotesDocActionDone messages to the server's SetData method.<br>
<br>
4)  If desired, add support for the NoteshNote or NotesDocAction messages to the server's GetData method.<br>
<br>
5)  When the first NotesDocInfo message is received, load and initialize the C API DLL.  This allows the OLE server to load and run even if Domino or Notes is not installed.  If the OLE server is unable to load and initialize Domino or Notes, the server should operate as if Domino or Notes is not available.<br>
</ul>
<br>
<b><font size="4" color="#000080">Notes/FX and NotesFlow Messages</font></b><br>
<br>
Notes/FX and NotesFlow use the SetData and GetData methods of OLE to send messages between Domino or Notes and the OLE server.  OLE 2 servers may also use the advise sink to advise Domino or Notes of field updates or actions.  There are four messages:<br>

<ul>*  NotesDocInfo	Sent from Domino or Notes to the OLE server.  Provides the basic Notes/FX and NotesFlow information, such as the read and update Note handles, access mode, flags, and, if available, NoteFlow actions.<br>
<br>
*  NoteshNote	Sent from OLE server to Domino or Notes.  Contains a note handle with field updates or deletions.<br>
<br>
*  NotesDocAction 	Sent from OLE server to Domino or Notes.  Requests that a Domino or Notes action be performed.<br>
<br>
*  NotesDocActionDone	Sent from Domino or Notes to the OLE server.  Informs the server that the action has been completed.</ul>
<br>
The OLE server must identify which messages are supported by storing that information in keys in the system registry.  See the &quot;Registry Keys&quot; section for details.  The server must also obtain the clipboard format identifier for each supported message from Windows using the RegisterClipboardFormat() function, as described in the &quot;Clipboard Formats&quot; section.  The same string is used for both the value of the registry key and the clipboard format name.  Further details for handling these message types are given below.<br>
<br>
The following table shows which messages must be supported for each Notes/FX or NotesFlow capability.  Entries in this table are not exclusive;  any combination of capabilities may be used by an application by supporting the required messages.<br>
<br>

<table width="100%" border="1">
<tr valign="top"><td width="31%"><img width="1" height="1" src="../images/Notes_FX_and_NotesFlow0.gif" border="0" alt=""></td><td width="15%"><img width="1" height="1" src="../images/Notes_FX_and_NotesFlow0.gif" border="0" alt=""></td><td width="14%"><div align="right">Message</div></td><td width="20%">Type</td><td width="21%"><img width="1" height="1" src="../images/Notes_FX_and_NotesFlow0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="31%">    Operation</td><td width="15%"><div align="center">NotesDocInfo</div></td><td width="14%"><div align="center">NoteshNote</div></td><td width="20%"><div align="center">NotesDocAction</div></td><td width="21%"><div align="center">NotesDocActionDone</div></td></tr>

<tr valign="top"><td width="31%">Read fields</td><td width="15%"><div align="center">Required</div></td><td width="14%"><img width="1" height="1" src="../images/Notes_FX_and_NotesFlow0.gif" border="0" alt=""></td><td width="20%"><img width="1" height="1" src="../images/Notes_FX_and_NotesFlow0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Notes_FX_and_NotesFlow0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="31%">Modify or delete fields</td><td width="15%"><div align="center">Required</div></td><td width="14%"><img width="1" height="1" src="../images/Notes_FX_and_NotesFlow0.gif" border="0" alt=""></td><td width="20%"><img width="1" height="1" src="../images/Notes_FX_and_NotesFlow0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Notes_FX_and_NotesFlow0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="31%">Update active fields</td><td width="15%"><div align="center">Required</div></td><td width="14%"><div align="center">Required</div></td><td width="20%"><img width="1" height="1" src="../images/Notes_FX_and_NotesFlow0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Notes_FX_and_NotesFlow0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="31%">Send actions</td><td width="15%"><div align="center">Required</div></td><td width="14%"><img width="1" height="1" src="../images/Notes_FX_and_NotesFlow0.gif" border="0" alt=""></td><td width="20%"><div align="center">Required</div></td><td width="21%"><img width="1" height="1" src="../images/Notes_FX_and_NotesFlow0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="31%">Action complete notification</td><td width="15%"><div align="center">Required</div></td><td width="14%"><img width="1" height="1" src="../images/Notes_FX_and_NotesFlow0.gif" border="0" alt=""></td><td width="20%"><div align="center">Required</div></td><td width="21%"><div align="center">Required</div></td></tr>
</table>
<br>
<br>
<b><font size="4" color="#000080">Registry Keys</font></b><br>
<br>
Domino or Notes uses the system registry to identify which Notes/FX and NotesFlow messages the OLE server supports.  These keys should be added to the registry when the program is installed.  The SetData formats must be listed in the key:<br>

<ul>HKEY_CLASSES_ROOT\&lt;ProgID&gt;\protocol\StdFileEditing\SetDataFormats</ul>
<br>
where &lt;ProgID&gt; is the OLE program ID for the application (not the class ID).  The value stored for this key must include NotesDocInfo, and may also include NotesDocActionDone if the server desires those notifications.  For example, the NOTESFLO sample program stores the value &quot;NotesDocInfo,NotesDocActionDone&quot; for this key.  The GetData formats must be listed in the key:<br>

<ul>HKEY_CLASSES_ROOT\&lt;ProgID&gt;\protocol\StdFileEditing\RequestDataFormats</ul>
<br>
The value stored for this key may include either NoteshNote or NotesDocAction, or both, depending on which messages the server supports.  The NOTESFLO sample stores the value &quot;NoteshNote,NotesDocAction&quot; for this key.<br>
<br>
<br>
<b><font size="4" color="#000080">Clipboard Formats</font></b><br>
<br>
Registered clipboard format IDs are used in the SetData and GetData calls to identify the type of data being sent or requested.  In Notes/FX and NotesFlow, these IDs also identify the type of message.  The OLE server must obtain the clipboard format ID for each supported message by calling RegisterClipboardFormat() and providing the appropriate message name string.<br>
<br>
<br>
<b><font size="4" color="#000080">Support for EnumFormats</font></b><br>
<br>
 In OLE 2, the function IDataObject::EnumFormatEtc() may either enumerate these formats, or return the status OLE_S_USEREG, which indicates that the server should obtain that information from the registry.<br>
<br>
<br>
<b><font size="4" color="#000080">Loading and Initializing the HCL C API for Domino and Notes</font></b><br>
<br>
C API applications are usually linked with the Domino and Notes C API import library, notes.lib.  When the application is loaded to be run, the Domino or Notes DLLs are also loaded automatically.  However, most OLE servers should not use this approach:  if the Domino or Notes DLL is not available, the OLE server cannot be loaded and run.  Another concern for OLE servers is locating the Domino or Notes executable directory.  To locate all the DLLs necessary to support the C API, the Domino or Notes executable directory must be in the PATH environment variable.<br>
<br>
For OLE servers, it is recommended that you explicitly load the Domino  and Notes C API DLL through the LoadLibrary() call, only when the HCL C API functions for Domino and Notes are needed.  Pointers to needed API functions may be obtained by calling GetProcAddress().  If the Domino or Notes executable directory is not in the system PATH environment variable, the OLE server should locate Domino or Notes using the system registry.  First, use the registry key HKEY_CLASSES_ROOT\Notes.NotesSession\CLSID to obtain the class ID for Domino or Notes.  Second, use the registry key HKEY_CLASSES_ROOT\&lt;Notes CLSID&gt;\LocalServer.  Remove the program name, and add that directory to the PATH environment variable before calling LoadLibrary().<br>
<br>
Another problem for OLE servers is that calling NotesInit() or NotesInitExtended() while the server is being started will terminate the server.  Internally, NotesInit() yields control to the operating system.  If this happens in Windows while an OLE server is being started, Windows assumes that the attempt to load the server failed.  For OLE servers, it is recommended that you delay calling NotesInit() or NotesInitExtended() until the first NotesDocInfo message is received.<br>
<br>
<br>
<b><font size="5" color="#000080">The NotesDocInfo Message</font></b><br>
<br>
The NotesDocInfo message is sent from Domino or Notes to the OLE server when the following events occur:<br>

<ul>*  When the OLE server is loaded.<br>
*  When an OLE object is created (OleCreate).<br>
*  When there is a change in the access mode for the containing Domino document (read-only to edit or edit to read-only).</ul>
<br>
This message must be supported for any Notes/FX or NotesFlow operation.  The message type NotesDocInfo must be stored in the SetDataFormats key in the system registry.  The clipboard format passed to the SetData method will be the value obtained by calling RegisterClipFormat() and passing NotesDocInfo as the label.<br>
<br>
The fields in this message are:<br>

<ul>Version	Version number of this structure;  currently 0.<br>
<br>
DocLink 	Complete link information for the document containing the OLE object<br>
<br>
DocOpenMode	Open mode for the document:  edit or read-only<br>
<br>
DocFlags	Information about special document conditions;  refer to DOC_FLAGS_xxx in the <i>HCL C API Reference</i> for more information.<br>
<br>
UserAccess	The Edit flag is set if the user has edit access to the document.<br>
<br>
hDocWnd	Handle of the Domino or Notes document window.<br>
<br>
UserName	Name of the current user (from the user's ID file).<br>
<br>
hNote	Read-only note handle to active document.<br>
<br>
hFXNote	Note handle for updates or deletions.<br>
<br>
cNumDocActions	Number of NotesFlow actions<br>
<br>
hDocActions	Handle to array of NOTES_FLOW action structures.  If this handle is non-NULL, the application must call OSMemFree() to free this memory.</ul>
<br>
The simplest way to use NotesFlow is to use the hNote handle while processing the NotesDocInfo message to read fields from the active document and store the hFXNote handle for later updates.  To update any items in the containing document when the OLE object is closed, append the new value to the hFXNote handle using one of the NSFItemAppend() functions and send an OLE_CHANGED (OLE 1) or DataChanged advise (OLE 2) notification to Domino or Notes.  To delete an item, append an item with the same name to the hFXNote with a type of TYPE_UNAVAILABLE.  Changes made via this handle will only be applied after the OLE server is closed.<br>
<br>
Items of type rich text should not be updated through Notes/FX.  When a document is closed, Domino or Notes internally uses the form to update any rich text items in that document.  If an OLE server appends an item with the same name as a rich text item in the form, the item will be overwritten and the server's update will be lost.<br>
<br>
The hNote handle may be used only to read items from the document, and is only valid during the SetData method.  Under no circumstances should an OLE server write to the document using this handle.  If the OLE server needs to read items from the document after the SetData method has completed, the server should make an in-memory copy of the note by calling NSFNoteCopy().  Updates to the note should be made only by using hFXNote or by sending NoteshNote messages.<br>
<br>
Notes/FX and NotesFlow operate using only data held in memory.  If necessary, data is transferred from one process to another using the OLE RPC mechanism.  This means that the note handles supplied in the NotesDocInfo message can only be used for C API calls that manipulate data in memory, such as the NSFItemXxx() calls.  These handles cannot be used for API calls that perform I/O to a database file;  if they are used for such a call, the program will crash.  In effect, the OLE server does not have the database open.  To perform I/O operations, the application must reopen the database.  To do so, call NSFNoteGetInfo() to get the database handle, NSFDbReopen() to get a new database handle, and NSFNoteSetInfo() to associate the note with the open database handle.  The following code sample shows how this is done.<br>
<br>

<table width="100%" border="1">
<tr valign="top"><td width="100%"><b>Establish a Database Context for an OLE Server API Program</b></td></tr>
</table>
<tt><font size="2">/*<br>
 * &nbsp;Get the handle to the database containing the note. Reopen the database<br>
 * &nbsp;to get its context, then read text from the note.<br>
 */</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp;NSFNoteGetInfo(hFXNote, _NOTE_DB, &amp;hMyDbHandle);<br>
 &nbsp; if (sError = NSFDbReopen(hMyDbHandle, &amp;hMyTaskDB))<br>
 &nbsp; 	goto FXReadErr;</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp;NSFNoteSetInfo(hFXNote, _NOTE_DB, &amp;hMyTaskDB); &nbsp; 	</font></tt><br>
<br>
If the NotesDocAction message is listed in the system registry and Domin or Notes actions have been published for OLE servers, the NotesDocInfo message also contains the number of actions supplied and a Domino memory handle to a block of memory containing an array of DOC_ACTION_INFO structures with the message text and action codes.  The OLE server is responsible for freeing this memory block by calling OSMemFree().  Each entry in the array contains:<br>

<ul>ActionID	Code to be passed back to Domino or Notes in a NotesDocAction message.<br>
<br>
NameLength	Length of the name string, in bytes.<br>
<br>
Name	Text string label to display for the user.<br>
<br>
Flags	Flags for this action record.</ul>
<br>
For more details on processing NotesFlow actions, see the section, &quot;The NotesDocAction Message.&quot;<br>
<br>
<br>
<b><font size="5" color="#000080">The NoteshNote Message</font></b><br>
<br>
The message &quot;NoteshNote&quot; is sent from the OLE server to Domino or Notes to update or delete fields while the OLE server is still active.  (Changes made using the hFXNote handle supplied in the NotesDocInfo message will only be applied after the OLE object is closed.)  The message name, NoteshNote, must be stored in the RequestDataFormats key in the system registry.  The clipboard format passed to the GetData method will be the value obtained by calling RegisterClipFormat() with NoteshNote as the label.  This message has one field:<br>

<ul>hNote	Handle to a copy of the note with new, updated, or deleted items</ul>
<br>
For each NoteshNote message, the OLE server must create a copy of the active document by calling NSFNoteCopy(), copy the fields to be updated or deleted to this new note, and send that new note handle in the NOTES_HNOTE_MSG structure.  The recommended approach is to create a copy of the original hNote by calling NSFNoteCopy() while processing the NotesDocInfo message, then to create a new copy from that handle for each NoteshNote message.  In OLE 1, the server should send an OLE_UPDATE to Domino or Notes.  Domino or Notes will call the GetData method with the NoteshNote clipboard format.  The server should allocate a block of memory to hold the NOTES_HNOTE_MSG structure, fill in the handle, and return it.  In OLE 2, the application can also send an OnDataChange to the Domino or Notes advise sink and supply the corresponding action code in a NOTES_HNOTE message.  In either case, the copy of the note created for this message is turned over to Domino or Notes;  the server should not perform any further processing using that note handle.<br>
<br>
Note that there are two steps involved in sending the message through OLE.  The server must send the OLE_UPDATE (OLE 1) or OnDataChange (OLE 2) notification and then supply the NoteshNote message in response to a GetData call.  The server must remember the update while waiting for the GetData call.  For example, the NOTESFLO sample program stores this information in fields in the CNotesFlowManager class.<br>
<br>
<br>
<b><font size="5" color="#000080">The NotesDocAction Message</font></b><br>
<br>
The &quot;NotesDocAction&quot; message is used to tell Domino or Notes when the user selects a NotesFlow action from the OLE server.  The message name, NotesDocAction, must be stored in the RequestDataFormats key in the system registry.  The clipboard format passed to the GetData method will be the value obtained by calling RegisterClipFormat() with NotesDocAction as the label.  The fields of this message are:<br>

<ul>ActionID - The ID supplied for the action in the NotesDocInfo message.<br>
Flags - No flags are currently supported for actions.</ul>
<br>
The actions provided in the NotesDocInfo message should be incorporated into the user interface of the server.  For example, the action names could be displayed in a pull-down or pop-up menu, on buttons, or in any other way consistent with the design of the server.  When the user selects an action, an OLE 1 server should send an OLE_UPDATE to Domino/Notes.  Domino/Notes will call the GetData method with the NotesDocAction clipboard format.  The server should allocate a block of memory to hold the NOTES_EXECUTE_DOCACTION_MSG structure, fill in the message, and return it.  In OLE 2, the application can also send an OnDataChange to the Domino/Notes advise sink and supply the corresponding action code in a NOTES_DOC_ACTION message.<br>
<br>
Again note that there are two steps involved in sending the message through OLE.  The server must send the OLE_UPDATE (OLE 1) or OnDataChange (OLE 2) notification and then supply the action message in response to a GetData call.  The server must remember the action being requested while waiting for the GetData call.  For example, the NOTESFLO sample program stores this information in fields in the CNotesFlowManager class.<br>
<br>
Actions must be published for use by OLE servers in order to be included in the action list.  This is an option in the properties for an action.  For example, open the sample database \notesapi\notedata\notesflo.nsf and open the form &quot;NotesFlow Container&quot;.  From the menu, select &quot;View/Action Pane&quot;.  Again from the menu, select &quot;Design/Action Properties&quot; to display the action properties box.  Select the &quot;NotesFlow Publishing&quot; tab.  If the box &quot;Publish action with OLE object&quot; is checked, the action is made available to OLE objects.  <br>
<br>
<br>
<b><font size="5" color="#000080">The NotesDocActionDone Message</font></b><br>
<br>
When a NotesFlow action has been sent to Domino or Notes and the OLE server has registered support for the NotesDocActionDone message, Domino or Notes will send that message to the OLE server when the action has been completed.  The message type NotesDocActionDone must be stored in the SetDataFormats key in the system registry, and (for OLE 1) must be returned from the EnumFormats() request.  The clipboard format passed to the SetData method will be the value obtained by calling RegisterClipFormat() and passing NotesDocActionDone as the label.  The fields in this message are:<br>

<ul>ActionID	ID of the action that has been completed.<br>
<br>
ExecuteStatus	If the action completed successfully, this is set to 0.  If the action failed, this field is set to a non-zero internal error code.</ul>

---
