##### Chapter 4-4
##### Server Add-In Tasks

This chapter describes custom tasks (server add-ins) that you can create for the HCL Domino Server.  A server add-in is an executable program that runs alongside the other tasks that make up the HCL Domino Server software and performs whatever C API operations you want.<br>
<br>
Since server add-in tasks are loaded by Domino, the names of the executable files must follow the conventions described in the &quot;Platform Specifics&quot; chapter for your platform.<br>
<br>
This chapter presents an overview of server add-ins, explains how to start and run them, and discusses some of the C API functions that are specific to server add-ins. <br>
<br>
For complete coding details, see the sample programs ADDIN and ADD_RES in the <i>server</i> subdirectory.<br>
<br>
<br>
<b><font size="5" color="#000080">Uses for Add-In Tasks</font></b><br>
<br>
It is possible to write an add-in that starts, performs one operation, and exits. However, the main use for add-ins is to perform some operation periodically. <br>
<br>
For instance, suppose you want to read a non-Domino database every hour and update a Domino database when the former changes. You can do this with an add-in task as follows:<br>

<ol type="1">
<li>Write an add-in task that contains all the C API code needed to read the non-Domino database and update the Domino database.
<li>In the add-in, use the control code that causes the task to execute once per hour.
<li>Do not load the add-in task under ServerTasks or manually via the Server Console.
<li>Start server (without the server add-in).
<li>Run debugger for the server add-in as you would a NotesMain program.</ol>
<br>
The add-in runs until the server is shut down. Every hour, the add-in task scans the non-Domino database and checks for updates to it. When the non-Domino database changes, the add-in task writes the changes to the Domino database. <br>
<br>
To use a different time interval between executions of the task, modify the timing control code to specify any schedule, such as once each night at 2:00 AM or once every 5 seconds. You can also write add-ins to execute more than one job, each with its own schedule.<br>
<br>
<br>
<b><font size="5" color="#000080">Starting an Add-In Task</font></b><br>
<br>
You can start add-in tasks two ways: automatically when the server software is started or manually, by a user at the server console. The first method is easier for production tasks, while the second method is most convenient for testing an add-in.<br>
<br>
The instructions below ask you to stop the HCL Notes client software while you run the HCL Domino Server software if the client is on the same machine as the server. This is not strictly required. The reason we ask you to stop the Notes client software while you run the Domino server software is for ease of reading the Domino server log file. If the Notes client software and the Domino server software are running at the same time, the last entry to the log file might not be written promptly. This can make it difficult to check the results of your add-in task.<br>
<br>
<br>
<b><font size="4" color="#000080">Starting an Add-In Automatically</font></b><br>
<br>
To start an add-in automatically, follow these steps:<br>

<ol type="1">
<li>Make sure the HCL Domino Server software is installed on the current machine and the Domino data directory contains a log file (log.nsf). You can use your existing log file or create a new one from the Log template.
<li>Copy the executable file for the add-in task to the Domino software directory. 
<li>Make a backup copy of notes.ini, then open notes.ini for editing and search for the line that begins &quot;ServerTasks=&quot;. This is a comma-delimited list of server tasks that start automatically each time the server starts.
<li>Add the name of the add-in task to this list, omitting the leading platform specifier character and the file extension. &quot;(Platform specifier characters for your platform are described in the &quot;Platform Specifics&quot; chapter.)&quot;. UNIX add-ins do not contain leading platform specifier characters. 
<li>Save and close notes.ini.
<li>If the Notes workstation software is running on the same machine, exit from it.
<li>Start the HCL Domino Server software.
<li>(Optional) To confirm that the add-in task is running, type &quot;SHOW TASKS&quot; at the server console. This displays a list of all server tasks that are running and the status of each task.
<ul><br>
</ul>
</ol>
<b><font size="4" color="#000080">Starting an Add-In Manually</font></b><br>
<br>
To start an add-in task manually from the server console, follow these steps:<br>

<ol type="1">
<li>Make sure your Domino data directory contains a  log file (log.nsf). You can use your existing log file or create a new one from the Log template.
<li>If the Notes workstation software is running on the same machine, exit from it. 
<li>Start the HCL Domino Server software. Wait until all server tasks have started - about 30 seconds.
<li>Press ENTER to get the server console prompt, &gt;.
<li>Load the add-in task by typing<font color="#FF0000"><br>
<br>
</font>load &lt;taskname&gt;<font color="#FF0000"><br>
<br>
</font>If the add-in executable is not in a directory in the search path, be sure to specify the full path name of the add-in task. You may omit the leading platform specifier character. (Platform specifier characters for your platform are described in the &quot;Platform Specifics&quot; chapter.)&quot;. UNIX add-ins do not contain leading platform specifier characters. 
<li>(Optional) To confirm that the add-in task is running, type &quot;show tasks&quot; at the server console.</ol>
<br>
<br>
<b><font size="5" color="#000080">Stopping an Add-In</font></b><br>
<br>
To stop an add-in task, type &quot;tell &lt;taskname&gt;quit&quot; at the HCL Domino Server console.
<ul>
<ul><br>
</ul>
</ul>
<b><font size="5" color="#000080">Checking the Operation of an Add-In</font></b><br>

