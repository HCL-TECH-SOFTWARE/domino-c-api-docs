##### Chapter 12-12
##### Multi-Threaded Application Support

<b><font size="5" color="#000080">Introduction </font></b><br>
<br>
The HCL C API for Domino and Notes supports mult-threaded applications within the same process.  Each thread must call the NotesInitThread and NotesTermThread routines. <br>
<br>
NotesInitThread performs per-thread initialization for a new thread. A call to this routine is required when a new thread that uses the C API starts, so that internal per-thread storage is initialized and the process thread count is incremented. The thread data includes all local and global Domino database and note handles. Threads that do not call NotesInitThread and reference global Domino handles will corrupt each other's handle values during execution.<br>
<br>
NotesTermThread performs per-thread termination for a thread.  A call to this routine is required when a thread terminates, so that internal per-thread storage is deallocated and the process thread count is decremented. Threads that fail to call the NotesTermThread routine prior to thread termination will leak any allocated resources.<br>
<br>
The main program thread performs initialization and termination for the process by calling NotesInitExtended and NotesTerm, so it does not need to call NotesInitThread and NotesTermThread. Although any thread can call NotesTerm (allowing for flexible process termination), it must always be called by the last thread to ensure appropriate resource deallocation. <br>
<br>
<br>
<b><font size="5" color="#000080">Sharing Domino Handles</font></b><br>
<br>
NotesInitThread provides the capability for separate threads to use global Domino handles when calling the C API. This means that each thread has its own copy of all declared Domino handle global variables, so that modifying the handle values in one thread does not corrupt the handle values of another thread. With this safety comes the limitation that created  handle values (for example, as returned by NSFDbOpen or NSFNoteCreate) are only valid in the scope of the thread and cannot be used by a different thread. Even though the handle variables are global to the program, a thread that calls NotesInitThread is still required to create the relevant handles. <br>
<br>
A global database handle that is opened by one thread can still be shared by a different thread by using NSFDbReopen to acquire a thread-specific copy. Even though you need to reference an additional database handle, overall thread performance will improve if you use NSFDbReopen instead of NSFDbOpen, because the physical database file access is eliminated.<br>
<br>
<br>
<b><font size="5" color="#000080">Multi-Threaded Server Add-In Sample</font></b><font size="5" color="#000080"> </font><br>
<br>
The sample program THREADS demonstrates the multi-threaded application support provided by the C API, implementing the basics for calling the C API from multiple threads.  The program also uses Message Queues for communication from the main thread to the worker threads.<br>
<br>
The source for this sample is in the SAMPLES\SERVER\THREADS directory.  THREADS is a Domino server add-in program that launches three threads, one for each of the following operations:<br>

<ul type="disc">
<li>Every 30 seconds send a message to worker thread 1 that will open the sample database, write a note, and close the database.
<li>Every minute send a message to worker thread 2 that will open the sample database, write a note, and close the database.
<li>Every other minute send a message to worker thread 3 that will open the sample database, read and display the notes, and close the database.</ul>
<br>
Before calling the main program thread entry point AddInMain, Domino calls NotesInitExtended, which initializes the program and the main thread.  The three threads share the sample global database and note handle when accessing the sample database.  Each thread created must call NotesInitThread and NotesTermThread. <br>
<br>
The THREADS sample program also contains basic semaphoring and file locking logic. The main program thread uses semaphores to determine when the three threads have ended. The worker threads use file locking to serialize requests to open the local sample database file. Note that file locking would be unnecessary if the database were located on a remote server. <br>
<br>
The main thread communicates with the worker threads through Message Queues.  A Message Queue is created and opened in the main thread for each worker thread and messages are sent to the threads to perform their operations.  The main thread controls the timing of all messages and sends a Quit message after a specific number of messages have been sent to terminate each thread.  When each worker thread has ended the main thread then terminates. <br>
<br>

<table border="1">
<tr valign="top"><td width="648"><b>threads.c - Global Domino Handle Declarations and Main Thread.</b></td></tr>
</table>
The following code fragment shows the global data declarations and main program thread for the THREADS sample program. The program thread uses the following globals -- a database and note handle, a  semaphore, a file lock count, a generic message queue name, 3 specific message queue names, and an array of 3 message queue handles.  The main program thread opens up the sample database, starts the three threads, and sends messages to the threads to perform their operations based on time intervals.<br>
<br>
<tt><font size="2">... &lt;missing global declarations&gt;</font></tt><br>
<br>
<tt><font size="2">/* Global variables */</font></tt><br>
<br>
<tt><font size="2">DBHANDLE &nbsp; &nbsp;db_handle; &nbsp; &nbsp; &nbsp; /* open handle to sample db */<br>
NOTEHANDLE &nbsp;note_handle; &nbsp; &nbsp; /* note handle */<br>
int &nbsp; &nbsp; &nbsp; &nbsp; semaphore; &nbsp; &nbsp; &nbsp; /* thread semaphore count */<br>
int &nbsp; &nbsp; &nbsp; &nbsp; filelock; &nbsp; &nbsp; &nbsp; &nbsp;/* nsf file lock count */</font></tt><br>
<tt><font size="2">char &nbsp; &nbsp; &nbsp; &nbsp;MsgQueueName[3][128];	 			/* generic Message queue name */</font></tt><br>
<tt><font size="2">char &nbsp; &nbsp; &nbsp; &nbsp;MsgQueue1[] = TASK_QUEUE_PREFIX &quot;MSG_Q1&quot;; /* Message queue name */</font></tt><br>
<tt><font size="2">char &nbsp; &nbsp; &nbsp; &nbsp;MsgQueue2[] = TASK_QUEUE_PREFIX &quot;MSG_Q2&quot;; /* Message queue name */</font></tt><br>
<tt><font size="2">char &nbsp; &nbsp; &nbsp; &nbsp;MsgQueue3[] = TASK_QUEUE_PREFIX &quot;MSG_Q3&quot;; /* Message queue name */</font></tt><br>
<tt><font size="2">MQHANDLE &nbsp; &nbsp;hQueue[3]; 	 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* Handles to message queue */</font></tt><br>
<br>
<tt><font size="2">... &lt;missing global declarations&gt;</font></tt><br>
<br>
<br>
<tt><font size="2">STATUS LNPUBLIC &nbsp;AddInMain (HMODULE hModule, int argc, char *argv[])<br>
{<br>
 &nbsp; &nbsp;<br>
... &lt;missing local declarations&gt;</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp;/* <br>
 &nbsp; &nbsp; &nbsp;Initialize the addin task -<br>
 &nbsp; &nbsp; &nbsp;Set the task name and status string of this add-in task. The task<br>
 &nbsp; &nbsp; &nbsp;name and status string appear on the status line at the Domino<br>
 &nbsp; &nbsp; &nbsp;server in response to the 'show tasks' command. Get the handle to</font></tt><br>
<tt><font size="2">	this default status line descriptor and delete it. Then create a new </font></tt><br>
<tt><font size="2">	status line and set the status to 'Initializing'.<br>
 &nbsp; &nbsp;*/<br>
 </font></tt><br>
<tt><font size="2">... &lt;missing code&gt;</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; /* Open sample database and assign global handle */</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; if (error = NSFDbOpen (DATABASE_NAME, &amp;db_handle))<br>
 &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp; &nbsp;AddInLogMessageText(&quot;Error opening database.&quot;, ERR(error));<br>
 &nbsp; &nbsp; &nbsp; &nbsp;return(ERR(error));<br>
 &nbsp; &nbsp;}</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp;/* Initialize semaphore and lock counts and spawn threads for each of <br>
	the addin operations<br>
 &nbsp; &nbsp;*/</font></tt><br>
