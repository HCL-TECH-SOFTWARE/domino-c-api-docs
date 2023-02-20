##### Chapter 12-9
##### Signal Handlers

<b><font size="5" color="#000080">Introduction</font></b><br>
<br>
C API applications can call the signal handlers that Domino and Notes use to report events to the user. They can also create signal handlers to perform customized processing when a signal occurs or to disable normal signal handling while performing specialized tasks.  Please be aware that Notes C API programs should not install operating system signal functions (for example: signal(), sigset(), etc), because it is not supported.<br>
<br>
Signal handlers are different from normal API functions. There are no function names that you can code in an application. Instead, Domino or Notes stores pointers to signal handler functions in an internal table. To obtain the current address of a signal handler, call the API function OSGetSignalHandler. To set a new signal handler, call the API function OSSetSignalHandler.<br>
<br>
There is a separate internal signal handler table for each process. A custom signal handler only &quot;catches&quot; signals from operations performed in the current process;  it does not handle signals from other processes. Furthermore, a call to a signal handler from a process is only handled by the &quot;default&quot; signal handlers for that process; if another process sets a custom signal handler, calls from the first process are not affected.<br>
<br>
The result of calling the default signal handlers depends on whether the application is running in the Notes client or Domino server environment. If the application runs in the context of the Notes client workstation process, the signal behavior (such as OS_SIGNAL_MESSAGE) is GUI-based. If the application runs in the context of a server add-in process, the signal behavior is character-based. For example, OS_SIGNAL_MESSAGE will only log a message to log.nsf and the console; no GUI message box is put up.<br>
<br>
<br>
<b><font size="5" color="#000080">Signals</font></b><br>
<br>
The C API supports the following signals:<br>
<br>
OS_SIGNAL_MESSAGE	Display a message to the user<br>
OS_SIGNAL_BUSY		Paint a busy indicator on the screen<br>
OS_SIGNAL_CHECK_BREAK	Check for user cancellation of I/O<br>
OS_SIGNAL_DIAL		Prompt to dial a remote system<br>
OS_SIGNAL_PROGRESS	Display the progress bar<br>
OS_SIGNAL_REPL		Signal the replication state<br>
<br>
<br>
Each of these signals and the corresponding signal handler is described in detail below.<br>
<br>
<br>
<b><font size="5" color="#000080">Calling a Signal Handler</font></b><br>
<br>
The C API allows applications to obtain the addresses of the signal handlers that are built into Domino and Notes and to call these signal handlers in the same way that Domino and Notes call them. This can be useful, for example, when building applications that need to display messages to the user;  you can use the signal handler for OS_SIGNAL_MESSAGE to display a dialog box and get a response from the user. As another example, you can use the OS_SIGNAL_BUSY message handler to display a busy indication on the user's screen.<br>
<br>
To call a signal handler, follow these steps:<br>

<ol type="1">
<li>Call OSGetSignalHandler to obtain the address of the signal handler, passing as the argument the appropriate signal ID. If no signal handler is present, this function returns NULL.
<li>Call the signal handler using the address and the appropriate argument list. The return value depends on the specific signal handler;  for details, refer to the description of the signal handler.</ol>

<ul></ul>
For example, the following code fragment illustrates a call to the message signal handler:<br>

<ul><tt>#include &lt;ossignal.h&gt;</tt><br>
<br>
<tt>OSSIGMSGPROC	MessageProc;</tt><br>
<tt>WORD				result;</tt><br>
<br>
<tt>MessageProc = (OSSIGMSGPROC) OSGetSignalHandler (OS_SIGNAL_MESSAGE);</tt><br>
<tt>if (NULL != MessageProc)</tt><br>
<tt>	result = (*MessageProc) (&quot;Press 'OK' to continue&quot;,</tt><br>
<tt>		OSMESSAGETYPE_OK);</tt></ul>
<br>
<br>
<b><font size="5" color="#000080">Supplying a Custom Signal Handler</font></b><br>
<br>
You can also supply a custom signal handler, either to provide special processing for a signal or to disable the normal handling of a signal. Use OSSetSignalHandler to set a signal handler for the current process, providing the signal ID and the address of the new signal handler. OSSetSignalHandler returns the address of the current signal handler for the process;  to ensure that normal processing of signals will resume, applications should restore this signal handler address when finished.<br>
<br>
To disable normal handling of system events, set the signal handler address to NULL, as the following code fragment illustrates:<br>

