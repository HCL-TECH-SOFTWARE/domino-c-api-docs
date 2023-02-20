##### Chapter 12-15
##### Calendar and Scheduling

<b><font size="5" color="#000080">Introduction</font></b><br>
<br>
Calendar and scheduling features are available through the C API.  This section will focus on how to add an appointment or a meeting invitation to a User's schedule, delete a scheduled event from a User's schedule and query a User's busy/free time information.  Please refer to the sample program, misc\schedule for coding details.<br>
<br>
<b><font size="5" color="#000080">Components of Calendar and Scheduling</font></b><br>

<ul type="disc">
<li><b><font size="4">Appointment:</font></b></ul>
<br>
The following items comprise an appointment note in a User's schedule maintained in the User's mail database.   <br>
<br>

<table width="100%" border="1">
<tr valign="top"><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="43%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%" bgcolor="#D2D2D2"><div align="center"><b><u>Item Name</u></b></div></td><td width="1%" bgcolor="#D2D2D2"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="43%" bgcolor="#D2D2D2"><div align="center"><b><u>Description</u></b></div></td><td width="2%" bgcolor="#D2D2D2"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%" bgcolor="#D2D2D2"><div align="center"><b><u>Constant</u></b></div></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%" bgcolor="#D2D2D2"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%" bgcolor="#D2D2D2"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="43%" bgcolor="#D2D2D2"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="2%" bgcolor="#D2D2D2"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%" bgcolor="#D2D2D2"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><b><font face="Courier New">$Alarm </font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="43%">Alarm is on</td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><b><font face="Courier New">$AlarmDescription</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="43%">Shows up when alarm rings</td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><b><font face="Courier New">$AlarmOffset</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="43%">x minutes before or after StartDateTime</td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><b><font face="Courier New">$BusyName</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="43%">Fully distinguished username of person that is busy</td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><font size="2" face="Courier New">MAIL_APPT_BUSYNAME_ITEM</font></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><b><font face="Courier New">$BusyPriority</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="43%">Tells scheduler if time is busy or free </td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><font size="2" face="Courier New">MAIL_APPT_BUSYNAME_ITEM</font></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><b><font face="Courier New">$CSVersion</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="43%"> This item is used to determine what version a cs       document was created in</td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><b><font face="Courier New">$NoPurge</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="43%">End date/time (prevents note from being purged)</td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><font size="2" face="Courier New">FIELD_NOPURGE</font></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><b><font face="Courier New">$PublicAccess</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="43%">Private or public accessible </td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><b><font face="Courier New">_ViewIcon</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="43%">Scheduled event Icon displayed</td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><b><font face="Courier New">AppointmentType</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="43%">Type of scheduled event</td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><b><font face="Courier New">apptUNID</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="43%">UNID of the scheduled event</td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><b><font face="Courier New">Body</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="43%">Detailed description of the scheduled event</td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><b><font face="Courier New">BookFreeTime</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="43%">Correspond to the &quot;Pencil in&quot; check box in the Notes UI</td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><b><font face="Courier New">CalendarDateTime</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="43%">Causes appointment to show up in Calendar View</td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><b><font face="Courier New">CHAIR</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="43%">Fully distinguished name of the mail file owner</td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><b><font face="Courier New">EndDate</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="43%">End date/time of the scheduled event</td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><b><font face="Courier New">EndDateTime</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="43%">End date/time of the scheduled event</td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><font size="2" face="Courier New">MAIL_APPT_ENDTIME_ITEM</font></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><b><font face="Courier New">EndTime</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="43%">End date/time of the scheduled event</td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><b><font face="Courier New">ExcludeFromView</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="43%">Prevents non sent appts from showing up in drafts view</td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><b><font face="Courier New">From</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="43%">Fully distinguished username</td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><font size="2" face="Courier New">MAIL_FROM_ITEM</font></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><b><font face="Courier New">Form</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="43%">What form to display</td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><font size="2" face="Courier New">FIELD_FORM</font></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><b><font face="Courier New">ORGTABLE</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="43%">Set for the scheduled event</td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><b><font face="Courier New">Principal</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="43%">Fully distinguished name of the mail file owner</td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><b><font face="Courier New">SEQUENCENUM</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="43%">Keeps the scheduled event ordered</td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><font size="2" face="Courier New">MAIL_APPT_SEQUENCE_ITEM</font></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><b><font face="Courier New">StartDate</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="43%">Start date/time of the scheduled event</td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><b><font face="Courier New">StartDateTime</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="43%">Start date/time of the scheduled event</td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><font size="2" face="Courier New">MAIL_APPT_STARTTIME_ITEM</font></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><b><font face="Courier New">StartTime</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="43%">Start date/time of the scheduled event</td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><b><font face="Courier New">Subject</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="43%">Brief description of the scheduled event</td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><font size="2" face="Courier New">MAIL_SUBJECT_ITEM</font></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="43%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>
</table>
Use NSFItemAppend<b> </b>API to add each item to the appointment note.<br>
<br>

<ul type="disc">
<li><b><font size="4">Meeting Invitation:</font></b></ul>

<ul>
<ul type="disc">
<li>Established meeting invitation note: </ul>

<ul>To create an invitation without sending the invitation notice, use:
<ul>
<ul type="disc">
<li>The items described above for creating an Appointment note, and
<li>The following items.</ul>
</ul>
</ul>
</ul>