<br>
<tt><font size="2">	semaphore = 0;<br>
	filelock = 0;</font></tt><br>
<br>
<tt><font size="2">#ifdef WIN32								 &nbsp;<br>
	_beginthread (ThirtySecOps, 0, NULL); &nbsp; /* 30 Second op thread */<br>
	_beginthread (OneMinOps, 0, NULL); &nbsp; &nbsp; &nbsp;/* 1 Minute op thread */<br>
	_beginthread (TwoMinOps, 0, NULL); &nbsp; &nbsp; &nbsp;/* 2 Minute op thread */<br>
#else <br>
	_beginthread (ThirtySecOps, NULL, 16384, NULL); &nbsp; /* 30 Second op thread */<br>
	_beginthread (OneMinOps, NULL, 16384, NULL); &nbsp; &nbsp; &nbsp;/* 1 Minute op thread */<br>
	_beginthread (TwoMinOps, NULL, 16384, NULL); &nbsp; &nbsp; &nbsp;/* 2 Minute op thread */<br>
#endif</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; </font></tt><tt><font size="2">/* Create and Open Message Queues for worker threads */</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; </font></tt><br>
<tt><font size="2">&nbsp; &nbsp; strcpy(MsgQueueName[0], MsgQueue1);</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; strcpy(MsgQueueName[1], MsgQueue2);</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; strcpy(MsgQueueName[2], MsgQueue3);</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; for (i=0; i&lt;3; i++)</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; {</font></tt><br>
<tt><font size="2">&nbsp; &nbsp;	error = MQCreate (MsgQueueName[i], 0, 0);	/* No quota on messages */</font></tt><br>
<tt><font size="2">&nbsp; &nbsp;	if (NOERROR != error)</font></tt><br>
<tt><font size="2">&nbsp; &nbsp;		return (ERR(error));</font></tt><br>
<tt><font size="2">&nbsp; &nbsp;	</font></tt><br>
<tt><font size="2">&nbsp; &nbsp;	error = MQOpen (MsgQueueName[i], 0, &amp;hQueue[i]);</font></tt><br>
<tt><font size="2">&nbsp; &nbsp;	if (NOERROR != error)</font></tt><br>
<tt><font size="2">&nbsp; &nbsp;		return (ERR(error));</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; }</font></tt><br>
<br>
<br>
<tt><font size="2">&nbsp; &nbsp;/* Initialize semaphore and lock counts and spawn threads for each of </font></tt><br>
<tt><font size="2">	the addin operations</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; */</font></tt><br>
<br>
<tt><font size="2">	semaphore = 0;</font></tt><br>
<tt><font size="2">	filelock = 0;</font></tt><br>
<br>
<tt><font size="2">#ifdef WIN32								 &nbsp;</font></tt><br>
<tt><font size="2">	_beginthread (ThirtySecOps, 0, NULL); &nbsp; /* 30 Second op thread */</font></tt><br>
<tt><font size="2">	_beginthread (OneMinOps, 0, NULL); &nbsp; &nbsp; &nbsp;/* 1 Minute op thread */</font></tt><br>
<tt><font size="2">	_beginthread (TwoMinOps, 0, NULL); &nbsp; &nbsp; &nbsp;/* 2 Minute op thread */</font></tt><br>
<tt><font size="2">#else </font></tt><br>
<tt><font size="2">	_beginthread (ThirtySecOps, NULL, 16384, NULL); &nbsp; /* 30 Second op thread */</font></tt><br>
<tt><font size="2">	_beginthread (OneMinOps, NULL, 16384, NULL); &nbsp; &nbsp; &nbsp;/* 1 Minute op thread */</font></tt><br>
<tt><font size="2">	_beginthread (TwoMinOps, NULL, 16384, NULL); &nbsp; &nbsp; &nbsp;/* 2 Minute op thread */</font></tt><br>
<tt><font size="2">#endif</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; </font></tt><br>
<tt><font size="2">&nbsp; &nbsp; /* get current time and initialize thread operation times */</font></tt><br>
<tt><font size="2">	TIME(&amp;cur_time);</font></tt><br>
<tt><font size="2">	op_time_1 = cur_time;</font></tt><br>
<tt><font size="2">	op_time_2 = cur_time;</font></tt><br>
<tt><font size="2">	op_time_3 = cur_time;</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; /* The main add-in loop assigns jobs to each thread by sending messages through</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp;* the thread message queues. &nbsp;Each thread is then told to terminate after a &nbsp; &nbsp; </font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp;* specific number of job assignments have been sent.</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp;*/</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp;while ((!AddInIdleDelay(5000L)) &amp;&amp; (threadsdone &lt; 3))</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp;{</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; 	OSPreemptOccasionally();</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; 	if (semaphore == 0)</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 		goto Done;</font></tt><br>
<tt><font size="2">		</font></tt><br>
<tt><font size="2">	 &nbsp;	/* get current time */</font></tt><br>
<tt><font size="2">	 &nbsp;	TIME(&amp;cur_time);</font></tt><br>
<font size="4" face="Times New Roman">       		</font><tt><font size="2">/* send message every 30 seconds to worker thread 1 */</font></tt><br>
<tt><font size="2">		if (cur_time == op_time_1 + THIRTYSECONDS)</font></tt><br>
<tt><font size="2">	 &nbsp; &nbsp;	{</font></tt><br>
<tt><font size="2">			/* if assigned jobs == 6 tell thread to quit */</font></tt><br>
<tt><font size="2">		</font></tt><font size="4" face="Times New Roman">  	</font><tt><font size="2">if (++counter1 == 6)</font></tt><br>
<tt><font size="2">		 &nbsp;	{</font></tt><br>
<tt><font size="2">		</font></tt><font size="4" face="Times New Roman">       		</font><tt><font size="2">strcpy(MsgBuffer[0], &quot;QUIT&quot;);</font></tt><br>
<tt><font size="2">		 &nbsp; &nbsp;		MsgLen = strlen(MsgBuffer[0]);</font></tt><br>
<br>
<font size="4" face="Times New Roman">            			</font><tt><font size="2">/* put the QUIT message in the first queue */</font></tt><br>
<tt><font size="2">				error = MQPut (hQueue[0], 1, MsgBuffer[0], MsgLen, 0);</font></tt><br>
<tt><font size="2">		 &nbsp; &nbsp;		if (error)</font></tt><br>
<tt><font size="2">		 &nbsp; &nbsp; &nbsp;		goto Done;</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 		threadsdone++;</font></tt><br>
<tt><font size="2">		 &nbsp;	}</font></tt><br>
<tt><font size="2">		</font></tt><font size="4" face="Times New Roman"> 	 </font><tt><font size="2">else /* tell thread to run job */</font></tt><br>
<tt><font size="2">		 &nbsp;	{</font></tt><br>
<tt><font size="2">	 &nbsp;			strcpy(MsgBuffer[0], &quot;RUN&quot;);</font></tt><br>
<tt><font size="2">		 &nbsp; &nbsp;		MsgLen = strlen(MsgBuffer[0]);</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; </font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 		/* put the RUN message in the first queue */</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 		error = MQPut (hQueue[0], 1, MsgBuffer[0], MsgLen, 0);</font></tt><br>
<tt><font size="2">		 &nbsp; &nbsp;		if (error)</font></tt><br>
<tt><font size="2">		 &nbsp; &nbsp; 			goto Done;</font></tt><br>
<tt><font size="2">		 &nbsp;	}</font></tt><br>
<font size="4" face="Times New Roman">        			</font><tt><font size="2">op_time_1 += THIRTYSECONDS; /* bump up time another 30 seconds */</font></tt><br>
<tt><font size="2">	</font></tt><font size="4" face="Times New Roman">    	}</font><br>
<font size="4" face="Times New Roman">      	</font><br>
<font size="4" face="Times New Roman"> 		</font><tt><font size="2">/* send message every 60 seconds to worker thread 2 */</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; 	else if (cur_time == op_time_2 + SIXTYSECONDS)</font></tt><br>
<tt><font size="2">	 &nbsp; &nbsp;	{</font></tt><br>
<tt><font size="2">		 &nbsp; 	/* if assigned jobs == 3 tell thread to quit */</font></tt><br>
<tt><font size="2">		 	if (++counter2 == 3)</font></tt><br>
<tt><font size="2">		 &nbsp;	{</font></tt><br>
<tt><font size="2">		 &nbsp; &nbsp;		strcpy(MsgBuffer[1], &quot;QUIT&quot;);</font></tt><br>
<tt><font size="2">		 &nbsp; 		MsgLen = strlen(MsgBuffer[1]);</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;			/* put the QUIT message in the second queue */</font></tt><br>
<tt><font size="2">				error = MQPut (hQueue[1], 1, MsgBuffer[1], MsgLen, 0);</font></tt><br>
<tt><font size="2">		 &nbsp; &nbsp;		if (error)</font></tt><br>
<tt><font size="2">	 &nbsp; &nbsp; &nbsp;			goto Done;</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp;			threadsdone++;</font></tt><br>
<tt><font size="2">		 	}</font></tt><br>
<tt><font size="2">		 &nbsp;	else /* tell thread to run job */</font></tt><br>
<tt><font size="2">		 &nbsp;	{</font></tt><br>
<tt><font size="2">		 &nbsp; &nbsp;		strcpy(MsgBuffer[1], &quot;RUN&quot;);</font></tt><br>
<tt><font size="2">		 &nbsp; &nbsp;		MsgLen = strlen(MsgBuffer[1]);</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; </font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;			/* put the RUN message in the second queue */</font></tt><br>
<tt><font size="2">	 &nbsp; &nbsp; &nbsp; &nbsp;		error = MQPut (hQueue[1], 1, MsgBuffer[1], MsgLen, 0);</font></tt><br>
<tt><font size="2">		 &nbsp; &nbsp;		if (error)</font></tt><br>
<tt><font size="2">		 &nbsp; &nbsp; 			 goto Done;</font></tt><br>
<tt><font size="2">		 &nbsp;	}</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 		op_time_2 += SIXTYSECONDS; /* bump up time another 60 seconds */</font></tt><br>
<tt><font size="2">	 &nbsp; 	}</font></tt><br>
<br>
<tt><font size="2">	 &nbsp; &nbsp;	/* send message every two minutes to worker thread 3 */</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; 	else if (cur_time == op_time_3 + TWOMINUTES)</font></tt><br>
<tt><font size="2">	 &nbsp; &nbsp;	{</font></tt><br>
<tt><font size="2">			/* if assigned jobs == 2 tell thread to quit */</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; 		if (++counter3 == 2)</font></tt><br>
<tt><font size="2">		 &nbsp;	{</font></tt><br>
<tt><font size="2">		 &nbsp; &nbsp;		strcpy(MsgBuffer[2], &quot;QUIT&quot;);</font></tt><br>
<tt><font size="2">		 &nbsp; &nbsp;		MsgLen = strlen(MsgBuffer[2]);</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; </font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;			/* put the QUIT message in the third queue */</font></tt><br>
<tt><font size="2">				error = MQPut (hQueue[2], 1, MsgBuffer[2], MsgLen, 0);</font></tt><br>
<tt><font size="2">		</font></tt><font size="4" face="Times New Roman">    		</font><tt><font size="2">if (error)</font></tt><br>
<tt><font size="2">	 &nbsp; &nbsp; &nbsp;			goto Done;</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;			threadsdone++;</font></tt><br>
<tt><font size="2">		</font></tt><font size="4" face="Times New Roman">  	</font><tt><font size="2">}</font></tt><br>
<tt><font size="2">		</font></tt><font size="4" face="Times New Roman">  	</font><tt><font size="2">else /* tell thread to run job */</font></tt><br>
<tt><font size="2">		 &nbsp;	{</font></tt><br>
<tt><font size="2">		 &nbsp; &nbsp;		strcpy(MsgBuffer[2], &quot;RUN&quot;);</font></tt><br>
<tt><font size="2">		 &nbsp; &nbsp;		MsgLen = strlen(MsgBuffer[2]);</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; </font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 		/* put the RUN message in the third queue */</font></tt><br>
<tt><font size="2">	 &nbsp; &nbsp; &nbsp; &nbsp;		error = MQPut (hQueue[2], 1, MsgBuffer[2], MsgLen, 0);</font></tt><br>
<tt><font size="2">		 &nbsp; &nbsp;		if (error)</font></tt><br>
<tt><font size="2">		 &nbsp; &nbsp; &nbsp;		goto Done;</font></tt><br>
<tt><font size="2">		 &nbsp;	}</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 		op_time_3 += TWOMINUTES; /* bump up time another 2 minutes */</font></tt><br>
<tt><font size="2">	 &nbsp; &nbsp;	}</font></tt><br>
<br>
<font size="4" face="Times New Roman">  </font><tt><font size="2">&nbsp; &nbsp;}</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp;/* We get here when the server notifies us that it is time to terminate. <br>
 &nbsp; &nbsp; &nbsp;This can occur when <br>
		1) The user has entered &quot;quit&quot; at the server console. <br>
		2) The user has entered &quot;tell &lt;ThisTask&gt; quit&quot; at the server console.<br>
		3) All three operation threads have ended.<br>
 &nbsp; &nbsp;*/</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; /* Wait for threads to term</font></tt><tt>inate or for user to exit */</tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; AddInSetStatusText(&quot;Terminating Add-In Threads&quot;);<br>
 &nbsp; &nbsp;while ( semaphore )<br>
 &nbsp; &nbsp; &nbsp; &nbsp;SLEEP(5000L);</font></tt><br>
