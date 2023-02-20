##### Chapter 12-11
##### Extension Manager

The Extension Manager allows an executable program library in an application to register a callback routine that will be called before, after, or before <i>and</i> after Domino or Notes performs selected internal operations. This allows C API applications to perform database shadowing or add additional access controls. The header file extmgr.h defines names that identify the notification events that are supported.<br>
<br>
Extension manager applications are built as executable program libraries (for example, dynamic link libraries for Windows or shared object libraries for UNIX environments). The structure and naming conventions for program libraries are platform-dependent; for more information, see the &quot;Platform-Specific Naming Conventions&quot; chapter.<br>
<br>
You must identify the executable program library for an extension in the notes.ini file by adding an EXTMGR_ADDINS entry. There should only be one such entry in notes.ini;  list all extension manager libraries in the same entry, separated by commas. For example, to run both sample programs extmngr and extpwd on a Win32 system, the entry in notes.ini should be:<br>

<ul><tt>EXTMGR_ADDINS=nextmngr.dll,nextpwd.dll</tt><br>
</ul>
If there are multiple extension managers that process the same notification,  each extension manager is notified of that event in the order listed in the EXTMGR_ADDINS entry of notes.ini .
<ul></ul>
An extension manager may be installed on either a Notes client workstation or a Domino server.  However, there is not necessarily a one-to-one correspondence between the C API calls made on a client workstation and extension manager notifications on a Domino server.  The extension manager on the server may not receive the expected notifications.  For example, when a client workstation performs an NSFNoteUpdate on a remote database, different requests are sent to the Domino server depending on the state of the document and the nature of the update.  In particular, the function NSFNoteUpdate may not be called on the server, therefore the notification EM_NSFNOTEUPDATE will not occur.<br>
<br>
<br>
<b><font size="4" color="#000080">Registering a Callback Function</font></b><br>
<br>
The first step in registering a callback function to receive notification events is to call EMCreateRecursionID to obtain a recursion ID. Although this step is optional, it is usually desirable because it prevents Domino or Notes from calling that extension if the current thread has already called the extension once.  For example, this prevents an endless cycle if your application is expecting notification on NSFDbOpen and calls NSFDbOpen when processing that notification.<br>
<br>
You only need one recursion ID per extension manager DLL or shared object. The same recursion ID applies to all threads in a process. You can set it individually on each extension you register to allow recursion on some extensions but not others. You can use the same ID across multiple extensions. You do not have to remember the recursion ID<b>,</b> because all the checking is done in Domino or Notes and it is freed on shutdown. <br>
<br>
Once the application obtains a recursion ID, call EMRegister with the ID of the desired notification, flags indicating when to call the function, the address of the callback function, and the recursion ID. The flag values may be:<br>

<ul>EM_REG_BEFORE - The routine will be called before the operation is attempted<br>
EM_REG_AFTER - The routine will be called after the operation is completed<br>
Both - The routine will be called before the operation is attempted and again after the operation is completed</ul>
<br>
Do not make any C API function calls for Domino and Notes, other than the extension manager EMxxx function calls, in the entry point routine that calls EMRegister. The extension manager DLL or shared object is loaded as part of Domino or Notes initialization and the extension manager entry point routine is called as part of that startup. The initialization of the other components of Domino or Notes is not yet completed when the extension manager entry point routine is called.<br>
<br>
When an application is finished with the Extension Manager, use EMDeregister to remove all the callback functions registered. Failure to de-register a callback function may result in a crash of Domino or Notes.  Do not de-register callback functions in the callback routine for the EM_TERMINATENSF notification.<br>
<br>
Extensions are registered on a per-process basis. Once an extension is registered, all threads in a process invoke that extension. If a recursion ID is used, it applies to all threads in that process.<br>
<br>
<br>
<b><font size="4" color="#000080">The Callback Function</font></b><br>
<br>
The callback function has the following declaration:<br>

