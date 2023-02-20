##### Chapter 9-8
##### Events

Event is a real-time indication that something interesting has happened.  It can be produced from a user program, or from a Domino server program.  This chapter defines some event terminologies, discusses several API event functions, ways to generate and to poll a user-defined event notification, and ways to capture the event notifications generated from the Domino server programs.<br>
<br>
<b><font size="5" color="#000080">Event Terminologies</font></b><br>
<br>
<b>Event</b>: In this <i>User Guide</i><i>,</i>a signal from one server add-in program to another, usually indicating that something of interest has occurred. <br>
<br>
<b>Event Queue</b>: The queue in which the signal is placed and from which the signal is read.<br>
<br>
<b>Event Producer</b>: An add-in task that generates the event, placing it on the queue.<br>
<br>
<b>Event Consumer</b>: An add-in task that removes the event from the event queue, acting on it as appropriate.<br>
<br>
<b>Event Type and Event Severity</b>: Each event is defined as being of a certain &quot;type&quot; - for example, a mail type of event or a security type of event. For a list of valid event type names, see the definition of EVT_xxx in the <i>Reference.</i>Each event is also defined as being of a certain &quot;severity&quot; - for instance, indicating a fatal condition. For a list of valid event severity names, see the definition of SEV_xxx in the <i>Reference.</i>Since each combination of type and severity defines a different kind of event, you can define a large number of distinct events.<br>
 <br>
<b><font size="5" color="#000080">Event Function Calls</font></b><br>
 <br>
Several API functions, described below, are specific to events. For demonstrations of their usage, see the discussions of the CONSUME and PRODUCE sample code below.<br>
<br>
<b><font size="4" color="#000080">EventQueueAlloc</font></b><br>
EventQueueAlloc allocates memory for an event queue and names the queue. It is called by an event consumer to create a queue to which an event producer may write events.<br>
<br>
<b><font size="4" color="#000080">EventQueueFree</font></b><br>
EventQueueFree deallocates the memory associated with a queue, destroying it. An event consumer should call EventQueueFree when the consumer is no longer interested in receiving events from<font color="#FF0000"> </font>that queue.<br>
<br>
<font size="4" color="#000080">E</font><b><font size="4" color="#000080">ventRegisterEventRequest</font></b><br>
An event consumer calls<font color="#FF0000"> </font>EventRegisterEventRequest to specify to the HCL Domino Server the name of the event queue it will poll, as well as the type and severity of events in which it is interested. You must call EventRegisterEventRequest for each unique combination of event type and event severity in which the consumer is interested.<br>
<br>
This function also allows the consumer to specify a user<font color="#FF0000"> </font>name or database name to associate with each type/severity of event. After an event is consumed, the consumer may call EventGetDestName to retrieve this name and then use it as appropriate -- for instance, mailing a message to the specified user or logging the event in the specified database.<br>
<br>
<b><font size="4" color="#000080">EventDeregisterEventRequest</font></b><br>
EventDeregisterEventRequest indicates to the server that an event consumer is no longer interested in events of a certain type and severity. You must call it once for each distinct type/severity combination.<br>
  <br>
<b><font size="4" color="#000080">EventQueuePut</font></b><br>
An event producer calls EventQueuePut to place an event of a specific type and severity on the specified event queue. An event producer may pass user-defined data specific to this event. For more details on event-specific data, see the definition of EVENT_DATA.<br>
<br>
<b><font size="4" color="#000080">EventQueueGet</font></b><br>
An event consumer calls EventQueueGet to check a specified queue for events. The function is usually called in the main AddInIdle loop. If there are no events in the queue, the function returns the error code ERR_EVTQUEUE_EMPTY. If the functions returns NOERROR, it removes an event from the queue, and returns a handle to an EVENT_DATA data structure.<br>
<br>
<b><font size="4" color="#000080">EventGetDestName</font></b><br>
An event consumer calls EventGetDestName to retrieve the user name or database name that was specified in the call to EventRegisterEventRequest.<br>
<br>
<br>
<b><font size="5" color="#000080">User-Defined Event Notification</font></b><br>
<br>
User-defined events allow one server add-in task to notify another that something has happened. This section examines some code fragments from the sample programs CONSUME and PRODUCE that demonstrate the functions. The two programs are in the subdirectory samples\server\events.<br>
<br>
<b><font color="#000080">The CONSUME Sample Program</font></b><br>
<br>
The sample program CONSUME is an event consumer. It first creates an event queue with the specified name and tells the server to notify it of events of type TYPE_MISC and severity SEV_NORMAL. <br>
<br>