<br>
<tt><font size="2">Done:<br>
 &nbsp; &nbsp;/* close the message queues */</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; for (i=0; i&lt;3; i++)</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; {</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp;	error = MQClose (hQueue[i], 0);</font></tt><br>
<tt><font size="2">&nbsp; &nbsp;	if (error)</font></tt><br>
<tt><font size="2">&nbsp; &nbsp;		return (ERR(error));</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; }</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; NSFDbClose (db_handle);</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; AddInSetStatusText(&quot;Terminating Add-in&quot;);<br>
 &nbsp; &nbsp;AddInLogMessageText(&quot;THREADS: Termination complete.&quot;, NOERROR);<br>
 &nbsp; &nbsp;<br>
 &nbsp; /* End of add-in task. We must &quot;return&quot; here rather than &quot;exit&quot;. */</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; return (NOERROR);<br>
}</font></tt><br>
<br>
<br>

<table border="1">
<tr valign="top"><td width="648"><b>threads.c - &quot;Writer&quot; Thread and Service Routines.</b></td></tr>
</table>
The following code fragment shows the two threads functions called by AddInMain and the service routine called by the threads to write a note to the sample database. Each thread increments the semaphore and calls NotesInitThread prior to entering its service loop, and decrements the semaphore and calls NotesTermThread prior to ending the function. In the service loop, the thread function: 
<ul>
<ol type="1">
<li>Waits for a message from the main thread to perform an operation and periodically  checks to see if the add-in has been terminated by the user.  
<li>If the RUNOP message is received it sets the database file lock (when available).
<li>Performs the database operation by calling the service routine WriteOpNote.
<li>If the QUITOP message is received the thread terminates. </ol>
</ul>
<br>
The WriteOpNote routine reopens the global database handle to a local handle and uses the thread's s database and note handles with the corresponding C API routines to write the note. This routine unlocks the database file at completion and returns to the calling routine. <br>
<br>
 <br>