<ul><tt>STATUS LNCALLBACK ExtMgrCallback (EMRECORD far *pExtRec);</tt></ul>
<br>
The single argument supplied by Domino or Notes is a pointer to an EMRECORD structure. The fields of this structure are:<br>

<ul>EId			Notification ID<br>
NotificationType	EM_BEFORE or EM_AFTER<br>
Status		Core error code<br>
Ap			Pointer to the arguments supplied to the Domino or Notes core function</ul>
<br>
The EId is the value supplied when the function was registered (or one of the values, if the same function was registered for more than one notification). The NotificationType informs the function whether this notification is before the operation is attempted or after it was completed. If the NotificationType is EM_BEFORE, the Status field is undefined;  if EM_AFTER, this field contains the return value from the operation. Ap points to the arguments supplied to the core function;  since this varies from one function to another, you must use the notification ID to determine the corresponding function for the notification so that the arguments can be correctly interpreted using the VARARG_xxx macros in global.h.<br>
<br>
<b>An important note:</b>  If the Notification Type is EM_BEFORE (before the operation has been performed), input parameters to the function will be valid.  For example if one of the input parameters is a note handle, the value will be active and valid when interpreted using the VARARG_xxx.  However if the Notification Type is EM_AFTER (after the operation has been performed) input parameters, such as note handles, will no longer be valid due to internal Notes processing freeing or deallocating handles once the operation has been completed.  Keep this in mind when processing EMxxx function calls. <br>
<br>
A note can be opened in &quot;canonical&quot; format.  When this occurs, the data type fields and data values that are normally converted to host format are left unconverted.  Extension manager callback functions that examine the data in a note must check for the flag NOTE_FLAG_CANONICAL by calling NSFNoteGetInfo() with the header member _NOTE_FLAGS before attempting to interpret the contents of the note.<br>
<br>
NOTE:  The Extension Manager notification EM_AGENTISENABLED has a slighly different callout signature due to the function returning something other than STATUS.  The signature is as follows:  STATUS LNPUBLIC AgentIsEnabled(HAGENT hAgent, BOOL *return_value)<br>
To retrieve the Core error code of this function check the *return_value parameter instead of the Status variable of the EMRECORD structure.<br>
<br>
<b><font size="4" color="#000080">Callback Return Codes</font></b><br>
<br>
The return code from the callback function controls the processing that Domino or Notes performs following the return. It is helpful to know the steps Domino or Notes uses for an internal operation that supports notifications:
<ul></ul>

<ol type="1">
<li>Domino or Notes calls any functions registered with EM_REG_BEFORE. If any function returns a value other than ERR_EM_CONTINUE, Domino or Notes does not call any subsequent functions and does not perform the operation.
<li>Domino or Notes performs the operation.
<li>Domino or Notes calls any functions registered with EM_REG_AFTER. If any function returns a value other than ERR_EM_CONTINUE, Domino or Notes does not call any subsequent functions and returns that value as the result of the operation (either internally or to the API application that invoked the operation).</ol>
<br>
In most instances, callback functions registered with EM_REG_BEFORE should return ERR_EM_CONTINUE, to ensure that Domino or Notes performs the requested operation.  Exceptions are noted in this chapter and in the <i>Reference</i>, under the specific callback function entry.<br>
<br>
<b><font size="4" color="#000080">Writing an Extension Manager that transforms a Non-Domino Database into a Domino Database.</font></b><br>
<br>
In the Extension Manager Sample \misc\extmngr a non-Domino database is transformed into a Domino database when the EM_NSFCREATEDB and EM_NSFCLOSEDB notifications are trapped for the sample database &quot;animals.nsf&quot;.  This sample demonstrates the use of an Extension Manager to perform complex Database operations upon trapping specific notifications.<br>
<br>
When the user creates a new database with the title &quot;animals&quot;, the Extension Manager traps the EM_NSFCREATEDB and also the EM_NSFCLOSEDB notifications.  Before the database is closed and the EM_NSFCLOSEDB notification has been trapped, the program creates the forms,  views, and documents needed for the Domino database &quot;animals.nsf&quot; to reflect the data contained in the non-Domino database &quot;animals.db&quot;.<br>
<br>
Other Database operations can be handled by the Extension Manager by trapping the specific notification before or after and before and after completion.  See the header file &quot;extmgr.h&quot; for a list of the supported Extension Manager Notifications.<br>
 <br>