<table width="100%" border="1">
<tr valign="top"><td width="100%">
<ul><b>consume.c:  Creating an Event Queue and Registering Events</b></ul>
</td></tr>
</table>
<tt><font size="2">/*<br>
 * &nbsp;Create the event queue and specify that we are interested in events<br>
 * &nbsp;of type EVT_MISC and of severity SEV_NORMAL.<br>
 */</font></tt><br>
<br>
<tt><font size="2">if (sError = EventQueueAlloc(QueueName))<br>
 &nbsp; &nbsp;return (ERR(sError));<br>
 &nbsp; <br>
if (sError = EventRegisterEventRequest(EVT_MISC,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; SEV_NORMAL,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; QueueName,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; InputDestName))<br>
 &nbsp; &nbsp;return (ERR(sError));</font></tt><br>
<br>
<br>
The main loop of the program calls EventQueueGet to see if an event of this type has occurred. If so, it processes the data returned with the event. Note that the format of the event-specific data is entirely up to the designer of the consumer and producer tasks. In this sample program, the event-specific data is simply a character string containing the date and time that the event was generated. The program reads the character string and logs it. It also calls EventGetDestName to get the name of the user or database that was specified for this event when the event was registered. It doesn't do anything with this name,  but a consumer could make use of this name -- for instance, by mailing a message to the specified user or logging the event in the specified database.<br>
<br>

<table width="100%" border="1">
<tr valign="top"><td width="100%">
<ul><b>consume.c: Consuming Events in the Event Queue</b></ul>
</td></tr>
</table>
<br>
<tt><font size="2">&nbsp; &nbsp;while (!AddInIdle())<br>
 &nbsp; {</font></tt><br>
<tt><font size="2">&nbsp; &nbsp;/*<br>
 &nbsp; &nbsp;* &nbsp;Check to see if there is an event we're interested in the queue.<br>
 &nbsp; &nbsp;* &nbsp;If no events in the queue, don't do anything.<br>
 &nbsp; &nbsp;*/</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp;sError = EventQueueGet(QueueName, &amp;hEventData);</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp;if (sError == ERR_EVTQUEUE_EMPTY) <br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; continue;</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp;if (sError == NOERROR)<br>
 &nbsp; &nbsp; &nbsp; {</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp;/*<br>
 &nbsp; &nbsp; &nbsp; &nbsp;* &nbsp;There is an event in the queue. &nbsp;Lock the handle returned <br>
 &nbsp; &nbsp; &nbsp; &nbsp;* &nbsp;to get the EVENT_DATA structure that is returned with the event.<br>
 &nbsp; &nbsp; &nbsp; &nbsp;* &nbsp;Copy the event-specific data (in this case, a string denoting<br>
 &nbsp; &nbsp; &nbsp; &nbsp;* &nbsp;the time the event occurred) into a local buffer, terminate the<br>
 &nbsp; &nbsp; &nbsp; &nbsp;* &nbsp;string with a NULL, and log an appropriate message.<br>
 &nbsp; &nbsp; &nbsp; &nbsp;*<br>
 &nbsp; &nbsp; &nbsp; &nbsp;* &nbsp;Also, call EventGetDestName to get the user or database name <br>
 &nbsp; &nbsp; &nbsp; &nbsp;* &nbsp;assigned to this event by the call to EventRegisterEventRequest.<br>
 &nbsp; &nbsp; &nbsp; &nbsp;* &nbsp;This program doesn't do anything with the name - the<br>
 &nbsp; &nbsp; &nbsp; &nbsp;* &nbsp;function is called for demonstration purposes only.<br>
 &nbsp; &nbsp; &nbsp; &nbsp;*/</font></tt><br>
<br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;pBuf = OSLockObject(hEventData);<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; pEventData = (EVENT_DATA far *)pBuf;<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; memmove(DataBuf, <br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &amp;pEventData-&gt;EventSpecificData,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; pEventData-&gt;EventDataLength);<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; DataBuf[pEventData-&gt;EventDataLength] = '\0'; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;sprintf(MessageBuf,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;CONSUME consumed an event at %s&quot;,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; DataBuf);</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;AddInLogMsg(ADDIN_MSG_FMT, MessageBuf);</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;bDestNameReturned = EventGetDestName(EVT_MISC,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;SEV_NORMAL,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;QueueName,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;OutputDestName,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;sizeof(OutputDestName));</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp;/*<br>
 &nbsp; &nbsp; &nbsp; &nbsp;* &nbsp;Here, the event consumer could do something with the name<br>
 &nbsp; &nbsp; &nbsp; &nbsp;* &nbsp;returned by EventGetDestName. If a database name was specified<br>
 &nbsp; &nbsp; &nbsp; &nbsp;* &nbsp;when the event was registered, the consumer could update the<br>
 &nbsp; &nbsp; &nbsp; &nbsp;* &nbsp;database appropriately. &nbsp;If a user name was specified during <br>
 &nbsp; &nbsp; &nbsp; &nbsp;* &nbsp;registration, the event consumer could send mail to notify<br>
 &nbsp; &nbsp; &nbsp; &nbsp;* &nbsp;the user that the event occurred. &nbsp;Such processing is covered<br>
 &nbsp; &nbsp; &nbsp; &nbsp;* &nbsp;elsewhere, so it won't be repeated here.<br>
 &nbsp; &nbsp; &nbsp; &nbsp;*/</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;OSUnlockObject(hEventData);<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; OSMemFree(hEventData);<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<br>
 &nbsp; &nbsp; &nbsp; }<br>
 &nbsp; }<br>