<tt><font size="2">/************************************************************************</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; FUNCTION: &nbsp; ThirtySecOps</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; PURPOSE: &nbsp; &nbsp;Add-in thread routine that performs &quot;30 Second&quot; operations<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;by writing a note to the sample database.</font></tt><br>
<br>
<tt><font size="2">*************************************************************************/</font></tt><br>
<br>
<tt><font size="2">#ifdef WIN32<br>
void ThirtySecOps(void *dummy)<br>
#else<br>
void _Optlink ThirtySecOps(void *dummy)<br>
#endif<br>
{<br>
 &nbsp; &nbsp;STATUS &nbsp;error;<br>
 &nbsp; &nbsp;int &nbsp; &nbsp; timer;<br>
 &nbsp; &nbsp;int &nbsp; &nbsp; counter = 0;<br>
 &nbsp; &nbsp;int &nbsp; &nbsp; op = 0;</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; char &nbsp; &nbsp;MsgBuffer [MAX_MESSAGE + 1];	/* Buffer for messages */</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; WORD &nbsp; &nbsp;MsgLen;				/* Size of message */ &nbsp; <br>
 &nbsp; </font></tt><br>
<tt><font size="2">&nbsp; &nbsp;/* First increment semaphore */</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; semaphore++;<br>
 &nbsp; &nbsp; <br>
 &nbsp; /* Initialize Domino thread - required by threads calling the C API. */</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; error = NotesInitThread (); &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; <br>
 &nbsp; &nbsp;if (error)<br>
 &nbsp; &nbsp;{<br>
	AddInLogMessageText(&quot;Error initializing 30 Second operation thread.&quot;, NOERROR);<br>
 &nbsp; &nbsp;	semaphore--;</font></tt><br>
<tt><font size="2">	_endthread();<br>
 &nbsp; &nbsp;}</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; </font></tt><tt><font size="2">/* while there isn't an error loop for messages from main thread */</font></tt><br>
<font size="4" face="Times New Roman">    </font><tt><font size="2">&nbsp; while (NOERROR == error)</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; {</font></tt><br>
<font size="4" face="Times New Roman">        	</font><tt><font size="2">/* if the main thread terminates we're done */</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp;	if (AddInShouldTerminate())</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp;	goto Done;</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; </font></tt><br>
<tt><font size="2">	/* attempt to get a message from the queue and wait for 5 seconds */ </font></tt><br>
<tt><font size="2">	error = MQGet (hQueue[0], MsgBuffer, MAX_MESSAGE,</font></tt><br>
<tt><font size="2">	 &nbsp;		 &nbsp;MQ_WAIT_FOR_MSG, (5 * 1000), &amp;MsgLen);</font></tt><br>
<br>
<tt><font size="2">	MsgBuffer[MsgLen] = '\0';</font></tt><br>
<br>
<font size="4" face="Times New Roman">       </font><tt><font size="2">&nbsp;	/* if we received a message... */</font></tt><br>
<tt><font size="2">	if (NOERROR == error)</font></tt><br>
<tt><font size="2">	{</font></tt><br>
<tt><font size="2">		/* get the message from the buffer */</font></tt><br>
<tt><font size="2">		op = ProcessMessage (MsgBuffer, MsgLen);</font></tt><br>
<tt><font size="2">	</font></tt><br>
<tt><font size="2">	 &nbsp; &nbsp; &nbsp;/* perform operation depending on message received */</font></tt><br>
<tt><font size="2">	 &nbsp; &nbsp; &nbsp;switch(op)</font></tt><br>
<tt><font size="2">		{</font></tt><br>
<tt><font size="2">			/* run the job assignment */</font></tt><br>
<tt><font size="2">			case RUNOP:</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 		AddInSetStatusText(&quot;Performing 30 Second operation&quot;);</font></tt><br>
<tt><font size="2">	 &nbsp; &nbsp;</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 		/* Do not write note until the database is no longer opened 	</font></tt><br>
<tt><font size="2">				 * by one of the other threads.</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;		 */</font></tt><br>
<tt><font size="2">	 &nbsp; &nbsp; &nbsp; &nbsp;</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 		while ( filelock ) </font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;			SLEEP (50L);</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 		filelock++; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; /* lock database */</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; 	 &nbsp; &nbsp; &nbsp; &nbsp;		if (error = WriteOpNote(THIRTYSECOP)) &nbsp; /* and write note */</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 		{</font></tt><br>
<tt><font size="2">		 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;		AddInLogMessageText(&quot;Error writing 30 Second 	</font></tt><br>
<tt><font size="2">					operation &nbsp;Note to database.&quot;, ERR(error));</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 			goto Done;</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 		}</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; 	 &nbsp; &nbsp; &nbsp; &nbsp;		AddInLogMessageText(&quot;THREADS: 30 Second operation </font></tt><br>
<tt><font size="2">				complete.&quot;, NOERROR);</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; 	 &nbsp; &nbsp; &nbsp; &nbsp;		AddInSetStatusText(&quot;30 Second operation Idle&quot;);</font></tt><br>
<tt><font size="2">			 &nbsp; 	break;</font></tt><br>
<tt><font size="2">			</font></tt><br>
<tt><font size="2">			 &nbsp;/* quit the job */</font></tt><br>
<tt><font size="2">			 &nbsp;case QUITOP:</font></tt><br>
<tt><font size="2">				goto Done;</font></tt><br>
<tt><font size="2">			 &nbsp; &nbsp;	break;</font></tt><br>
<tt><font size="2">			</font></tt><br>
<tt><font size="2">			 &nbsp;default:</font></tt><br>
<tt><font size="2">				error = op;</font></tt><br>
<tt><font size="2">		 &nbsp; &nbsp; &nbsp; &nbsp;	break;</font></tt><br>
<tt><font size="2">		}</font></tt><br>
<tt><font size="2">	}</font></tt><br>
<tt><font size="2">	/* if we have a timeout loop again */</font></tt><br>
<tt><font size="2">	else if (ERR_MQ_TIMEOUT == error)</font></tt><br>
<tt><font size="2">	{</font></tt><br>
<tt><font size="2">		error = NOERROR;</font></tt><br>
<tt><font size="2">	}</font></tt><br>
<tt><font size="2">&nbsp; &nbsp;</font></tt><br>
<tt><font size="2">&nbsp; &nbsp;} &nbsp; /* End of main task loop. */</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp;/* We get here when the server notifies us that it is time to terminate. <br>
 &nbsp; &nbsp; &nbsp;Clean up anything we have been doing. <br>
 &nbsp; &nbsp;*/</font></tt><br>
<br>
<tt><font size="2">Done:<br>
 &nbsp; &nbsp;AddInLogMessageText(&quot;THREADS: Ending 30 Second operation thread.&quot;, NOERROR);<br>
 &nbsp; &nbsp;AddInSetStatusText(&quot;Exiting 30 Second operation&quot;);</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp;/* Terminate Notes thread, decrement semaphore count, and end OS thread */</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; NotesTermThread (); &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; <br>
 &nbsp; &nbsp;semaphore--;<br>
 &nbsp; &nbsp;_endthread();<br>
} </font></tt><br>
<br>
<br>
<tt><font size="2">/************************************************************************</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; FUNCTION: &nbsp; OneMinOps</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; PURPOSE: &nbsp; &nbsp;Add-in thread routine that performs &quot;1 Minute&quot; operations<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;by writing a note to the sample database.</font></tt><br>
<br>
<tt><font size="2">*************************************************************************/</font></tt><br>
<br>
<tt><font size="2">#ifdef WIN32<br>
void OneMinOps(void *dummy)<br>
#else <br>
void _Optlink OneMinOps(void *dummy)<br>
#endif<br>
{<br>
 &nbsp; &nbsp;STATUS &nbsp;error;<br>
 &nbsp; &nbsp;int &nbsp; &nbsp; timer;<br>
 &nbsp; &nbsp;int &nbsp; &nbsp; counter = 0;<br>
 &nbsp; &nbsp;int &nbsp; &nbsp; op = 0;</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; char &nbsp; &nbsp;MsgBuffer [MAX_MESSAGE + 1];	/* Buffer for messages */</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; WORD &nbsp; &nbsp;MsgLen;				/* Size of message */</font></tt><br>
<tt><font size="2">&nbsp; &nbsp;<br>
 &nbsp; /* First increment semaphore */</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; semaphore++;</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp;/* Initialize Notes thread - required by threads calling the C API. */</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; error = NotesInitThread (); &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; <br>
 &nbsp; &nbsp;if (error)<br>
 &nbsp; &nbsp;{<br>
 &nbsp; &nbsp;	AddInLogMessageText(&quot;Error initializing 1 Minute operation thread.&quot;, NOERROR);<br>
 &nbsp; &nbsp; &nbsp;semaphore--;<br>
 &nbsp; &nbsp; &nbsp;_endthread();<br>
 &nbsp; &nbsp;}<br>
 <br>
 &nbsp; </font></tt><br>
<tt><font size="2">&nbsp; &nbsp; /* while there isn't an error loop for messages from main thread */</font></tt><br>
<tt><font size="2">&nbsp;</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; while (NOERROR == error)</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; {</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; 	/* if the main thread terminates we're done */</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; if (AddInShouldTerminate())</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp;	goto Done;</font></tt><br>
<tt><font size="2">	</font></tt><br>
<tt><font size="2">	/* attempt to get a message from the queue and wait for 5 seconds */ </font></tt><br>
<tt><font size="2">	error = MQGet (hQueue[1], MsgBuffer, MAX_MESSAGE,</font></tt><br>
<tt><font size="2">	 &nbsp;		 &nbsp;MQ_WAIT_FOR_MSG, (5 * 1000), &amp;MsgLen);</font></tt><br>
<br>
<tt><font size="2">	MsgBuffer[MsgLen] = '\0';</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; /* if we received a message... */</font></tt><br>
<tt><font size="2">	if (NOERROR == error)</font></tt><br>
<tt><font size="2">	{</font></tt><br>
<tt><font size="2">		/* get the message from the buffer */</font></tt><br>
<tt><font size="2">		op = ProcessMessage (MsgBuffer, MsgLen);</font></tt><br>
<tt><font size="2">	</font></tt><br>
<tt><font size="2">	 &nbsp; &nbsp; &nbsp;/* perform operation depending on message received */</font></tt><br>
<tt><font size="2">	 &nbsp; &nbsp; &nbsp;switch(op)</font></tt><br>
<tt><font size="2">		{</font></tt><br>
<tt><font size="2">			/* run the job assignment */</font></tt><br>
<tt><font size="2">			case RUNOP:</font></tt><br>
<tt><font size="2">				AddInSetStatusText(&quot;Performing 1 Minute operation&quot;);</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 		/* Do not write note until the database is no longer opened 					by one	of the other threads.</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 		*/</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; 	 &nbsp; &nbsp;</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 		while ( filelock ) </font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;			SLEEP (50L);</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 		filelock++; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; /* lock database */</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp;	 &nbsp; &nbsp; &nbsp; 	if (error = WriteOpNote(ONEMINOP)) &nbsp;/* and write note */</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 		{</font></tt><br>
<tt><font size="2">		 &nbsp; &nbsp; &nbsp; 		AddInLogMessageText(&quot;Error writing 1 Minute operation &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;					note to database.&quot;, ERR(error));</font></tt><br>
<tt><font size="2">	 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;		goto Done;</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 		}</font></tt><br>
<tt><font size="2">	 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;	AddInLogMessageText(&quot;THREADS: 1 Minute operation complete.&quot;, 						 &nbsp; &nbsp; &nbsp;NOERROR);</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; 	 &nbsp; &nbsp; &nbsp; &nbsp;		AddInSetStatusText(&quot;1 Minute operation idle&quot;);</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 		break;</font></tt><br>
<tt><font size="2">			</font></tt><br>
<tt><font size="2">			/* quit the job */</font></tt><br>
<tt><font size="2">			case QUITOP:</font></tt><br>
<tt><font size="2">				goto Done;</font></tt><br>
<tt><font size="2">				break;</font></tt><br>
<tt><font size="2">			</font></tt><br>
<tt><font size="2">			default:</font></tt><br>
<tt><font size="2">				error = op;</font></tt><br>
<tt><font size="2">		 &nbsp; &nbsp; &nbsp; &nbsp;	break;</font></tt><br>
<tt><font size="2">		}</font></tt><br>
<tt><font size="2">	}</font></tt><br>
<tt><font size="2">	else if (ERR_MQ_TIMEOUT == error)</font></tt><br>
<tt><font size="2">	{</font></tt><br>
<tt><font size="2">		error = NOERROR;</font></tt><br>
<tt><font size="2">	}</font></tt><br>
<tt><font size="2">&nbsp; &nbsp;</font></tt><br>
<tt><font size="2">&nbsp; &nbsp;} &nbsp; /* End of main task loop. */</font></tt><br>
<br>
<br>
<tt><font size="2">&nbsp; &nbsp;/* We get here when the server notifies us that it is time to terminate. <br>
 &nbsp; &nbsp; &nbsp;Clean up anything we have been doing. <br>
 &nbsp; &nbsp;*/<br>
 &nbsp; &nbsp;<br>
Done:<br>
 &nbsp; &nbsp;AddInLogMessageText(&quot;THREADS: Ending 1 Minute operation thread.&quot;, NOERROR);<br>
 &nbsp; &nbsp;AddInSetStatusText(&quot;Exiting 1 Minute operation&quot;);</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp;/* Terminate Notes thread, decrement semaphore count, and end OS thread */</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; NotesTermThread (); <br>
 &nbsp; &nbsp;semaphore--;<br>
 &nbsp; &nbsp;_endthread();<br>
} </font></tt><br>
<br>
<tt><font size="2">/************************************************************************</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; FUNCTION: &nbsp; WriteOpNote</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; PURPOSE: &nbsp; &nbsp;Local function called by the operation thread routines to <br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;write a note to the sample database. Checks that file <br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;locks are in place before opening local database.</font></tt><br>
<br>
<tt><font size="2">*************************************************************************/</font></tt><br>
<br>
<tt><font size="2">STATUS WriteOpNote (char *op_thread)<br>
{</font></tt><br>
<br>
<tt><font size="2">/* Local data declarations. */</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; DBHANDLE &nbsp; write_handle; &nbsp; &nbsp; &nbsp;/* local database handle */</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; STATUS &nbsp; &nbsp; error = NOERROR; &nbsp; /* return code from API calls */<br>
 &nbsp; &nbsp;TIMEDATE &nbsp; timedate; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* contents of a time/date field */<br>
 &nbsp; &nbsp;char &nbsp; &nbsp; &nbsp; thread_text[64]; &nbsp; /* thread specific item text */</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp;/* First ensure that the file has been locked. */</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; if (filelock &lt; 1) <br>
 &nbsp; &nbsp;{<br>
 &nbsp; &nbsp;	filelock = 0;<br>
 &nbsp; &nbsp; &nbsp;return (ERR(ERR_LOCK_FAILED));<br>
 &nbsp; &nbsp;}<br>
 &nbsp; &nbsp;<br>
 &nbsp; /* Then ensure that the database file has been locked by only one thread. */<br>
 &nbsp; <br>
 &nbsp; &nbsp;if (filelock &gt; 1) <br>
 &nbsp; &nbsp;{<br>
	error = ERR_LOCK;<br>
 &nbsp; &nbsp; &nbsp;goto Done;<br>
 &nbsp; &nbsp;}</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp;/* Reopen the database from the global handle. */</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; if (error = NSFDbReopen (db_handle, &amp;write_handle))<br>
 &nbsp; &nbsp;	goto Done;<br>
 &nbsp; <br>
 &nbsp; /* Create a new data note. */</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; if (error = NSFNoteCreate (write_handle, &amp;note_handle))<br>
 &nbsp; &nbsp;{<br>
	NSFDbClose (write_handle);<br>
 &nbsp; &nbsp;	goto Done;<br>
 &nbsp; &nbsp;}</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp;/* Write the form name to the note. */</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; if (error = NSFItemSetText (note_handle, &quot;Form&quot;, &quot;AddInForm&quot;, MAXWORD))<br>
 &nbsp; &nbsp;{<br>
 &nbsp; &nbsp;	NSFNoteClose (note_handle);<br>
 &nbsp; &nbsp;	NSFDbClose (write_handle);<br>
	goto Done;<br>
 &nbsp; &nbsp;}<br>
 &nbsp; &nbsp;<br>
 &nbsp; /* Write a text field to the note. */</font></tt><br>
<br>
<tt><font size="2">... &lt;missing code&gt;</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; <br>
 &nbsp; /* Write the current time into the note. */</font></tt><br>
<br>
<tt><font size="2">... &lt;missing code&gt;</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp;/* Add the note to the database. */</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; if (error = NSFNoteUpdate (note_handle, 0))<br>
 &nbsp; &nbsp;{<br>
	NSFNoteClose (note_handle);<br>
 &nbsp; &nbsp;	NSFDbClose (write_handle);<br>
 &nbsp; &nbsp;	goto Done;<br>
 &nbsp; &nbsp;}</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp;/* Deallocate the new note from memory. */</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; if (error = NSFNoteClose (note_handle))<br>
 &nbsp; &nbsp;{<br>
	NSFDbClose (write_handle);<br>
 &nbsp; &nbsp;	goto Done;<br>
 &nbsp; &nbsp;}<br>
 &nbsp; &nbsp;<br>
 &nbsp; /* Close the database. */</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; if (error = NSFDbClose (write_handle))<br>
	goto Done;</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; <br>
 &nbsp; /* End of function. Unlock database file and return status. */</font></tt><br>
<br>
<tt><font size="2">Done:<br>
 &nbsp; &nbsp;filelock--;<br>
 &nbsp; &nbsp;return (error);<br>
}</font></tt><br>
<br>
<br>