<b><font size="4" color="#000080">Capturing the Domino or Notes Password Prompt Request</font></b><br>
<br>
One of the operations you can trap using the Extension Manager is the Domino or Notes password prompt request. The extension ID code is EM_GETPASSWORD. There is no corresponding API function for this operation. The header file extmgr.h documents the arguments to the get password operation.<br>
<br>
The sample program misc\extpwd uses the extension manager to capture the password prompt request. For simplicity, the program displays a dialog box to obtain the password. However, this is not necessary; all Domino or Notes requires is that the characters for the password be written to the address provided in the request.<br>
<br>
An extension manager hook for the EM_GETPASSWORD request is only called before the operation is attempted. Registering a callback function with the EM_REG_AFTER flag has no effect.<br>
<br>
The EM_GETPASSWORD request  uses the following special status codes to indicate the status of the operation to Domino or Notes:<br>

<ul>
<ul type="disc">
<li>ERR_BSAFE_EXTERNAL_PASSWORD<br>
The password has been supplied by an external source. (An extension manager hook is considered an external source.) This status code must be returned to Domino or Notes by an extension manager hook that provides a password.</ul>

<ul type="disc">
<li>ERR_BSAFE_USER_ABORT<br>
The password request was canceled. This corresponds to the user clicking Cancel in the Notes password dialog box.</ul>

<ul type="disc">
<li>ERR_EM_CONTINUE<br>
Domino or Notes performs the usual processing (that is, displaying the password dialog prompt).</ul>
</ul>
Since this extension manager hook works with user passwords, there are security issues to consider. First, it is not practical to attempt to guess a user's password through an API program. Domino or Notes supplies a built-in delay between attempts to provide the password, and the delay increases if the correct password is not provided. The estimated average time to guess a password using the extension manager is 99,260 years.<br>
<br>
A more plausible attack is to provide an extension that prompts the user for the password, then both supplies the password to Domino or Notes and stores the password in an unsecured location. Users should be aware that a user interface other than the Domino or Notes password dialog prompt may not be secure; system administrators and application developers must implement processes to ensure that user passwords are not compromised in this way.<br>
<br>
Another risk comes from applications that store the password for legitimate purposes. For example, if the password is stored in a disk file, an unscrupulous individual who was aware of that fact could obtain the password from the file. If at all possible, applications should not store passwords anywhere an unauthorized person could obtain them.<br>
<br>
<br>
<b><font size="4" color="#000080">Capturing the Domino or Notes Replication Conflict Notification</font></b><br>
<br>
By trapping the replication conflict notification, you can have an extension manager automatically handle replication conflicts.  The extension ID code is EM_NSFCONFLICTHANDLER. There is no corresponding API function for this operation. The header file extmgr.h documents the arguments to the replication conflict handler.<br>
<br>
The Notes C API Release 4.5 introduced several new functions that can be used by the extension manager to determine how to handle a replication conflict.  These functions include:<br>