</font></tt><br>
<br>
When the consumer no longer wishes to receive notice of a particular event, it calls the function EventDeregisterEventRequest to indicate this to the server. Before terminating, the consumer should also call EventQueueFree in order to free up any memory the system allocated for the queue.
<table width="100%" border="1">
<tr valign="top"><td width="100%">
<ul><b>consume.c: Deregistering Events, Deallocating Event Queue</b></ul>
</td></tr>
</table>
<br>
<tt><font size="2">&nbsp; &nbsp;<br>
 &nbsp; /*<br>
 &nbsp; &nbsp;* &nbsp;Destroy the event queue.<br>
 &nbsp; &nbsp;*/<br>
</font></tt><br>
<tt><font size="2">&nbsp; &nbsp;sError = EventDeregisterEventRequest(EVT_MISC, SEV_NORMAL, QueueName); &nbsp; &nbsp;<br>
 &nbsp; EventQueueFree(QueueName);</font></tt><br>
<br>
<br>
<b><font color="#000080">The PRODUCE Sample Program</font></b><br>
<br>
The sample program PRODUCE is an event producer. Every minute, it creates an event of type EVT_MISC and severity SEV_NORMAL and places it on the specified event queue.  A string containing the current date and time is passed as event-specific data.<br>
<br>

<table width="100%" border="1">
<tr valign="top"><td width="100%">
<ul><b>produce.c:  Generating Events</b></ul>
</td></tr>
</table>
<br>
<br>
<tt><font size="2">&nbsp; &nbsp; while (!AddInIdle())<br>
 &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp; &nbsp;if (AddInMinutesHaveElapsed(1))<br>
 &nbsp; &nbsp; &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp; &nbsp;/*<br>
 &nbsp; &nbsp; &nbsp; &nbsp; * &nbsp;If a minute has passed, get the current time and date. &nbsp;Then<br>
 &nbsp; &nbsp; &nbsp; &nbsp; * &nbsp;generate an event of type EVT_MISC and severity SEV_NORMAL.<br>
 &nbsp; &nbsp; &nbsp; &nbsp; * &nbsp;Pass a string containing the time and date as event-specific <br>
 &nbsp; &nbsp; &nbsp; &nbsp; * &nbsp;data.<br>
 &nbsp; &nbsp; &nbsp; &nbsp; */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; <br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;OSCurrentTIMEDATE(&amp;EventTimeDate);<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;ConvertTIMEDATEToText(NULL,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;NULL,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&amp;EventTimeDate,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;EventBuffer, <br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;sizeof(EventBuffer)-1, <br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&amp;wLen);</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; sError = EventQueuePut(szQueueName,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; NULL,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; EVT_MISC,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; SEV_NORMAL,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &amp;EventTimeDate,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; TYPE_TEXT,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; wLen,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; (BYTE far *) EventBuffer);<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; <br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;AddInLogMsg(ADDIN_MSG_FMT, &quot;PRODUCE Test: Produced an event!&quot;);<br>
 &nbsp; &nbsp; &nbsp; &nbsp;}<br>
 &nbsp; &nbsp;}</font></tt><br>
<br>
<br>
<b><font size="5" color="#000080">Domino-Generated Event Notification</font></b><br>
<br>
The EVENTS4.nsf database contains event configurations which the Domino Event Monitor uses when notifying administrators about a specific event.  To capture the Domino event notification and direct it into a user-specified queue, you need to specify the relationship between the notification and the queue in the EVENTS4.nsf.<br>

<ul type="disc">
<li><u>Create a new Notification Method</u>
<ol type="1">
<li>From the Names &amp; Messages (Advanced) \ Notification Methods view of the EVENTS4.nsf, click the New Notification Method action.<br>

<li>Enter the following values in the Event Notification Method form:
<table width="100%" border="1">
<tr valign="top"><td width="28%">Item Name:</td><td width="72%">Value:</td></tr>

<tr valign="top"><td width="28%"><b>Method Description</b></td><td width="72%">Any text, for example: eventMethodTest1</td></tr>