<ol type="1">
<li>Watch the server console for several minutes. You should see messages from the add-in task as it executes various parts of its code.
<li>Occasionally, type &quot;show tasks&quot; at the server console to display a list of all the server tasks, including the add-in, and the current status of each add-in. At different times you should see that the status of the add-in task has changed.
<li>Type &quot;quit&quot; to stop the server software. Wait for all the server tasks to stop. You should see a termination message from the add-in task.
<li>Start the Notes workstation software.
<li>If you have not already done so, add the server's log (log.nsf) database to your workspace. The database is found in the Domino data directory.
<li>Open the server log database.
<li>Choose the view Miscellaneous Events. The last entry in this view should show the start and stop times of the server session that you just ran.
<li>Open the last log entry. You should see all the messages that were displayed on the server console.
<li>Exit from this database.</ol>
<br>
<br>
<b><font size="5" color="#000080">Server Add-In Function Calls</font></b><br>
<br>
The following C API functions are specific to custom server tasks. Refer to the <i>Reference</i> for details. These functions only work properly in the context of a server add-in and may not work correctly outside that context.<br>
<br>
<br>
<b><font size="4" color="#000080">AddInMain</font></b><br>
<br>
AddInMain is the standard entry point for HCL Domino Server add-in tasks. AddInMain functions as a &quot;wrapper,&quot; in that the server initializes the Domino run-time system and certain per-task data before calling AddInMain. It also creates a default status line for the add-in task. After AddInMain returns, the HCL Domino Server performs shutdown tasks and frees the per-task data. This means the add-in code itself needs no Domino initialization or termination code.<br>
<br>
Use the function AddInCreateStatusLine to create the status line. Alternatively, if you need to call functions that require a default status line, such as AddInSetStatus or AddInSetStatusText, call AddInQueryDefaults, AddInCreateStatusLine, and AddInSetDefaults. You must also call AddInDeleteStatusLine before termination to deallocate the status line. A program that uses main as the entry point must call NotesInitExtended to initialize the Domino run-time system explicitly before calling any other C API function. It must also call NotesTerm to terminate the Domino run-time system.<br>
<br>
<br>
<b><font size="4" color="#000080">AddInIdle</font></b><br>
<br>
The function AddInIdle yields control of the processor to the server task and receives control back when the server decides the add-in may proceed. A TRUE value is returned from the function call when it is time to shut down the add-in task. <br>
<br>
Use calls to AddInIdle as the add-in task main looping condition, as many of the other add-in functions depend on AddInIdle being called regularly. This also allows the add-in task to respond to the server console commands &quot;quit&quot; or &quot;tell  &lt;taskname&gt; quit&quot;. The main loop should not require more than one to five seconds to complete, to satisfy timing conditions for the HCL Domino Server; operations that require more than five seconds should use AddInShouldTerminate to check every five seconds for termination.<br>
<br>
If the add-in task is running on a non-preemptive operating system such as Windows and its looping condition is compute-bound, it should use the function OSPreemptOccasionally. This causes the add-in to give up control of the processor so that other tasks can run.<br>
<br>
<br>
<b><font size="4" color="#000080">AddInShouldTerminate</font></b><br>
<br>
The function AddInShouldTerminate also returns TRUE when it is time to shut down the add-in task. This function is useful for checking for HCL Domino Server console commands such as &quot;quit&quot; or &quot;tell &lt;taskname&gt; quit&quot; while an add-in task is performing an operation that takes more than five seconds.<br>
<br>
<br>
<b><font size="4" color="#000080">AddInSecondsHaveElapsed, AddInMinutesHaveElapsed</font></b><br>
<br>
Use the functions AddInSecondsHaveElapsed and AddInMinutesHaveElapsed to schedule tasks. To schedule a task to execute every 30 minutes, one would call AddInMinutesHaveElapsed(30), and when this call returned TRUE, execute the task. <br>
<br>
<br>
<b><font size="4" color="#000080">AddInSetStatus, AddInSetStatusText, AddInSetStatusLine</font></b><br>
<br>
AddInSetStatus and AddInSetStatusText sets the status string of the add-in task default status line. The current status is represented by either a resource ID to a status string or a string. AddInSetStatus uses a resource string ID, while AddInSetStatusText uses a string. In either case, this string, along with the name of the add-in task, appears in the task list when the user types &quot;show tasks&quot; at the server console. <br>
<br>
AddInSetStatusLine sets the status string in a specified status line.<br>
<br>
<br>
<b><font size="4" color="#000080">AddInLogMsg, AddInLogMessage, AddInLogMessageText</font></b><br>
<br>
Use these functions to log non-error events to the Domino Log. AddInLogMsg and AddInLogMessage require a resource string ID. AddInLogMessageText uses the actual string. AddInLogMessage and AddInLogMessageText provide more flexible formatting capabilities than AddInLogMsg.<br>
<br>
<br>
<b><font size="5" color="#000080">Checking Server Status</font></b><br>
<br>
Developers of server add-ins are responsible for checking the server status every 5 seconds to see if it is time to quit for every add-in. Using a single add-in task to do the checking and passing that info along to other processes is not sufficient as some process aren't responding to requests to dump memory or to terminate.<br>
<br>
<br>
<b><font size="5" color="#000080">Resource String IDs</font></b><br>
<br>
Resource strings are supported in Windows environments. The C API provides a set of add-in functions that use resource string ID codes. For each function that requires a resource string ID, there is a corresponding function that accepts a string instead.<br>
<br>
For details on how to use resource string IDs, refer to the sample program ADD_RES.<br>
<br>
<br>
<b><font size="5" color="#000080">Debugging a Server Add-In</font></b><br>
<br>
Follow these steps to debug a server add-in task:<br>

<ul type="disc">
<li>Build the add-in with debugger switches turned on. For details, see the section for your platform in the &quot;Platform Specifics&quot; chapter in this User Guide.
<li>Run the server. This ensures that log file messages are correctly logged.
<li>On the same machine as the server, but in a separate window or session, set up your debugger with your add-in task.
<li>Set a breakpoint at AddInMain. Source code is not viewable until AddInMain is entered.
<li>Start your add-in under the debugger.</ul>

---