<ul>
<ul><tt>#include &lt;ossignal.h&gt;</tt><br>
<br>
<tt>OSSIGBUSYPROC	OldBusyProcPtr;</tt><br>
<br>
<tt>OldBusyProcPtr = OSSetSignalHandler (OS_SIGNAL_BUSY, (OSSIGPROC) NULL);</tt><br>
<br>
<tt>	/* Code to execute with no busy indication */</tt><br>
<br>
<tt>OSSetSignalHandler (OS_SIGNAL_BUSY, OldBusyProcPtr);</tt></ul>
</ul>
<br>
Setting a custom signal handler for the <tt>OS_SIGNAL_MESSAGE</tt> is not supported in the C API.  You may call the built-in signal handler for <tt>OS_SIGNAL_MESSAGE</tt> to display messages at the Notes UI.<br>
<br>
<b><font size="5" color="#000080">Built-In Signal Handlers</font></b><br>
<br>
The following sub-sections describe the signal handlers that are built into Domino and Notes.<br>
<br>
<b><font size="4" color="#000080">The Message Signal Handler</font></b><br>
<br>
Notes workstation clients use the message signal handler to display message boxes to the user via a graphical user interface. The built-in signal handler can post a message to the status line on the display or display a message in a dialog box with buttons; the type of display is controlled by the Type parameter passed to the signal handler.<br>
<br>
This signal handler requires two parameters:
<ul>
<li type="disc">Message - Far pointer to message text to be displayed
<li type="disc">Type - How the message is to be displayed. The values allowed for this parameter are:<br>

<ul>OSMESSAGETYPE_OK
<ul>Display the message in a dialog box with an OK button.</ul>
<br>
OSMESSAGETYPE_OKCANCEL
<ul>Display the message in a dialog box with OK and CANCEL buttons.</ul>
<br>
OSMESSAGETYPE_YESNO
<ul>Display the message in a dialog box with YES and NO buttons.</ul>
<br>
OSMESSAGETYPE_YESNOCANCEL
<ul>Display the message in a dialog box with YES, NO, and CANCEL buttons.</ul>
<br>
OSMESSAGETYPE_RETRYCANCEL
<ul>Display the message in a dialog box with RETRY and CANCEL buttons.</ul>
<br>
OSMESSAGETYPE_POST
<ul>Display the message on the status line.</ul>
</ul>
</ul>
This signal handler returns a status code that identifies the user's action. The return codes are:<br>

<ul>ERR_OSMESSAGE_OK		User selected OK<br>
ERR_OSMESSAGE_CANCEL	User selected CANCEL<br>
ERR_OSMESSAGE_RETRY	User selected RETRY<br>
ERR_OSMESSAGE_YES		User selected YES<br>
ERR_OSMESSAGE_NO		User selected NO</ul>
<br>
If the dialog box cannot be loaded, the error code ERR_OSMESSAGE_CANNOT_PROMPT is returned. A call to the message signal handler with the parameter OSMESSAGETYPE_POST always returns ERR_OSMESSAGE_OK. Applications can obtain the address of the message signal handler by calling OSGetSignalHandler (OS_SIGNAL_MESSAGE).<br>
<br>
In the Domino server environment, only OSMESSAGETYPE_POST is enabled. A call to the mMessage signal handler with this type code records an entry in log.nsf containing the message text if logging is enabled; otherwise, it displays the message on the server console. Using any other type code results in an error message.<br>
<br>
<br>
<b><font size="4" color="#000080">The Busy Signal Handler</font></b><br>
<br>
The low-level I/O code in the Notes core DLLs uses the busy signal handler to indicate when I/O operations are taking place. The Notes client workstation code provides a signal handler that displays the &quot;lightning bolt,&quot; indicating network activity, when BUSY_SIGNAL_NET_ACTIVE is signaled and erases it when BUSY_SIGNAL_NET_INACTIVE is signaled.  Applications can provide a custom signal handler to take action when Notes starts or completes an operation.<br>
<br>
Five different events are signaled, identified by the BusyType parameter to the signal handler:<br>