<table width="100%" border="1">
<tr valign="top"><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="20%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="47%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="26%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="20%" bgcolor="#D2D2D2"><div align="center"><b><u>Item Name</u></b></div></td><td width="2%" bgcolor="#D2D2D2"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="47%" bgcolor="#D2D2D2"><div align="center"><b><u>Description</u></b></div></td><td width="2%" bgcolor="#D2D2D2"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="26%" bgcolor="#D2D2D2"><div align="center"><b><u>Constant</u></b></div></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="20%" bgcolor="#D2D2D2"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="2%" bgcolor="#D2D2D2"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="47%" bgcolor="#D2D2D2"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="2%" bgcolor="#D2D2D2"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="26%" bgcolor="#D2D2D2"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="20%"><b><font face="Courier New">CopyTo </font></b></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="47%">Fully distinguished name(s) of the Optional invitee(s)</td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="26%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="20%"><b><font face="Courier New">SendTo</font></b></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="47%">Fully distinguished name(s) of the Primary invitee(s)</td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="26%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="20%"><b><font face="Courier New">BlindCopyTo</font></b></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="47%">Fully distinguished name(s) of FYI invitee(s)</td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="26%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>
</table>

<ul>
<ul>Use NSFItemAppend<b> </b>API to add each item to the meeting invitation note.</ul>
</ul>
<br>

<ul>
<ul type="disc">
<li>Meeting invitation event note:</ul>

<ul>Once the meeting invitation is initiated, one or more of the following events will take place:<br>

<ul>
<ul type="disc">
<li>Meeting invitation originator <b>sends</b> the meeting invitation to invitees
<li>Invitee <b>counters </b>the meeting time
<li>Meeting invitation originator <b>re-schedules </b>the meeting
<li>Invitee <b>accepts </b>the meeting invitation
<li>Invitee <b>declines </b>the meeting invitation
<li>Invitee <b>delegate </b>the meeting invitation
<li>Meeting invitation originator <b>confirms </b>the meeting
<li>Meeting invitation originator <b>cancels </b>the meeting</ul>
</ul>
For each event, the &quot;event owner&quot; creates/updates the current message note, and sends out a responding message note.   Item to be included in either kind of the notes are:<br>
The items described above for creating an Appointment note,
The items described above for creating an established meeting invitation note, and
The following items.
<p> See the Summary of Invitation Event Note Itemssection for summarized information.  
<p>
<table width="100%" border="1">
<tr valign="top"><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="20%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="47%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="26%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="20%" bgcolor="#D2D2D2"><div align="center"><b><u>Item Name</u></b></div></td><td width="2%" bgcolor="#D2D2D2"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="47%" bgcolor="#D2D2D2"><div align="center"><b><u>Description</u></b></div></td><td width="2%" bgcolor="#D2D2D2"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="26%" bgcolor="#D2D2D2"><div align="center"><b><u>Constant</u></b></div></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="20%" bgcolor="#D2D2D2"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="2%" bgcolor="#D2D2D2"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="47%" bgcolor="#D2D2D2"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="2%" bgcolor="#D2D2D2"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="26%" bgcolor="#D2D2D2"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="20%"><font face="Courier New">$CSFlags </font></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="47%">Mainly used for repeating entries; Determines what type of repeating entry a document is.</td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="26%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="20%"><b><font face="Courier New">_ViewIcon2</font></b></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="47%">Secondary icon to display in a view column</td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="26%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="20%"><b><font face="Courier New">Delegator</font></b></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="47%">Fully distinguished name of the delegator</td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="26%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="20%"><b><font face="Courier New">Delegee</font></b></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="47%">Fully distinguished name of the person being delegated to</td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="26%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="20%"><b><font face="Courier New">FormToUse</font></b></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="47%">Only used by UI when sending a notice with additional comments</td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="26%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="20%"><b><font face="Courier New">NewEndDate</font></b></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="47%">New End date/time of the scheduled event</td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="26%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="20%"><b><font face="Courier New">NewEndTime</font></b></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="47%">New End date/time of the scheduled event</td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="26%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="20%"><b><font face="Courier New">NewStartDate</font></b></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="47%">New Start date/time of the scheduled event</td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="26%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="20%"><b><font face="Courier New">NewStartTime</font></b></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="47%">New Start date/time of the scheduled event</td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="26%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="20%"><b><font face="Courier New">NoticeType</font></b></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="47%">Type of the notice</td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="26%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="20%"><b><font face="Courier New">OptionalAttendees</font></b></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="47%">Fully distinguished name(s) of the Optional invitee(s)</td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="26%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="20%"><b><font face="Courier New">Recipients</font></b></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="47%">Complete list of invitees</td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="26%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="20%"><b><font face="Courier New">Requiredattendees</font></b></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="47%">Fully distinguished name(s) of thePrimary invitee(s) </td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="26%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="20%"><b><font face="Courier New">StatusUpdate</font></b></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="47%">Details of the event status</td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="26%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="20%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="47%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="26%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>
</table>
  Summary of Invitation Event Note Items 
The following 2 tables document different item values required for a specific meeting invitation event: Invitation, Countering, Re-scheduling, Accepting, Declining, Delegating, Cancelled and Confirmed.

