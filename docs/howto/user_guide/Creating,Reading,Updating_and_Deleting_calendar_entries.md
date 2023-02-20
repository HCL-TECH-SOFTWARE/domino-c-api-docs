##### Chapter 11-2
##### Creating,Reading,Updating and Deleting calendar entries

This chapter explains how to use Calendar and Scheduling API functions to create or delete calendar entries. <br>
<br>
<b><font size="5" color="#000080">Creating calendar entries</font></b><br>
<br>
Calendar entries can be created in a database using the CalCreateEntry routine.  CalCreateEntry takes iCalendar input and attempts to create an event in a Notes/Domino database based on that iCalendar.
<p>The iCalendar input must contain data for a single calendar identifier, but that calendar entry may contain a recurrence pattern and may also contain additional VEVENTs that contain information about a specific instance.  If the iCalendar specified does not contain a UID, then a UID will be generated for the created entry and optionally returned from the create method (a DHANDLE to char* data will be populated if it was provided).
<p>When iCalendar input lists a value in ORGANIZER that matches the owner of the mailfile the entry is being created it, invitations to that calendar entry will be sent to all PARTICIPANTs listed in the iCalendar (although this can be disabled).
<p><b><font size="5" color="#000080">Reading calendar entries</font></b><br>
<br>
Information about calendar entries in a date range can be returned using the CalReadRange routines.  This will return view level information about any existing calendar entries that appear in a Notes/Domino calendar.  This is useful to get the identifiers for calendar entries within a date range, as well as to get basic information about the calendar entries that would be needed to display those entries in a calendar view.  This does not actually open any notes in the database, so it is performant but it also does not provide full information (such as the Description) in the returned iCalendar data.  There are several advanced capabilities that can be used in the ReadRangeExt method to control the data that is returned and to control paging capabilities.
<p>Information about a particular calendar entry can be read using the CalReadEntry routines.  This requires that an identifier to a particular calendar entry be passed in.  This identifier can be UID(preferred), NOTEID, or UNID.  CalReadEntry does require opening the note or notes that represent the calendar data and returns a full iCalendar representation, including things like DESCRIPTION and references to attachment data.
<p>For recurring meetings, CalReadEntry can return data about the entire series (An iCalendar VEVENT representing the recurrence pattern and series data as well as a VEVENT to represent any instances that contain data that is an exception to the base recurrence pattern or series data).  Also, the specification of a RECURRENCE-ID allows for data for only a particular occurrence to be returned.
<p>iCalendar data is returned as char* data in a DHANDLE.
<p><b><font size="5" color="#000080">Updating calendar entries</font></b><br>
<br>
Calendar entries can be updated in a database using the CalUpdateEntry routine.  CalUpdateEntry takes iCalendar input and attempts to update an event in a Notes/Domino database based on that iCalendar.  The iCalendar itself contains the identifiers in the UID and/or RECURRENCE-ID, so these do not need to be specified as arguments.
<p>Currently, only a single instance of a recurring meeting can be updated at a time.  This means that the provided iCalendar input of a recurring update must contain a VEVENT that specifies both UID and RECURRENCE-ID.  Note: Updates to more than one instance may be allowed in the future.
<p>When iCalendar input lists a value in ORGANIZER that matches the owner of the mailfile the entry is being created it, invitations to that calendar entry will be sent to all PARTICIPANTs listed in the iCalendar (although this can be disabled).
<p>Updates will fail if the iCalendar appears less recent than the existing iCalendar (based on SEQUENCE).
<p><b><font size="5" color="#000080">Deleting calendar entries</font></b><br>
<br>
Calendar entries can be deleted from a database using the CalEntryAction routine and passing in the CAL_PROCESS_DELETE action.  Unlike CalUpdateAction, CalEntryAction can act on an entire series, a particular instance, or a range (this and future).  Using CAL_PROCESS_DELETE does not send out cancellations or decline notices and removes the calendar forever.  If you are using this for meetings and want to send out cancelations or declines when you delete it, use CAL_PROCESS_SMARTDELETE instead and it will choose delete, cancel, or decline based on the calendar entry you are acting on.
<p><br>
<b><span class="domino-highlight-yellow" style="background-color: yellow"><font size="4" color="#000080">Example Using Calendar and Scheduling Functions</font></span></b><br>
<br>