<tr valign="top"><td width="28%"><b>Method Name</b></td><td width="72%">The name of the event queue which the consume program will be polling the notification message from</td></tr>
</table>
</ol>
</ul>

<ul type="disc">
<li><u>Create a Event Notification and direct the notification to a specific queue</u>
<ol type="1">
<li>From the Event Notification view of the EVENTS4.nsf, click the New Event Notification action.<br>

<li>From the Basics and Event tabs in the Event Notification form, select appropriate event trigger, and event notification criteria.<br>

<li>From the Action tab in the Event Notification form, choose the new Notification Method just created.</ol>

<li><u>Create a consume program to poll the notification</u><br>
The name of the message queue specified in this program should be exact the same as the Method Name specified in the EVENTS4.nsf as described above, for example: eventMethodTest1. <br>
<br>

<table width="100%" border="1">
<tr valign="top"><td width="100%">
<ul><b>consume.c: To retrieve information from EVENT_DATA</b></ul>
</td></tr>
</table>
</ul>
<font face="Courier New">  </font><br>
<tt><font size="2">&nbsp; &nbsp;while (!AddInIdle())<br>
 &nbsp; {</font></tt><br>
<tt><font size="2">&nbsp; &nbsp;/*<br>
 &nbsp; &nbsp;* &nbsp;Check to see if there is an event we're interested in the queue.<br>
 &nbsp; &nbsp;* &nbsp;If no events in the queue, don't do anything.<br>
 &nbsp; &nbsp;*/</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp;sError = EventQueueGet(QueueName, &amp;hEventData);</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp;if (sError == ERR_EVTQUEUE_EMPTY) <br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; continue;</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp;if (sError == NOERROR)<br>
 &nbsp; &nbsp; &nbsp; {</font></tt><br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;pBuf = OSLockObject ( hEventData );</tt><br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;pEventData &nbsp; = (EVENT_DATA *) pBuf;</tt><br>
<br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* Acquire ErrorCode from the EVENT_DATA structure. */</tt><br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;</tt><br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;errorcode = pEventData-&gt;ErrorCode;</tt><br>
<br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* Acquire FormatSpecifier from the EVENT_DATA structure. */</tt><br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;</tt><br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;formatspecifier = pEventData-&gt;FormatSpecifier;</tt><br>
<br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* Acquire AddIn name from the EVENT_DATA structure. */</tt><br>
<br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;memmove ( eventAddInData_Buffer, </tt><br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&amp;(pEventData-&gt;EventSpecificData),</tt><br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;pEventData-&gt;AddinNameLength );</tt><br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;eventAddInData_Buffer [ pEventData-&gt;AddinNameLength ] = '\0';</tt><br>
<br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* Acquire EventData from the EVENT_DATA structure. */</tt><br>
<br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;memmove ( eventData_Buffer,</tt><br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&amp;(pEventData-&gt;EventSpecificData) + pEventData-&gt;AddinNameLength,</tt><br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;pEventData-&gt;EventDataLength - pEventData-&gt;AddinNameLength );</tt><br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;eventData_Buffer[</tt><br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;pEventData-&gt;EventDataLength-pEventData-&gt;AddinNameLength ]='\0';</tt><br>
<br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* Acquire OriginatingServerName from the EVENT_DATA structure. */</tt><br>
<br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;memmove ( eventOriginatingServer_Buffer,</tt><br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;pEventData-&gt;OriginatingServerName,</tt><br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;MAXUSERNAME );</tt><br>
<br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* Acquire Type from the EVENT_DATA structure. */</tt><br>
<br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;type = pEventData-&gt;Type;</tt><br>
<br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* Acquire Severity from the EVENT_DATA structure. */</tt><br>
<br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;severity = pEventData-&gt;Severity;</tt><br>
<br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* Log and Print the alert message. */</tt><br>
<br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;AddInLogMessageText ( SS_ADDIN_LOG,</tt><br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 0,</tt><br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; errorcode,</tt><br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; severity,</tt><br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; type,</tt><br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; (LPSTR) eventAddInData_Buffer,</tt><br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; (LPSTR) eventOriginatingServer_Buffer,</tt><br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; formatspecifier,</tt><br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; (LPSTR) eventData_Buffer );</tt><br>
<br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;OSUnlockObject ( hEventData );</tt><br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;OSMemFree ( hEventData );</tt><tt><font size="2"><br>
 &nbsp; &nbsp; &nbsp; }<br>
 &nbsp; }</font></tt><br>

<ul type="disc">
<li><u>Load the Event Monitor (the Event server task )and the consume add-in program</u><br>
Please refer to the Server Add-In Tasks chapter (Chapter 4-4) in this manual for more information on loading the consume add-in program and the event program (be sure they are loaded in this order.)</ul>

---