<ul>BUSY_SIGNAL_FILE_ACTIVE	Starting local disk I/O operation<br>
BUSY_SIGNAL_FILE_INACTIVE	Local disk I/O completed<br>
BUSY_SIGNAL_NET_ACTIVE	Starting network I/O operation<br>
BUSY_SIGNAL_NET_INACTIVE	Network I/O completed<br>
BUSY_SIGNAL_POLL		Checking to see if network I/O has completed</ul>
<br>
To obtain the address of the busy signal handler, call OSGetSignalHandler (OS_SIGNAL_BUSY). To install a custom signal handler, call OSSetSignalHandler().<br>
<br>
The default signal handler in the Notes client workstation reacts only to BUSY_SIGNAL_NET_ACTIVE and BUSY_SIGNAL_NET_INACTIVE to control display of the network activity indicator. The other actions are ignored to speed up the operation of Notes. The low-level I/O code in the Notes core DLLs invokes this signal handler frequently. BUSY_SIGNAL_FILE_ACTIVE and BUSY_SIGNAL_FILE_INACTIVE are called before and after each disk I/O operation. BUSY_SIGNAL_NET_ACTIVE and BUSY_SIGNAL_NET_INACTIVE are called before and after each network I/O operation, and BUSY_SIGNAL_NET_POLL is called each time Notes checks to see if a network operation has completed. These events can happen many times per second (particularly BUSY_SIGNAL_NET_POLL), so be careful when writing a custom signal handler to avoid slowing the operation of Notes.<br>
<br>
In the server environment, since there is no GUI interface, the busy signal handler has no effect and always returns NOERROR.<br>
<br>
<b><font size="4" color="#000080">The Check Break Signal Handler</font></b><br>
<br>
The check break signal handler is called when the Notes client workstation and the Domino server test to see if a &quot;break&quot; event has occurred. There are different signal handlers for the Notes client and the Domino server, so the behavior is different in each environment.  For Notes clients, the check break signal handler returns ERR_CANCEL if the user has pressed the key combination to generate the break signal; otherwise, it returns NOERROR.  For Domino servers, the check break signal handler returns ERR_QUIT if the task (or server) has been commanded to quit; otherwise, it returns NOERROR.  Applications can obtain the address of the check break signal handler by calling OSGetSignalHandler (OS_SIGNAL_CHECK_BREAK). This signal handler requires no parameters.<br>
<br>
<b><font size="4" color="#000080">The Dial Signal Handler</font></b><br>
<br>
In the Notes client workstation environment, the dial signal handler displays a dialog box where  the user can specify options for dialing a server. This signal handler is called before initiating an external dial. It returns ERR_NET_CONTINUE if the number is to be dialed; any other return value is an error code to be reported to the application. This signal handler requires five parameters:<br>

<ul type="disc">
<li>pServer - Far pointer to a null-terminated string containing the name of the server to dial
<li>pPort - Far pointer to a null-terminated string containing the name of the port to use
<li>pDialParams - Reserved for future use; should be set to NULL
<li>pRetServer - Pointer to a buffer to hold the actual name of the server to call
<li>pRetPort - Pointer to a buffer to hold the actual name of the port to use</ul>
<br>
Applications can obtain the address of the dial signal handler by calling OSGetSignalHandler (OS_SIGNAL_DIAL).<br>
<br>
In the Domino server environment, the dial signal handler has no effect and always returns ERR_NET_CONTINUE.<br>
<br>
<b><font size="4" color="#000080">The Progress Signal Handler</font></b><br>
<br>
The Progress signal handler displays a progress bar. This signal handler requires three parameters:<br>

<ul type="disc">
<li>Option - Specify one of the following options:<br>
	<font face="Courier">PROGRESS_SIGNAL_BEGIN<br>
	PROGRESS_SIGNAL_END<br>
	PROGRESS_SIGNAL_SETRANGE<br>
	PROGRESS_SIGNAL_SETTEXT<br>
	PROGRESS_SIGNAL_SETPOS<br>
	PROGRESS_SIGNAL_DELTAPOS</font>
<li>data1 - Depending on the value of the Option, this parameter supplies the header text, the range, or the position of the progress bar.
<li>data2 - Reserved for future use; should be set to NULL</ul>
<br>
<b><font size="4" color="#000080">The Repl Signal Handler</font></b><br>
<br>
The Repl signal handler signals the state of the replication. This signal handler requires three parameters:<br>

<ul type="disc">
<li>State - Specify one of the following states:<br>
	<font face="Courier">REPL_SIGNAL_IDLE<br>
	REPL_SIGNAL_PICKSERVER<br>
	REPL_SIGNAL_CONNECTING<br>
	REPL_SIGNAL_SEARCHING<br>
	REPL_SIGNAL_SENDING<br>
	REPL_SIGNAL_RECEIVING<br>
	REPL_SIGNAL_SEARCHINGDOCS<br>
	REPL_SIGNAL_DONEFILE</font>
<li>pText1 - Pointer to a null terminated string identifying the server.
<li>pText2 - Pointer to a null terminated string identifying the server.</ul>

---