<ul>
<ul>NSFNoteFindMatchingItem	Find item in one note that matches the same item in another.<br>
NSFNoteFindDivergenceTime	Find when two notes were last in synch.<br>
NSFItemGetModifiedTime	Get the last modified time for an item.<br>
NSFItemGetModifiedTimeByBLOCKID	Get the last modified time for an item, given the item's BLOCKID.<br>
</ul>
</ul>
Use the extension manager callback routine to handle the replication conflict.  In this handler routine, you can use NSFNoteFindMatchingItems to pair items from one note that match items from another.  An item pair may be in conflict if one of the item's modified time is later than the note's divergence time.  You can then specify the desired value for the item by setting this item value in the item of one note and deleting this item from the other.  Then, pass CONFLICT_ACTION_MERGE back so that the two matching notes are merged with your specified resolution to the conflict.<br>
<br>
If you want Domino or Notes to handle the replication conflict, pass back ERR_EM_CONTINUE.  For example, if an error occurs in your replication conflict handler you may want to abort handling the conflict yourself and pass ERR_EM_CONTINUE back to Domino or Notes.<br>
<br>
The replication conflict handler needs to be installed on each Domino or Notes installation that can be involved in the replication and subsequent conflict resolution.  Domino or Notes calls the extension manager replication conflict handler (if any) on the installation that lost the replication conflict.<br>
<br>
The sample program misc\extconf demonstrates an extension manager that handles a replication conflict.<br>
<br>
<b><font size="4" color="#000080">Writing an Extension Manager to Process Outgoing Mail</font></b><br>
<br>
The extension manager notification, EM_MAILSENDNOTE, can be used to process outgoing mail.  The sample program,  \mail\extmail, demonstrates how to intercept certain outgoing mail messages.  If the notification type is EM_BEFORE, and the mail message's subject text is &quot;Extension Manager&quot;,  the Extension Manager modifies the mail message's body text notifying the user that the mail has been intercepted.  If the notification type is EM_AFTER, the Extension Manager creates a new mail message with user mail information, attaches an Extension Manager log file and sends the message to the originator of the outgoing mail message.<br>
<br>
<br>
<b><font size="4" color="#000080">Extension Manager Limitations</font></b><br>

<ul type="disc">
<li>Do not make any C API function calls for Domino and Notes, other than the extension manager EMxxx function calls, in the entry point routine that calls EMRegister.  The initialization of the other components of Domino or Notes is not yet completed at this point.</ul>

<ul type="disc">
<li>All Domino and Notes applications activate the extension managers specified in the notes.ini file.  In the entry point of your extension manager, you can register your extension manager for the Notes client only by checking the name of the calling application before you call EMRegister.  For example, with a Windows 32-bit application, if the name of the calling application is not nnotes.dll, then do not call EMRegister.</ul>

<ul type="disc">
<li>Do not de-register callback functions in the callback routine for the EM_TERMINATENSF notification.</ul>

<ul type="disc">
<li>Do not call C API functions (such as NSFItemScan) that require callback functions in your extensions manager.</ul>

<ul type="disc">
<li>Be wary of processing messages in a mail.box file.  If you intercept the EM_NSFNOTEOPEN notification to make changes to the document that affects the routing of the message (for example, change the send to field to redirect a message), you may not get the desired results.  At this point the Router may already contain state information about the message and may deliver the message to the original recipient.</ul>

<ul type="disc">
<li>There has been a reported anomaly that when trapping EM_NSFNOTECLOSE, and then using the associated object handle, Notes returned a &quot;handle out of range&quot; error.  This is a rare condition and due to Notes internally discarding the object before actually freeing it.  To guard against this error occurring, it has been suggested that you test the validity of the handle by calling OSLockObject().  If the call returns NULLHANDLE do not use the handle in any further processing.<br>

<li>Beginning with R5.0, the output of printf in the Extension Manager routines are buffered.  To see the output, you can use the <b>fflush </b>function to flush the buffer, or, use the <b>AddInLogErrorText </b>function instead.</ul>

<ul type="disc">
<li>Be aware that Extension Manager callback routines may be called when the corresponding database's semaphore is locked.  In this case, you must not call a C API routine that needs to acquire the database semaphore, or a deadlock will occur.  For example, you must not call NSFDbGetUnreadNoteTable in the routine that traps EM_NSFMARKREAD.  Similarly, you must not call NSFFolderGetIDTable in the routine that traps EM_NSFADDTOFOLDER  with the same Folder ID.</ul>

---