<table border="1">
<tr valign="top"><td width="379"><b><sup>Legend:</sup></b>
<ul><br>
<b><sup><font size="2" color="#FF00FF">(1) </font></sup></b><sup><font size="1">denotes a note to be modified or created for the current &quot;event owner&quot; when the given event occurs.</font></sup><br>
<b><sup><font size="2" color="#008000">(2)</font></sup></b><sup><font size="2"> denotes a message note to be sent out when </font></sup><sup><font size="1">the given event occurs.</font></sup><br>
<b><sup><font size="2" color="#0000FF">(3)</font></sup></b><sup><font size="2"> denotes a message note to be sent to meeting invitation originator when the delegating event occurs.</font></sup><br>
<b><sup><font size="2" color="#00FF00">(4)</font></sup></b><sup><font size="2"> denotes a message note to be sent to delegee when the delegating event occurs.</font></sup><br>
<b><font size="2">--</font></b><sup><font size="2">                  - indicates the item is not required for the given event.</font></sup><br>
<b><i><font size="2">italic font</font></i></b><sup><font size="2"> - indicates the description of the item value.</font></sup><br>
<b><font size="2">NULL</font></b><sup><font size="2">          - indicates a NULL value.</font></sup><br>
<b><font size="2">helv font</font></b><b><sup><font size="2">   </font></sup></b><sup><font size="2">- indicates the text string of the item value.</font></sup></ul>
</td></tr>
</table>
</ul>
</ul>
<br>

<table width="100%" border="1">
<tr valign="top"><td width="24%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="12%" bgcolor="#E1E1E1"><div align="center"><b>Invita-</b><br>
<b>tion</b></div></td><td width="11%" bgcolor="#E1E1E1"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="10%" bgcolor="#E1E1E1"><div align="center"><b>Counter- ing</b></div></td><td width="11%" bgcolor="#E1E1E1"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="11%" bgcolor="#E1E1E1"><div align="center"><b>Re-</b><br>
<b>schedule</b></div></td><td width="10%" bgcolor="#E1E1E1"><div align="center"><b>Accept-</b><br>
<b>ing</b></div></td><td width="11%" bgcolor="#E1E1E1"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="24%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="12%"><div align="center"> <b><sup><font size="2"> </font></sup></b><b><sup><font size="2" color="#FF00FF">(1)</font></sup></b></div></td><td width="11%"><div align="center"> <b><sup><font size="2"> </font></sup></b><b><sup><font size="2" color="#008000">(2)</font></sup></b></div></td><td width="10%"><div align="center"> <b><sup><font size="2" color="#FF00FF">(1)</font></sup></b></div></td><td width="11%"><div align="center">  <b><sup><font size="2" color="#008000">(2)</font></sup></b></div></td><td width="11%"><div align="center"> <sup><font size="2"> </font></sup><b><sup><font size="2" color="#008000">(2)</font></sup></b></div></td><td width="10%"><div align="center"><b><sup><font size="2" color="#FF00FF">(1)</font></sup></b></div></td><td width="11%"><div align="center"> <b><sup><font size="2" color="#008000">(2)</font></sup></b></div></td></tr>

<tr valign="top"><td width="24%">$BusyName</td><td width="12%"><i>current  user</i></td><td width="11%">--</td><td width="10%"><i>current user</i></td><td width="11%">--</td><td width="11%">--</td><td width="10%"><i>current user</i></td><td width="11%">--</td></tr>

<tr valign="top"><td width="24%">$BusyPriority</td><td width="12%">1</td><td width="11%">--</td><td width="10%">2</td><td width="11%">--</td><td width="11%">--</td><td width="10%">1</td><td width="11%">--</td></tr>

<tr valign="top"><td width="24%">$CSFlags</td><td width="12%">--</td><td width="11%">--</td><td width="10%">--</td><td width="11%">w</td><td width="11%">w</td><td width="10%">--</td><td width="11%">w</td></tr>

<tr valign="top"><td width="24%">$REF</td><td width="12%">--</td><td width="11%">--</td><td width="10%">--</td><td width="11%"><i>yes</i></td><td width="11%"><i>yes</i></td><td width="10%">--</td><td width="11%"><i>yes</i></td></tr>

<tr valign="top"><td width="24%">_ViewIcon</td><td width="12%">158</td><td width="11%">133</td><td width="10%">39</td><td width="11%">39</td><td width="11%">33</td><td width="10%">158</td><td width="11%">83</td></tr>

<tr valign="top"><td width="24%">_ViewIcon2</td><td width="12%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="11%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="10%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="11%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="11%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="10%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="11%">11</td></tr>

<tr valign="top"><td width="24%">CopyTo</td><td width="12%">NULL</td><td width="11%"><i>yes</i></td><td width="10%"><i>yes</i></td><td width="11%"><i>yes</i></td><td width="11%"><i>yes</i></td><td width="10%"><i>yes</i></td><td width="11%"><i>yes</i></td></tr>

<tr valign="top"><td width="24%">Delegator</td><td width="12%">--</td><td width="11%">--</td><td width="10%">--</td><td width="11%">--</td><td width="11%">--</td><td width="10%">--</td><td width="11%">--</td></tr>

<tr valign="top"><td width="24%">Delegee</td><td width="12%">--</td><td width="11%">--</td><td width="10%"><i>yes</i></td><td width="11%">--</td><td width="11%">--</td><td width="10%">--</td><td width="11%">--</td></tr>

<tr valign="top"><td width="24%">Form</td><td width="12%">appointment</td><td width="11%">notice</td><td width="10%">notice</td><td width="11%">notice</td><td width="11%">notice</td><td width="10%">notice</td><td width="11%">appointment</td></tr>

<tr valign="top"><td width="24%">FormToUse</td><td width="12%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="11%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="10%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="11%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="11%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="10%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="11%">notice</td></tr>

<tr valign="top"><td width="24%">NewEndDate</td><td width="12%">--</td><td width="11%">--</td><td width="10%"><i>yes</i></td><td width="11%"><i>yes</i></td><td width="11%">--</td><td width="10%">--</td><td width="11%">--</td></tr>