<ul type="disc">
<li>Create</ul>
/*<br>
code snippet<br>
<br>
note: GetDBHdl is one of helper methods, used here only to show the usage of Calendar and Scheduling api. The code of these<br>
functions can be find in samples.<br>
*/<br>
<font size="2">#define CRLF &quot;\r\n&quot;</font><br>
<font size="2">#define ICAL_UID &quot;20121120T172345Z-JJU9O5@example.com&quot;</font><br>
<br>
<font size="2">        	char pszICalendar[] = &quot;BEGIN:VCALENDAR&quot; CRLF</font><br>
<font size="2">                                &quot;VERSION:2.0&quot; CRLF</font><br>
<font size="2">                                &quot;PRODID:-//hacksw/handcal//NONSGML v1.0//EN&quot; CRLF</font><br>
<font size="2">                                &quot;BEGIN:VEVENT&quot; CRLF</font><br>
<font size="2">                                &quot;UID:&quot; ICAL_UID CRLF</font><br>
<font size="2">                                &quot;DTSTAMP:20121120T172345Z&quot; CRLF</font><br>
<font size="2">                                &quot;DTSTART:20121120T100000Z&quot; CRLF</font><br>
<font size="2">                                &quot;DTEND:20121120T120000Z&quot; CRLF</font><br>
<font size="2">                                &quot;RRULE:FREQ=DAILY;COUNT=10&quot; CRLF</font><br>
<font size="2">                                &quot;SUMMARY:Bastille Day Party&quot; CRLF</font><br>
<font size="2">                                &quot;ORGANIZER:</font><font size="2"><a href="mailto:jsmith@example.com">mailto:jsmith@example.com</a></font><font size="2">&quot; CRLF</font><br>
<font size="2">                                &quot;ATTENDEE:</font><font size="2"><a href="mailto:jdoe@example.com">mailto:jdoe@example.com</a></font><font size="2">&quot; CRLF</font><br>
<font size="2">                                &quot;END:VEVENT&quot; CRLF</font><br>
<font size="2">                                &quot;END:VCALENDAR&quot; CRLF;</font><br>
<br>
<font size="2">       	//delayed</font><br>
<font size="2">		//start at 20121120T180000Z and end at 20121120T210000Z</font><br>
<font size="2">		char pszICalendarDelayed[] = &quot;BEGIN:VCALENDAR&quot; CRLF</font><br>
<font size="2">                                &quot;VERSION:2.0&quot; CRLF</font><br>
<font size="2">                                &quot;PRODID:-//hacksw/handcal//NONSGML v1.0//EN&quot; CRLF</font><br>
<font size="2">                                &quot;BEGIN:VEVENT&quot; CRLF</font><br>
<font size="2">                                &quot;UID:&quot; ICAL_UID CRLF</font><br>
<font size="2">                                &quot;DTSTAMP:20121120T172345Z&quot; CRLF</font><br>
<font size="2">                                &quot;DTSTART:20121120T180000Z&quot; CRLF</font><br>
<font size="2">                                &quot;DTEND:20121120T210000Z&quot; CRLF</font><br>
<font size="2">                                &quot;SUMMARY:(Delayed)Bastille Day Party&quot; CRLF</font><br>
<font size="2">                                &quot;END:VEVENT&quot; CRLF</font><br>
<font size="2">                                &quot;END:VCALENDAR&quot; CRLF;</font><br>
<br>
STATUS	error = NOERROR;<br>
<br>
char* pInputFile = &quot;mail/Test.nsf&quot;;<br>
DHANDLE hDB = NULLHANDLE;<br>
<br>
<font size="2">        	DWORD dwFlags = 0;</font><br>
<font size="2">        	MEMHANDLE hRetUID = NULL;</font><br>
<font size="2">        	char* pszRetUID = NULL;</font><br>
<br>
//step1:Get database handle;<br>
if (error = GetDBHdl(pInputFile , hDB))<br>
	return error;<br>
<br>
//step2:Create calendar entry to the database<br>
<font size="2">error = CalCreateEntry(hDB, pszICalender, dwFlags, &amp;hRetUID, NULL);</font><br>
<br>
if (error == NOERROR)<br>
	return error;<br>
<br>
<font size="2">pszRetUID = OSMemoryLock(hRetUID);</font><br>
<br>
<font size="2">        	printf(&quot;UID Returnd %s \r\n&quot;, pszRetUID);</font><br>
<br>
<font size="2">        	OSMemoryUnlock(hRetUID);</font><br>
<font size="2">        	OSMemoryFree(hRetUID);</font><br>

<ul type="disc">
<li>Read:</ul>
/*<br>
code snippet<br>
*/<br>
<br>
STATUS	error = NOERROR;<br>
<br>
<font size="2">MEMHANDLE hCalData = NULL;</font><br>
<font size="2">DWORD dwFlags = CAL_READ_INCLUDE_X_LOTUS;</font><br>
<font size="2">char* pszCalData = NULL;</font><br>
<br>
<font size="2">error = CalReadEntry(hDB, pszICalenderUID, NULL, &amp;hCalData, NULL, dwFlags, NULL);</font><br>
<br>
<font size="2">if(error != NOERROR)</font><br>
<font size="2">	return error;</font><br>
<br>
<font size="2">pszCalData = OSMemoryLock(hCalData);</font><br>
<br>
<font size="2">printf(&quot;Calender Data Returnd\r\n%s\r\n&quot;, pszCalData);</font><br>
<br>
<font size="2">OSMemoryUnlock(hCalData);</font><br>
<font size="2">OSMemoryFree(hCalData);</font><br>

<ul type="disc">
<li>Update:</ul>
/*<br>
code snippet<br>
*/<br>
<br>
STATUS	error = NOERROR;<br>
<br>
<font size="2">DWORD dwFlags = 0;</font><br>
<br>
<font size="2">error = CalUpdateEntry(hDB, </font><font size="2">pszICalendarDelayed</font><font size="2">, NULL, NULL, &quot;Delayed for some reason...&quot;, dwFlags, NULL);</font><br>

<ul type="disc">
<li>Delete</ul>
/*<br>
code snippet<br>
*/<br>
<br>
STATUS	error = NOERROR;<br>
<br>
<font size="2">DWORD dwAction = CAL_PROCESS_DELETE;</font><br>
<font size="2">DWORD dwRange = 0;</font><br>
<font size="2">PEXT_CALACTION_DATA pExtActionInfo = NULL;</font><br>
<br>
<font size="2">error = CalEntryAction(hDB, pszICalenderUID, NULL, dwAction, dwRange, &quot;Cancled&quot;, pExtActionInfo, 0, NULL);</font><br>

---