<table border="1">
<tr valign="top"><td width="648"><b>threads.c - &quot;Reader&quot; Thread and Service Routines.</b></td></tr>
</table>
The following code fragment shows the thread functions called by AddInMain and the service routine called by the thread to read and display the notes in the sample database. The thread increments the semaphore and calls NotesInitThread before entering its service loop, and decrements the semaphore and calls NotesTermThread before ending the function. Within the service loop, the thread function: 
<ul></ul>

<ol type="1">
<li>Waits for a message from the main thread to perform an operation and periodically checks to see if the add-in has been terminated by the user.
<li>If the RUNOP message is received it sets the file lock (when available) and reopens the global database handle to a local handle.
<li>Performs the database operation by calling the NSFSearch service routine ReadOpNote.Closes and unlocks the database.
<li>If the QUITOP message is received the thread terminates. </ol>
<br>
The ReadOpNote routine uses the thread's database and note handle values with the corresponding C API routines to open and read the notes from the database.<br>
<br>
<tt><font size="2">/************************************************************************</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; FUNCTION: &nbsp; TwoMinOps</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; PURPOSE: &nbsp; &nbsp;Addin thread routine that performs &quot;2 Minute&quot; operations..<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;by reading and displaying all the notes in the sample database.</font></tt><br>
<br>
<tt><font size="2">*************************************************************************/</font></tt><br>
<br>
<tt><font size="2">#ifdef WIN32<br>
void TwoMinOps(void *dummy)<br>
#else <br>
void _Optlink TwoMinOps(void *dummy)<br>
#endif<br>
{<br>
 &nbsp; &nbsp;DBHANDLE	read_handle; &nbsp; &nbsp;/* local database handle */</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; STATUS &nbsp;	error;<br>
 &nbsp; &nbsp;int &nbsp; &nbsp; 	counter = 0;<br>
 &nbsp; &nbsp;int &nbsp; &nbsp; 	op = 0;</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; char &nbsp; &nbsp;	MsgBuffer [MAX_MESSAGE + 1];	/* Buffer for messages */</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; WORD &nbsp; &nbsp;	MsgLen;				/* Size of message */	 &nbsp; <br>
 &nbsp; </font></tt><br>
<tt><font size="2">&nbsp; &nbsp;/* First increment semaphore */</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; semaphore++;</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp;/* Initialize Notes thread - required by threads calling the C API. */</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; error = NotesInitThread (); &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; <br>
 &nbsp; &nbsp;if (error)<br>
 &nbsp; &nbsp;{<br>
 &nbsp; &nbsp;	AddInLogMessageText(&quot;Error initializing 2 Minute operation thread.&quot;, NOERROR);<br>
 &nbsp; &nbsp; &nbsp;semaphore--;<br>
 &nbsp; &nbsp; &nbsp;_endthread();<br>
 &nbsp; &nbsp;}</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp;</font></tt><tt><font size="2">/* while there isn't an error loop for messages from main thread */</font></tt><br>
<tt><font size="2">&nbsp;</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; while (NOERROR == error)</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; {</font></tt><br>
<font size="4" face="Times New Roman">       	</font><tt><font size="2">/* if the main thread terminates we're done */</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; if (AddInShouldTerminate())</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp;	goto Done;</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; </font></tt><br>
<tt><font size="2">	/* attempt to get a message from the queue and wait for 5 seconds */ </font></tt><br>
<tt><font size="2">	error = MQGet (hQueue[2], MsgBuffer, MAX_MESSAGE,</font></tt><br>
<tt><font size="2">	 &nbsp;		 &nbsp;MQ_WAIT_FOR_MSG, (5 * 1000), &amp;MsgLen);</font></tt><br>
<br>
<tt><font size="2">	MsgBuffer[MsgLen] = '\0';</font></tt><br>
<br>
<font size="4" face="Times New Roman">       </font><tt><font size="2">&nbsp;	/* if we received a message... */</font></tt><br>
<tt><font size="2">	if (NOERROR == error)</font></tt><br>
<tt><font size="2">	{</font></tt><br>
<tt><font size="2">		/* get the message from the buffer */</font></tt><br>
<tt><font size="2">		op = ProcessMessage (MsgBuffer, MsgLen);</font></tt><br>
<tt><font size="2">	</font></tt><br>
<tt><font size="2">	 &nbsp; &nbsp; &nbsp;/* perform operation depending on message received */</font></tt><br>
<tt><font size="2">	 &nbsp; &nbsp; &nbsp;switch(op)</font></tt><br>
<tt><font size="2">		{</font></tt><br>
<tt><font size="2">			/* run the job assignment */</font></tt><br>
<tt><font size="2">			case RUNOP:</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 		AddInSetStatusText(&quot;Performing 2 Minute operation&quot;);</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 		AddInLogMessageText(&quot;THREADS: Begin 2 Minute Database &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 				Summary:&quot;,NOERROR);</font></tt><br>
<br>
<font size="4" face="Times New Roman">               </font><tt><font size="2">&nbsp;			/* Do not read note until the database is no longer opened 	</font></tt><br>
<tt><font size="2">				 &nbsp; by one of the other threads.</font></tt><br>
<tt><font size="2">		 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;*/</font></tt><br>
<br>
<font size="4" face="Times New Roman">               			</font><tt><font size="2">while ( filelock ) </font></tt><br>
<tt><font size="2">	 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;		SLEEP (50L); &nbsp; /* sleep length based on typical lock 								 &nbsp;time */</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 		/* Lock and reopen the database from the global 						handle. */</font></tt><br>
<tt><font size="2">&nbsp; &nbsp;</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;			filelock++; &nbsp; &nbsp; &nbsp; &nbsp;</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;			if (error = NSFDbReopen (db_handle, &amp;read_handle))</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;			{</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;				AddInLogMessageText(&quot;Error opening database.&quot;, </font></tt><br>
<tt><font size="2">	 &nbsp; &nbsp;	 &nbsp; 					 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;ERR(error));</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;				filelock--;</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;				goto Done;</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;			}</font></tt><br>
<font size="4" face="Times New Roman">   </font><br>
<font size="4" face="Times New Roman">         </font><tt><font size="2">&nbsp;				/* Call NSFSearch to find all data notes in the 						database. */</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;			if (error = NSFSearch (</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 			read_handle,	/* database handle */</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 			NULLHANDLE,		/* selection formula(all)*/</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 			NULL,	/* title of view in selection formula */</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 			0, &nbsp; 			/* search flags */</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 			NOTE_CLASS_DOCUMENT, &nbsp;/* note class to find */</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 			NULL, &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; /* starting date (unused) */</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 			ReadOpNote,/*action routine for notes found*/</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 			&amp;read_handle, /* argument to action routine */</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 			NULL)) /* returned ending date (unused) */</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;			{</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;				NSFDbClose (read_handle);</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;				AddInLogMessageText(&quot;Error reading notes from 	</font></tt><br>
<tt><font size="2">						database.&quot;, ERR(error));</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;				filelock--;</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;				goto Done;</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;			}</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;			/* Close and unlock the database. */</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; </font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;			if (error = NSFDbClose (read_handle))</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;			{</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;				AddInLogMessageText(&quot;Error closing database.&quot;, </font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;	ERR(error));</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;				filelock--;</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;				goto Done;</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;			}</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;			filelock--;</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;			AddInLogMessageText(&quot;THREADS: 2 Minute operation </font></tt><br>
<tt><font size="2">				complete.&quot;, NOERROR);</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 			AddInSetStatusText(&quot;2 Minute operation Idle&quot;);</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;			break;</font></tt><br>
<tt><font size="2">			</font></tt><br>
<tt><font size="2">			/* quit the job */</font></tt><br>
<tt><font size="2">			case QUITOP:</font></tt><br>
<tt><font size="2">				goto Done;</font></tt><br>
<tt><font size="2">		 &nbsp; &nbsp;		break;</font></tt><br>
<tt><font size="2">			</font></tt><br>
<tt><font size="2">		 &nbsp;	default:</font></tt><br>
<tt><font size="2">				error = op;</font></tt><br>
<tt><font size="2">	 &nbsp; &nbsp; &nbsp; &nbsp;		break;</font></tt><br>
<tt><font size="2">		}</font></tt><br>
<tt><font size="2">	}</font></tt><br>
<tt><font size="2">	else if (ERR_MQ_TIMEOUT == error)</font></tt><br>
<tt><font size="2">	{</font></tt><br>
<tt><font size="2">		error = NOERROR;</font></tt><br>
<tt><font size="2">	}</font></tt><br>
<tt><font size="2">&nbsp; &nbsp;</font></tt><br>
<tt><font size="2">&nbsp; &nbsp;} &nbsp; /* End of main task loop. */</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp;/* We get here when the server notifies us that it is time to terminate. <br>
 &nbsp; &nbsp; &nbsp;Clean up anything we have been doing. <br>
 &nbsp; &nbsp;*/</font></tt><br>
<br>
<tt><font size="2">Done:<br>
 &nbsp; &nbsp;AddInLogMessageText(&quot;THREADS: Ending 2 Minute operation thread.&quot;,NOERROR);<br>
 &nbsp; &nbsp;AddInSetStatusText(&quot;Exiting 2 Minute operation&quot;);</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp;/* Terminate Notes thread, decrement semaphore count, and end OS thread */</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; NotesTermThread (); &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; <br>
 &nbsp; &nbsp;semaphore--;<br>
 &nbsp; &nbsp;_endthread();<br>
} </font></tt><br>
<br>
<tt><font size="2">/************************************************************************</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; FUNCTION: &nbsp; ReadOpNote</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; PURPOSE: &nbsp; &nbsp;Local function called by the operation thread routines to <br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;read and print out all the notes from the sample database.<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;Assumes that file locks are in place for local database.</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; This routine is called by NSFSearch for each note that <br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;matches the selection criteria (in this case, all the notes).</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; INPUTS:<br>
 &nbsp; &nbsp; &nbsp; &nbsp;The first argument to this function is the optional argument<br>
 &nbsp; &nbsp; &nbsp; &nbsp;that we supplied when we called NSFSearch.</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; The second argument is supplied by NSFSearch. It is<br>
 &nbsp; &nbsp; &nbsp; &nbsp;a structure of information about the note that was found.</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; The third argument is also supplied by NSFSearch and is<br>
 &nbsp; &nbsp; &nbsp; &nbsp;the summary buffer for this note. </font></tt><br>
<br>
<br>
<tt><font size="2">*************************************************************************/</font></tt><br>
<br>
<tt><font size="2">STATUS LNPUBLIC ReadOpNote ( VOID *read_handle,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;SEARCH_MATCH *search_info,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;ITEM_TABLE *summary_info)<br>
{</font></tt><br>
<br>
<tt><font size="2">/* Local data declarations. */</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; STATUS &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;error;<br>
 &nbsp; &nbsp;char &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;field_text[64]; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* contents of a AddIn_Text field */<br>
 &nbsp; &nbsp;WORD &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;field_len; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; /* length of field */<br>
 &nbsp; &nbsp;char &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;msg_text[80]; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* add-in message string */<br>
 &nbsp; &nbsp;SEARCH_MATCH &nbsp; &nbsp;SearchMatch; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; /* local copy of search match */ &nbsp;</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; memcpy ((char*)(&amp;SearchMatch), (char *)search_info, sizeof(SEARCH_MATCH));</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; /* Skip this note if it does not really match the search criteria (it is<br>
 &nbsp; &nbsp; * now deleted or modified). &nbsp;This is not necessary for full searches,<br>
 &nbsp; &nbsp; * but is shown here in case a starting date was used in the search. <br>
 &nbsp; &nbsp; */</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; if (!(SearchMatch.SERetFlags &amp; SE_FMATCH))<br>
 &nbsp; &nbsp; &nbsp; &nbsp;return (NOERROR);</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; /* Open the note. */</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; if (error = NSFNoteOpen (<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;*(DBHANDLE *)read_handle, &nbsp; &nbsp; &nbsp; /* database handle */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;SearchMatch.ID.NoteID, &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* note ID */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;0, &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* open flags */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&amp;note_handle)) &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* note handle (return) */<br>
 &nbsp; &nbsp; &nbsp; <br>
 &nbsp; &nbsp; &nbsp; &nbsp;return (ERR(error));</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; /* Get the note text item. */</font></tt><br>
<br>
<tt><font size="2">... &lt;missing code&gt;</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; /* Build message text: note ID + field text. */</font></tt><br>
<br>
<tt><font size="2">... &lt;missing code&gt;</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; /* Display the note information message. */</font></tt><br>
<br>
<tt><font size="2">... &lt;missing code&gt;</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; /* Close the note. */</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; if (error = NSFNoteClose (note_handle))<br>
 &nbsp; &nbsp; &nbsp; &nbsp;return (ERR(error));</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; /* End of subroutine. */</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; return (NOERROR);<br>
}</font></tt>
---