<tr valign="top"><td width="24%">NewEndTime</td><td width="12%">--</td><td width="11%">--</td><td width="10%"><i>yes</i></td><td width="11%"><i>yes</i></td><td width="11%">--</td><td width="10%">--</td><td width="11%">--</td></tr>

<tr valign="top"><td width="24%">NewStartDate</td><td width="12%">--</td><td width="11%">--</td><td width="10%"><i>yes</i></td><td width="11%"><i>yes</i></td><td width="11%">--</td><td width="10%">--</td><td width="11%">--</td></tr>

<tr valign="top"><td width="24%">NewStartTime</td><td width="12%">--</td><td width="11%">--</td><td width="10%"><i>yes</i></td><td width="11%"><i>yes</i></td><td width="11%">--</td><td width="10%">--</td><td width="11%">--</td></tr>

<tr valign="top"><td width="24%">NoticeType</td><td width="12%">--</td><td width="11%">I</td><td width="10%">T</td><td width="11%">T</td><td width="11%">U</td><td width="10%">A</td><td width="11%">A</td></tr>

<tr valign="top"><td width="24%">Recipients</td><td width="12%"><i>yes</i></td><td width="11%">--</td><td width="10%">--</td><td width="11%">--</td><td width="11%">--</td><td width="10%">--</td><td width="11%">--</td></tr>

<tr valign="top"><td width="24%">SEQUENCENUM</td><td width="12%">1</td><td width="11%">1</td><td width="10%">1</td><td width="11%">1</td><td width="11%">3</td><td width="10%">1</td><td width="11%">3</td></tr>

<tr valign="top"><td width="24%">StatusUpdate</td><td width="12%">--</td><td width="11%">--</td><td width="10%"><i>yes</i></td><td width="11%">-</td><td width="11%">-</td><td width="10%"><i>yes</i></td><td width="11%"><i>yes</i></td></tr>

<tr valign="top"><td width="24%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="12%"><div align="center"><b><sup><font size="2" color="#FF00FF">(1)</font></sup></b></div></td><td width="11%"><div align="center"> <b><sup><font size="2" color="#008000">(2)</font></sup></b></div></td><td width="10%"><div align="center"><sup><font size="2"> </font></sup><b><sup><font size="2" color="#FF00FF">(1)</font></sup></b></div></td><td width="11%"><div align="center"><sup><font size="2"> </font></sup><b><sup><font size="2" color="#008000">(2)</font></sup></b></div></td><td width="11%"><div align="center"> <sup><font size="2"> </font></sup><b><sup><font size="2" color="#008000">(2)</font></sup></b></div></td><td width="10%"><div align="center"> <b><sup><font size="2" color="#FF00FF">(1)</font></sup></b></div></td><td width="11%"><div align="center"> <sup><font size="2"> </font></sup><b><sup><font size="2" color="#008000">(2)</font></sup></b></div></td></tr>

<tr valign="top"><td width="24%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="12%" bgcolor="#E1E1E1"><div align="center"><b>Invita-</b><br>
<b>tion</b></div></td><td width="11%" bgcolor="#E1E1E1"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="10%" bgcolor="#E1E1E1"><div align="center"><b>Counter- ing</b></div></td><td width="11%" bgcolor="#E1E1E1"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="11%" bgcolor="#E1E1E1"><div align="center"><b>Re-</b><br>
<b>schedule</b></div></td><td width="10%" bgcolor="#E1E1E1"><div align="center"><b>Accept-</b><br>
<b>ing</b></div></td><td width="11%" bgcolor="#E1E1E1"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>
</table>

<table width="100%" border="1">
<tr valign="top"><td width="24%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="9%" bgcolor="#E1E1E1"><div align="center"><b>Declin- ing</b></div></td><td width="11%" bgcolor="#E1E1E1"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="10%" bgcolor="#E1E1E1"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="11%" bgcolor="#E1E1E1"><div align="center"><b>Delegat- ing</b></div></td><td width="11%" bgcolor="#E1E1E1"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="12%" bgcolor="#E1E1E1"><div align="center"><b>Cancelled</b></div></td><td width="11%" bgcolor="#E1E1E1"><div align="center"><b>Confirm- ed</b></div></td></tr>

<tr valign="top"><td width="24%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="9%"><div align="center"><sup><font size="2"> </font></sup><b><sup><font size="2" color="#FF00FF">(1)</font></sup></b></div></td><td width="11%"><div align="center"> <sup><font size="2"> </font></sup><b><sup><font size="2" color="#008000">(2)</font></sup></b></div></td><td width="10%"><div align="center"> <sup><font size="2"> </font></sup><b><sup><font size="2" color="#FF00FF">(1)</font></sup></b></div></td><td width="11%"><div align="center"> <b><sup><font size="2" color="#0000FF">(3)</font></sup></b></div></td><td width="11%"><div align="center"> <sup><font size="2"> </font></sup><b><sup><font size="2" color="#00FF00">(4)</font></sup></b></div></td><td width="12%"><div align="center"><b><font color="#008000"> </font></b><b><sup><font size="2" color="#008000">(2)</font></sup></b></div></td><td width="11%"><div align="center"> <b><font color="#008000"> </font></b><b><sup><font size="2" color="#008000">(2)</font></sup></b></div></td></tr>

<tr valign="top"><td width="24%">$BusyName</td><td width="9%"><i>current  user</i></td><td width="11%">--</td><td width="10%"><i>current user</i></td><td width="11%">--</td><td width="11%">--</td><td width="12%"><i>--</i></td><td width="11%">--</td></tr>

<tr valign="top"><td width="24%">$BusyPriority</td><td width="9%">2</td><td width="11%">--</td><td width="10%">2</td><td width="11%">--</td><td width="11%">--</td><td width="12%">--</td><td width="11%">--</td></tr>

