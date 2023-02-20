##### Chapter 11-1
##### Overview

<b><font size="5" color="#000080">Introduction</font></b><br>
<br>
The use of Calendar and Scheduling has grown considerably in the last decade.  Enterprise and inter-enterprise business has become dependent on rapid scheduling of events and actions using this information technology.<br>
<br>
You can schedule meetings, appointments, all day events, anniversaries, reminders, or event announcements on your Notes calendar. Some of the differences between these types of entries.
<p>
<table class="table" border="1">
<tr valign="top"><td id="d286728e54" class="entry" width="170"><b>Type</b></td><td id="d286728e57" class="entry" width="926"><b>Description</b></td></tr>

<tr valign="top"><td width="170" valign="middle">Calendar entry types </td><td width="926"><img width="1" height="1" src="../images/Overview0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td class="entry" width="170">Meeting</td><td class="entry" width="926">Schedule a meeting with others and send email invitations they can respond to (for example, accept, decline, or propose changes). </td></tr>

<tr valign="top"><td class="entry" width="170">Event Announcement</td><td class="entry" width="926">Schedule a meeting with others and send broadcast email invitations they can add to their calendars without having to respond to you.</td></tr>

<tr valign="top"><td class="entry" width="170">Appointment</td><td class="entry" width="926">Schedule time within a day in your calendar.</td></tr>

<tr valign="top"><td class="entry" width="170">All Day Event</td><td class="entry" width="926">Schedule an entire day or block of days (such as vacation time) in your calendar.</td></tr>

<tr valign="top"><td class="entry" width="170">Anniversary</td><td class="entry" width="926">Add annual events such as birthdays to your calendar. Anniversary entries repeat on the same date for 10 consecutive years beginning on the date you specify (unless you click Repeat in an anniversary entry and change its duration).</td></tr>

<tr valign="top"><td class="entry" width="170">Reminder</td><td class="entry" width="926">Remind yourself of something at a particular time.</td></tr>
</table>
<br>
<b><font size="5" color="#000080">Calendar and Scheduling API</font></b><br>
<br>
The Notes/Domino 12.0 C API Toolkit offers advanced Calendar and Scheduling capabilities.  These capabilities include the ability to create, read, update, and delete all kinds of calendar entries.  They also allow explicit scheduling actions to be performed on both calendar entries on your calendar and on workflow notices associated with calendar entries, such as accept, counter-propose, cancel, etc.  All of these capabilities automatically send out appropriate workflow notices to other users on a meeting.<br>
The specific methods that are implemented are outlined in calapi.h. This document aims to provide a written description of the API capabilities.
<p>When creating, updating, or reading calendar entries or notices, the data format accepted by the APIs is the industry standard iCalendar representation, as described in RFC 5545 (<a href="../images/Overview1.gif"><u><font color="#0000FF">../images/Overview1.gif</font></u></a>).  There are existing open source applications that aid in the creation, modification, or interpretation of iCalendar data.  To identify specific calendar entries, the iCalendar UID property is used by the API methods (see RFC 5545 section 3.8.4.7).  Some API functionality also accepts NOTEID and/or UNID as an alternate identifier.  To identify a particular instance of a recurring event, the iCalendar RECURRENCE-ID property is used by the API methods (see RFC 5545 section 3.8.4.4).
<p>The APIs work within the context of a Notes database (*.nsf) file that is assumed to have basic calendar design elements required to perform the actions, namely views that are found in the existing mail template.  There are additions to the 9.0.1 mail template which enhance the API functionality but the APIs also work against previous 8.5.x mail template versions. 
<p>The Calendar and Scheduling API consists of a subset of the functions in the HCL C API for Notes/Domino. This subset helps you create, read, update, and delete all kinds of calendar entries. Each of the Calendar and Scheduling API functions starts with the prefix &quot;Cal&quot; (for example, CalCreateEntry).<br>
<br>
<b><font size="4" color="#000080">Capabilities of the </font></b><b><font size="5" color="#000080">Calendar and Scheduling</font></b><b><font size="4" color="#000080"> API</font></b><br>
<br>
The Calendar and Scheduling API provides a complete set of functions for manipulating Calendar and Scheduling messages and are particularly useful in the context of a HCL Domino Server add-in task. Calendar and Scheduling API enable:<br>

<ul type="disc">
<li>Creating calendar entries
<li>Reading calendar entries
<li>Updating calendar entries
<li>Deleting calendar entries
<li>Performing scheduling actions on calendar entries
<li>Reading calendar notices
<li>Performing scheduling actions on calendar notices</ul>
<br>
<br>
<b><font size="4" color="#000080">Advantages of the </font></b><b><font size="4" color="#000080">Capabilities of the </font></b><b><font size="5" color="#000080">Calendar and Scheduling</font></b><b><font size="4" color="#000080"> </font></b><b><font size="4" color="#000080">API</font></b><br>
<br>
The Calendar and Scheduling API is optimized to manipulate Calendar and Scheduling messages.<br>
<br>
<b><font size="4" color="#000080">Limitations of the </font></b><b><font size="5" color="#000080">Calendar and Scheduling</font></b><b><font size="4" color="#000080"> API</font></b><br>

<ul type="disc">
<li>API does not allow you to modify more than one occurrence at a time of an existing recurring entry
<li>API does not aid in the creation, manipulation, or interpretation of iCalendar data
<li>API does not implement tasks/todos
<li>API does not read or modify data from a non-mailfile (such as a room and reservation database)
<li>API only works on databases that you have access to.  It does not, for example, return public busytime info.</ul>
<br>
<b><font size="4" color="#000080">For More About the </font></b><b><font size="5" color="#000080">Calendar and Scheduling</font></b><b><font size="4" color="#000080"> API</font></b><br>
<br>
Subsequent documents in this guide discuss Calendar and Scheduling and the Calendar and Scheduling API. Also see the <i>Reference</i> and the sample programs entryCRUD.
---