<tr valign="top"><td width="24%">$CSFlags</td><td width="9%">--</td><td width="11%">w</td><td width="10%">--</td><td width="11%">w</td><td width="11%">w</td><td width="12%">w</td><td width="11%">w</td></tr>

<tr valign="top"><td width="24%">$REF</td><td width="9%">--</td><td width="11%"><i>yes</i></td><td width="10%">--</td><td width="11%"><i>yes</i></td><td width="11%"><i>--</i></td><td width="12%"><i>yes</i></td><td width="11%"><i>yes</i></td></tr>

<tr valign="top"><td width="24%">_ViewIcon</td><td width="9%">84</td><td width="11%">84</td><td width="10%">84</td><td width="11%">84</td><td width="11%">133</td><td width="12%">81</td><td width="11%">10</td></tr>

<tr valign="top"><td width="24%">_ViewIcon2</td><td width="9%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="11%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="10%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="11%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="11%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="12%">11</td><td width="11%">11</td></tr>

<tr valign="top"><td width="24%">CopyTo</td><td width="9%"><i>yes</i></td><td width="11%"><i>yes</i></td><td width="10%"><i>yes</i></td><td width="11%"><i>yes</i></td><td width="11%"><i>yes</i></td><td width="12%"><i>yes</i></td><td width="11%"><i>yes</i></td></tr>

<tr valign="top"><td width="24%">Delegator</td><td width="9%">--</td><td width="11%">--</td><td width="10%">--</td><td width="11%">--</td><td width="11%"><i>yes</i></td><td width="12%">--</td><td width="11%">--</td></tr>

<tr valign="top"><td width="24%">Delegee</td><td width="9%"><i>yes</i></td><td width="11%">--</td><td width="10%"><i>yes</i></td><td width="11%"><i>yes</i></td><td width="11%">--</td><td width="12%">--</td><td width="11%">--</td></tr>

<tr valign="top"><td width="24%">Form</td><td width="9%">notice</td><td width="11%">notice</td><td width="10%">notice</td><td width="11%">notice</td><td width="11%">notice</td><td width="12%">(ReplyNotice)</td><td width="11%">notice</td></tr>

<tr valign="top"><td width="24%">FormToUse</td><td width="9%">--</td><td width="11%">--</td><td width="10%">--</td><td width="11%">--</td><td width="11%">--</td><td width="12%">notice</td><td width="11%">notice</td></tr>

<tr valign="top"><td width="24%">NewEndDate</td><td width="9%"><i>yes</i></td><td width="11%">--</td><td width="10%"><i>yes</i></td><td width="11%">--</td><td width="11%">--</td><td width="12%">--</td><td width="11%">--</td></tr>

<tr valign="top"><td width="24%">NewEndTime</td><td width="9%"><i>yes</i></td><td width="11%">--</td><td width="10%"><i>yes</i></td><td width="11%">--</td><td width="11%">--</td><td width="12%">--</td><td width="11%">--</td></tr>

<tr valign="top"><td width="24%">NewStartDate</td><td width="9%"><i>yes</i></td><td width="11%">--</td><td width="10%"><i>yes</i></td><td width="11%">--</td><td width="11%">--</td><td width="12%">--</td><td width="11%">--</td></tr>

<tr valign="top"><td width="24%">NewStartTime</td><td width="9%"><i>yes</i></td><td width="11%">--</td><td width="10%"><i>yes</i></td><td width="11%">--</td><td width="11%">--</td><td width="12%">--</td><td width="11%">--</td></tr>

<tr valign="top"><td width="24%">NoticeType</td><td width="9%">R</td><td width="11%">R</td><td width="10%">D</td><td width="11%">D</td><td width="11%">L</td><td width="12%">C</td><td width="11%">N</td></tr>

<tr valign="top"><td width="24%">Recipients</td><td width="9%">--</td><td width="11%">--</td><td width="10%">--</td><td width="11%">--</td><td width="11%">--</td><td width="12%">--</td><td width="11%">--</td></tr>

<tr valign="top"><td width="24%">SEQUENCENUM</td><td width="9%">1</td><td width="11%">1</td><td width="10%">1</td><td width="11%">1</td><td width="11%">1</td><td width="12%">3</td><td width="11%">3</td></tr>

<tr valign="top"><td width="24%">StatusUpdate</td><td width="9%"><i>yes</i></td><td width="11%">--</td><td width="10%"><i>yes</i></td><td width="11%">--</td><td width="11%">--</td><td width="12%"><i>yes</i></td><td width="11%"><i>yes</i></td></tr>

<tr valign="top"><td width="24%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="9%"><div align="center"> <sup><font size="2"> </font></sup><b><sup><font size="2" color="#FF00FF">(1)</font></sup></b></div></td><td width="11%"><div align="center"><sup><font size="2"> </font></sup><b><sup><font size="2" color="#008000">(2)</font></sup></b></div></td><td width="10%"><div align="center"> <b><sup><font size="2" color="#FF00FF">(1)</font></sup></b></div></td><td width="11%"><div align="center">  <b><sup><font size="2" color="#0000FF">(3)</font></sup></b></div></td><td width="11%"><div align="center"><sup><font size="2"> </font></sup><b><sup><font size="2" color="#00FF00">(4)</font></sup></b></div></td><td width="12%"><div align="center"><b><sup><font size="2" color="#008000">(2)</font></sup></b></div></td><td width="11%"><div align="center"><sup><font size="2"> </font></sup><b><sup><font size="2" color="#008000">(2)</font></sup></b></div></td></tr>

<tr valign="top"><td width="24%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="9%" bgcolor="#E1E1E1"><div align="center"><b>Declin- ing</b></div></td><td width="11%" bgcolor="#E1E1E1"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="10%" bgcolor="#E1E1E1"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="11%" bgcolor="#E1E1E1"><div align="center"><b>Delegat- ing</b></div></td><td width="11%" bgcolor="#E1E1E1"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="12%" bgcolor="#E1E1E1"><div align="center"><b>Cancelled</b></div></td><td width="11%" bgcolor="#E1E1E1"><div align="center"><b>Confirm-</b><br>
<b>ed</b></div></td></tr>
</table>
<br>
<br>
<br>
<br>
<br>
The following sections describe each of the items alphabetically.<br>
<br>
<b><font size="4" color="#000080">$Alarm</font></b><br>
The $Alarm item is of type TYPE_NUMBER and indicates the alarm is on.  Set this value to 1.<br>
<br>
<b><font size="4" color="#000080">$AlarmOffset</font></b><br>
The $AlarmOffset item is of type TYPE_NUMBER and indicates when the alarm should ring (negative = x minutes before StartDateTime or positive = x minutes after).<br>
<br>
<b><font size="4" color="#000080">$BusyName</font></b><br>
The $BusyName item is of type TYPE_TEXT and contains the fully distinguished username of the person that is busy in that timeslot (ex. CN=Jane Doe/OU=CAM/O=Lotus) .<br>
<br>
<b><font size="4" color="#000080">$BusyPriority</font></b><br>
The $BusyPriority item is of type TYPE_TEXT and tells the scheduler whether this schedule event should be considered busy or free time: <br>
<br>
&quot;<b>1</b>&quot; =  Busy Value <br>
&quot;<b>2</b>&quot; =  Not Busy     <br>
<br>
 <b><font size="4" color="#000080">$CSFlags</font></b><br>
The $CSFlags item is of type TYPE_TEXT. <br>
<br>
&quot;<b>m</b>&quot;= R5 repeat message<br>
&quot;<b>i</b>&quot;   = R5 repeat instance<br>
  <br>
<b><font size="4" color="#000080">$CSVersion</font></b><br>
The $CSVersion item is of type TYPE_TEXT.<br>
  <br>
Non existent for 4.5/4.6 documents<br>
&quot;<b>2</b>&quot; =  R5 documents<br>
<br>
<b><font size="4" color="#000080">$NoPurge</font></b><br>
The $NoPurge item is of type TYPE_TIME and contains the ending date/time.  This item prevents the note from being purged by replication before the schedule event has occurred.  Use ConvertTextToTIMEDATE for the ending time string (ex. &quot;03/16/2000 05:00 pm&quot;).
<ul>
<ul></ul>
</ul>
<b><font size="4" color="#000080">$PublicAccess</font></b><br>
The $PublicAccess item is of type TYPE_TEXT and indicates if this scheduled event can be viewed by public:<br>
<br>
&quot;<b>1</b>&quot; indicates this scheduled event can be viewed by the public<br>
<b>Skip this item</b> to mark it as Private<br>
<br>
<b><font size="4" color="#000080">_ViewIcon</font></b><br>
The _ViewIcon item is of type TYPE_NUMBER and indicates what view icon to use.  When creating an appointment, set this value to 160.  See the Summary of Invitation Event Note Itemssection for the used value when creating a meeting invitation.
<br>
<br>
<b><font size="4" color="#000080">_ViewIcon2</font></b><br>
The _ViewIcon2 item is of type TYPE_NUMBER.  It is the secondary icon to display in a view column. See the Summary of Invitation Event Note Itemssection for the used value when creating a meeting invitation.
<br>
<br>
<b><font size="4" color="#000080">AppointmentType</font></b><br>
The AppointmentType item is of type TYPE_TEXT and can be one of the following values:<br>
<br>
&quot;<b>0</b>&quot; = Personal Appointment<br>
&quot;<b>1</b>&quot; = Anniversary<br>
&quot;<b>2</b>&quot; = Event<br>
&quot;<b>3</b>&quot; = Meeting Invitation<br>
&quot;<b>4</b>&quot; = Reminder<br>
<br>
<b><font size="4" color="#000080">apptUNID </font></b><br>
The apptUNID item is of type TYPE_TEXT and contains the Universal NoteID of the scheduled event.<br>
<br>
<b><font size="4" color="#000080">Body</font></b><br>
The Body item is of type TYPE_COMPOSITE and contains the scheduled event's detailed description.<br>
<br>
<b><font size="4" color="#000080">BookFreeTime</font></b><br>
The BookFreeTime item is of type TYPE_TEXT.  It is the &quot;Pencil in&quot; check box in the Notes UI: <br>
<br>
&quot;&quot;    =  the not checked &quot;Pencil in&quot; check box<br>
&quot;1&quot;  =  the checked &quot;Pencil in&quot; check box<br>
<br>
<b><font size="4" color="#000080">CalendarDateTime</font></b><br>
The CalendarDateTime is of type TYPE_TIME and contains the start date/time of the appointment.  Adding this item to the note causes the scheduled time to show up in the calendar view.  Use ConvertTextToTIMEDATE for CalendarDateTime string (ex. &quot;03/16/2000 09:00 am&quot;).  
<ul>
<ul></ul>
</ul>
<b><font size="4" color="#000080">CHAIR</font></b><br>
The CHAIR item is of type TYPE_TEXT and contains the fully distinguished username of the owner of the mail database that created the calendar entry (ex. CN=Jane Doe/OU=CAM/O=Lotus) .<br>
<br>
<b><font size="4" color="#000080">CopyTo </font></b><br>
The CopyTo item is of type TYPE_TEXT or TYPE_TEXTLIST and contains the scheduled event's optional invitee(s).
<ul>
<ul></ul>
</ul>
<b><font size="4" color="#000080">Delegator</font></b><br>
The Delegator item is of type TYPE_TEXT and contains the fully distinguished username of the<b><font color="#000080"> </font></b>person delegating the event.<br>
<br>
<b><font size="4" color="#000080">Delegee</font></b><br>
The Delegee item is of type TYPE_TEXT and contains the fully distinguished username of the<b><font color="#000080"> </font></b>person the event is delegated to.<br>
<br>
<b><font size="4" color="#000080">EndDate </font></b><br>
The EndDate is of  type TYPE_TIME and is the end date/time of the scheduled event.  Use ConvertTextToTIMEDATE for CalendarDateTime string (ex. &quot;03/16/2000 05:00 pm&quot;).  It is mainly used in the UI to display a single instance of a value from a multi-valued EndDateTime item.  It is also used in some of the Calendar view display columns.  <br>
<br>
<b><font size="4" color="#000080">EndDateTime</font></b><br>
The EndDateTime is of type TYPE_TIME or TYPE_TIME_RANGE and contains the end date/time of the scheduled event.  Use ConvertTextToTIMEDATE for EndDateTime string (ex. &quot;03/16/2000 05:00 pm&quot;).<br>
   <br>
<b><font size="4" color="#000080">EndTime </font></b><br>
The EndTime is of  type TYPE_TIME and contains the end date/time of the scheduled event.  Use ConvertTextToTIMEDATE for CalendarDateTime string (ex. &quot;03/16/2000 05:00 pm&quot;).  It is mainly used in the UI to display a single instance of a value from a multi-valued EndDateTime item.  It is also used in some of the Calendar view display columns.    <br>
<br>
<b><font size="4" color="#000080">ExcludeFromView</font></b><br>
The ExcludeFromView item is of type TYPE_TEXT and prevents the scheduled events that are not sent from showing up in the drafts view.  The value of this item is &quot;D&quot;.<br>
<br>
<b><font size="4" color="#000080">Form</font></b><br>
The Form item is of type TYPE_TEXT and determines what form to display.  Set this value to &quot;Appointment&quot; when creating an appointment.  When creating a meeting invitation, see the Summary of Invitation Event Note Itemssectionfor the required value.<br>
<br>
<b><font size="4" color="#000080">FormToUse</font></b><br>
The FormToUse item is of type TYPE_TEXT.<br>
<br>
<b><font size="4" color="#000080">From</font></b><br>
The From item is of type TYPE_TEXT and contains the fully distinguished username who created or sent it (ex. CN=Jane Doe/OU=CAM/O=Lotus).
<ul>
<ul></ul>
</ul>
<b><font size="4" color="#000080">NewEndDate</font></b><br>
The NewEndDate is of  type TYPE_TIME and is the new end date/time of the scheduled event.  <br>
<br>
<b><font size="4" color="#000080">NewEndTime</font></b><br>
The NewEndTime is of  type TYPE_TIME and is the new end date/time of the scheduled event.  <br>
<br>
<b><font size="4" color="#000080">NewStartDate</font></b><br>
The NewStartDate is of  type TYPE_TIME and is the new start date/time of the scheduled event.  <br>
<br>
<b><font size="4" color="#000080">NewStartTime</font></b><br>
The NewStartTime is of  type TYPE_TIME and is the new start date/time of the scheduled event.  <br>
<br>
<b><font size="4" color="#000080">NoticeType</font></b><br>
The NoticeType item is of type TYPE_TEXT and can be one of the following values:<br>
<br>
&quot;<tt><b>I</b></tt>&quot; = Invitation<br>
&quot;<tt><b>U</b></tt>&quot; = Rescheduled<br>
&quot;<tt><b>C</b></tt>&quot; = Cancelled<br>
&quot;<tt><b>N</b></tt>&quot; = Confirmed<br>
&quot;<tt><b>A</b></tt>&quot; = Accepted<br>
&quot;<tt><b>R</b></tt>&quot; = Declined<br>
&quot;<tt><b>T</b></tt>&quot; = Countered<br>
&quot;<tt><b>D</b></tt>&quot; = Delegated<br>
&quot;<tt><b>L</b></tt>&quot; = Delegate Invited<br>
<br>
<b><font size="4" color="#000080">OptionalAttendees</font></b><br>
The OptionalAttendees item is of type TYPE_TEXT and contains the fully distinguished username of the Optional invitees (ex. CN=Jane Doe/OU=CAM/O=Lotus).<br>
<br>
<b><font size="4" color="#000080">ORGTABLE</font></b><br>
The ORGTABLE item is of type TYPE_TEXT.  It is set to &quot;C0&quot; for Calendar.
<ul>
<ul></ul>
</ul>
<b><font size="4" color="#000080">Principal</font></b><br>
The Principal item is of type TYPE_TEXT and contains the fully distinguished username of the owner of the mail database (ex. CN=Jane Doe/OU=CAM/O=Lotus).
<ul>
<ul></ul>
</ul>
<b><font size="4" color="#000080">Recipients</font></b><br>
The Recipients item is of type TYPE_TEXT or TYPE_TEXTLIST and contains the fully distinguished username(s) of all the invitees (ex. CN=Jane Doe/OU=CAM/O=Lotus).<br>
<br>
<b><font size="4" color="#000080">RequiredAttendees</font></b><br>
The RequiredAttendees item is of type TYPE_TEXT and contains the fully distinguished username of the Primary invitees (ex. CN=Jane Doe/OU=CAM/O=Lotus).<br>
<br>
<b><font size="4" color="#000080">SendTo </font></b><br>
The SendTo item is of type TYPE_TEXT or TYPE_TEXTLIST and contains the scheduled event's primary invitee(s).
<ul>
<ul></ul>
</ul>
<b><font size="4" color="#000080">SEQUENCENUM</font></b><br>
The SEQUENCENUM item is of type TYPE_NUMBER and keeps the scheduled events ordered.  Set this value to 1 initially.<br>
<br>
<b><font size="4" color="#000080">StartDate</font></b><br>
The StartDate is of  type TYPE_TIME and is the start date/time of the scheduled event.  Use ConvertTextToTIMEDATE for CalendarDateTime string (ex. &quot;03/16/2000 09:00 am&quot;).   It is mainly used in the UI to display a single instance of a value from a multi-valued StartDateTime item.  It is also used in some of the Calendar view display columns.      <br>
<br>
<b><font size="4" color="#000080">StartDateTime</font></b><br>
The StartDateTime is of type TYPE_TIME or TYPE_TIME_RANGE and contains the start date/time of the scheduled event.  Use ConvertTextToTIMEDATE for StartDateTime string (ex. &quot;03/16/2000 09:00 am&quot;).   
<ul></ul>
<b><font size="4" color="#000080">StartTime</font></b><br>
The StartTime is of  type TYPE_TIME and is the start date/time of the scheduled event.  Use ConvertTextToTIMEDATE for CalendarDateTime string (ex. &quot;03/16/2000 09:00 am&quot;).   It is mainly used in the UI to display a single instance of a value from a multi-valued StartDateTime item.  It is also used in some of the Calendar view display columns.      <br>
<br>
<b><font size="4" color="#000080">StatusUpdate</font></b><br>
The StatusUpdate item is of type TYPE_COMPOSITE and contains the scheduled event's status description.<br>
<br>
<b><font size="4" color="#000080">Subject</font></b><br>
The Subject item is of type TYPE_TEXT and contains the scheduled event's brief description.<br>
<br>
<br>
<br>
<b><font size="5" color="#000080">Adding a Scheduled Event to a User's Schedule</font></b><br>
<br>
This section describes how to use the C API to add an appointment  or a meeting invitation to a User's schedule.  Following are the basic steps and the corresponding API functions to perform this task.  For details, refer to the AddSchedule() routine in the <b><font size="2">SCHEDULE</font></b> sample program in the misc\schedule directory.<br>
<br>
Note:  The specified scheduled event time must be within a day's boundary.<br>
<br>
1. Open the mail database (as specified on the command line) for a specified User. (NSFDbOpen)<br>
<br>
2. Create a Note in the database (NSFNoteCreate).<br>
<br>
3. Set the NOTE CLASS to NOTE_CLASS_DOCUMENT (NSFNoteSetInfo).<br>
<br>
4. Allocate a buffer for data to copy each item's value to (OSMemAlloc).<br>
<br>
5.  Add each of the appropriate Items mentioned in the <i>Components of Calendar and Scheduling</i> section<b><font size="5" color="#000080"> </font></b>to the Note (NSFItemAppend). <br>
<br>
6. Update the Note (NSFNoteUpdate).<br>
<br>
7.  Free the data buffer (OSMemFree).<br>
<br>
8.  Close the Note and the Database.<br>
<br>
<br>
<b><font size="5" color="#000080">Deleting a Scheduled Event from a User's Schedule</font></b><br>
<br>
This section describes how to use the C API to delete a scheduled event from a User's schedule.  Following are the basic steps and the corresponding API functions to perform this task.  For details, refer to the ScheduleTask() routine in the <b><font size="2">SCHEDULE</font></b> sample program in the misc\schedule directory.<br>
<br>
1. Create an empty text list data structure. (ListAllocate).<br>
<br>
2. Add the current user to the list (ListAddEntry).<br>
<br>
3. Retrieve the user's schedule container (SchRetrieve).<br>
<br>
4. Get the first schedule in the container (SchContainer_GetFirstSchedule).<br>
<br>
5.  Get the busy time information from the schedule (Schedule_ExtractBusyTimeRange).<br>
<br>
6.  Attempt to find the &quot;scheduled event to delete&quot; time in the data returned.<br>
<br>
7.  If the time is found get the schedule list of the user (Schedule_ExtractSchedList).<br>
<br>
8. Attempt to find the scheduled event time in the schedule list returned.<br>
<br>
9.  If the entry is found delete the note. <br>
<br>
<br>
<b><font size="5" color="#000080">Query a User's Busy/Free Time Information</font></b><br>
<br>
This section describes how to use the C API to query a user's busy/free time information.  Following are the basic steps and the corresponding API functions to perform this task.  For details, refer to the ScheduleTask() routine in the <b><font size="2">SCHEDULE</font></b> sample program in the misc\schedule directory.<br>
  <br>
Note:  The specified time range may extend past a day's boundary.<br>
<br>
1. Create an empty text list data structur (ListAllocate).<br>
<br>
2. Add the current user to the list (ListAddEntry).<br>
<br>
3. Retrieve the user's schedule container (SchRetrieve).<br>
<br>
4. Get the first schedule in the container (SchContainer_GetFirstSchedule).<br>
<br>
5. Get the free time information from the schedule (Schedule_ExtractFreeTimeRange).<br>
<br>
6.  Get the busy time information from the schedule (Schedule_ExtractBusyTimeRange).
---
