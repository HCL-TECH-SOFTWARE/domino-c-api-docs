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
<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%" bgcolor="#D2D2D2"><div align="center"><b><u>Item Name</u></b></div></td><td width="1%" bgcolor="#D2D2D2"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%" bgcolor="#D2D2D2"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%" bgcolor="#D2D2D2"><div align="center"><b><u>Description</u></b></div></td><td width="1%" bgcolor="#D2D2D2"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%" bgcolor="#D2D2D2"><div align="center"><b><u>Constant</u></b></div></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%" bgcolor="#D2D2D2"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%" bgcolor="#D2D2D2"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%" bgcolor="#D2D2D2"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%" bgcolor="#D2D2D2"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%" bgcolor="#D2D2D2"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%" bgcolor="#D2D2D2"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">$Alarm </font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">Alarm is on.<br>
C&amp;S field that controls whether the alarm is set for the entry.<br>
This item is mutually exclusive with $AlarmDisabled, so if $AlarmDisabled is set, $Alarm must not be set.<br>
The only valid value is 1; the item should not be present otherwise.<br>
Note: When generating a repeating CS note set, this item can be in repeat parent but is not required.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">$AlarmDescription</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">Shows up when alarm rings.<br>
The text to display when the alarm triggers.<br>
Created only if Notify Me is checked, that is. if the field Alarms has value 1.<br>
Note: When generating a repeating CS note set, this item can be in repeat parent but is not required.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">$AlarmOffset</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">x minutes before or after StartDateTime.<br>
The offset, in minutes by default, from the StartTime of the entry that the alarm should be triggered. Positive offsets are after the start time; negative offsets are before the start time. This item is used only if the alarm is relative to the start time of the entry and must not exist if there is an $AlarmTime item. Its not of any use if $Alarm (or Alarm) item is not present or set properly (or if the alarm is to trigger at a specific time). Created only if Notify Me is checked, that is, the field value Alarms has value 1.<br>
Note: When generating a repeating CS note set, this item can be in repeat parent but is not required.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">$BusyName</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">Fully distinguished username of person that is busy.<br>
Indicates who the entry is for and whose busytime it should affect.<br>
Must be a single canonical name of a user or resource.<br>
This item must not be present on repeat C&amp;S parent documents. It should only appear on the actual calendar entries and not on every child document. For example, it should not appear on an Accept notice from Invitees in the Chairs mail file but it must appear on the actual calendar entries in the Invitees mail file.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><font size="2" face="Courier New">MAIL_APPT_BUSYNAME_ITEM</font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">$BusyPriority</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">Tells scheduler if time is busy or free.<br>
Indicates how the entry should be reflected in busytime and thus presented in the busytime search UI. Only one value is permitted on any given entry. If the item or a value are missing, the entry will default to Busy.<br>
Valid values are:<br>
&quot;&quot; = Busy (Only found on Notes 4.5 entries)<br>
1 = Busy (Default on calendar entries from 5.0 or later)<br>
2 = Not-busy. The entity will appear available even though there is a possible entry on the calendar. This is typically used for &quot;Pencilled-in&quot;, &quot;Tentative&quot; and &quot;Cancelled&quot; entries.<br>
The item must not be present on repeating C&amp;S parent documents. </td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><font size="2" face="Courier New">MAIL_APPT_BUSYNAME_ITEM</font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">$CSVersion</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">This item is used to determine what version a cs document was created in.<br>
Used to indicate that the entry was generated by a &quot;2nd generation&quot; C&amp;S template.<br>
Notes version 5 and later: Must be &quot;2&quot; by default.<br>
This item is not present on pre-R5-generated entries.<br>
Valid values are:<br>
0 = Pre-R5 entry<br>
2 = R5 or later</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">$NoPurge</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">End date/time (prevents note from being purged).<br>
Core: This item prevents the note from being purged by replication before the schedule event has occurred. Use ConvertTextToTIMEDATE for the ending time string. For example: ConvertTextToTIMEDATE(&quot;03/16/2000 05:00 PM&quot;).<br>
Set to latest EndDateTime in the repeat instance document. On repeat parent, set to latest EndDateTime of entire meeting set.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><font size="2" face="Courier New">FIELD_NOPURGE</font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">$PublicAccess</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">Private or public accessible.<br>
Marks the entry as a public doc. Used to make the entry public. Lotus Notes C&amp;S is based on allowing designees (for example, Administrative Assistants) to see a users calendar but not their mail file. It does this by making C&amp;S entries public. All C&amp;S entries should have this, unless the user marks the entry private (the field does not appear in such entries).<br>
Note that, if Mark Private was unchecked the first time it was saved, this item exists on both parent and response; however, if Mark Private was checked the first time it was saved and unchecked later, the item does not exist on the parent doc. </td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">_ViewIcon</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">Scheduled event Icon displayed.<br>
<font size="4">The icon to display in the calendar views for the entry.</font><br>
<font size="4">Valid values are:</font><br>
<font size="4">9 = Event</font><br>
<font size="4">10 = Confirmation or Reminder</font><br>
<font size="4">33 = Reschedule</font><br>
<font size="4">38 = Counter decline</font><br>
<font size="4">39 = Counter</font><br>
<font size="4">63 = Anniversary</font><br>
<font size="4">71 = Repaired or obsoleted entry (new for 8.5)</font><br>
<font size="4">81 = Cancel</font><br>
<font size="4">82 = Completed</font><br>
<font size="4">83 = Accept</font><br>
<font size="4">84 = Decline or Delegator response</font><br>
<font size="4">133 = Invitation or Delegate Invitation</font><br>
<font size="4">157 = Uninvited or Removed</font><br>
<font size="4">158 = Meeting</font><br>
<font size="4">160 = Appointment</font><br>
<font size="4">168 = Task </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">AppointmentType</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">Type of scheduled event.<br>
Indicates what kind of calendar entry this is.<br>
Valid values are:<br>
0 = Appointment<br>
1 = Anniversary or Personal ToDo<br>
2 = Event or Group ToDo<br>
3 = Meeting<br>
4 = Reminder</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">apptUNID</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">UNID of the scheduled event.<br>
A text version of the entry's original/actual UNID.<br>
Generally this item should be the UNID converted to text, but it could also be the iCalendar UID or some other value. This also makes iCalendar support (introduced in Notes version 6) easier since it maps directly onto iCalendar's UID property.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">Body</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">Detailed description of the scheduled event.<br>
The description of the appointment. This can be in Rich Text format or HTML format; however, auxiliary processes such as the IMAP server behave better when it is in RichText format.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">BookFreeTime</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">Correspond to the &quot;Pencil in&quot; check box in the Notes UI.<br>
User interface field.<br>
Indicates whether an entry is displayed as penciled in. It is used by the template but it is not used by the busytime system which relies on the $BusyPriority item. This should be kept in sync with the $BusyPriority item.<br>
Value is 1 if Pencil-In has been checked.<br>
Value is  otherwise.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">CalendarDateTime</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">Causes appointment to show up in Calendar View.<br>
A date &amp; time value as to when the entry should show up in the calendar view. Mainly, the presence of this item indicates that it belongs in the Calendar view and when it should appear.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">CHAIR</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">Fully distinguished name of the mail file owner.<br>
Name of the user who is chairing or organizing the entry.<br>
This should be the canonical name of the calendar owner when a meeting is created from Lotus Notes.<br>
It can be an Internet address when meeting is created from outside Notes.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">EndDate</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">End date/time of the scheduled event.<br>
The UTC date &amp; time at which the entry ends. It is derived from EndDateTime and is typically the same for non-repeating entries. In the rescheduling case, this will be the new date (&amp; time) to which the base instance is being moved.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">EndDateTime</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">End date/time of the scheduled event.<br>
The UTC date &amp; time at which the entry ends.<br>
The number of values in this item must match the number of values in the StartDateTime item.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><font size="2" face="Courier New">MAIL_APPT_ENDTIME_ITEM</font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">EndTime</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">End date/time of the scheduled event.<br>
The UTC date &amp; time the entry ends. It is derived from EndDateTime and is typically the same for non-repeating entries. This is a separate item from EndDate, even though they both share the same information, because a UI change for Notes R5 to split the combo Date/Time picker into two separate items requires two separate items.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">ExcludeFromView</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">Prevents non sent appts from showing up in drafts view.<br>
The view(s) to exclude the note from in the mail file. The values are not actual view names but some shorthand abbreviations of them (or their aliases). Valid values (for C&amp;S at least) are:<br>
A = All Documents (aka $All) view<br>
D = Drafts<br>
S = Sent</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">From</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">Fully distinguished username.<br>
Contains the username of the user who created the document. For example, when an assistant creates an invitation, the From item has their name.<br>
In contrast, the Principal item contains name of the owner of the mail database from which mail was created. Of course, the values may the same.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><font size="2" face="Courier New">MAIL_FROM_ITEM</font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">Form</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">What form to display.<br>
The name of the form used for display.<br>
The value for a room or resource document should be Resource<br>
The value for a site document is SiteProfile<br>
The value for a room reservation request should be Notice. The Rooms &amp; Resource Manager will change it to Reservation</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><font size="2" face="Courier New">FIELD_FORM</font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">ORGTABLE</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">Set for the scheduled event.<br>
Tells Lotus Organizer in which section an entry should be displayed. Since Organizer can have &gt; 1 calendar, Notes defaults to using the first one by always putting a &quot;0&quot; in the second character of this items value. The leading character is used to indicate the type of entry.<br>
Valid first character values:<br>
&quot;C0&quot; = Calendar entry<br>
&quot;T0&quot; = To Do entry<br>
&quot;H0&quot; = Calls entry<br>
&quot;P0&quot; = All Day Event / Planner entry<br>
&quot;D0&quot; = Address entry<br>
&quot;N0&quot; = Notepad entry<br>
&quot;A0&quot; = Anniversary entry</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">Principal</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">Fully distinguished name of the mail file owner.<br>
The fully distinguished username of the owner of the mail database from which mail is being created.<br>
In contrast, the From item is the name of the person, such as an assistant, creating mail. The items may be the same value.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">SEQUENCENUM</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">Keeps the scheduled event ordered.<br>
Sequence number of event notice. It is incremented when a change in start or end time occurs. When SequenceNum is changed, all the recipients must accept/decline again. Changing cosmetic things like the Subject is not grounds for increasing. Replies to a different SequenceNum are not valid and are ignored by the Chair as stale information.<br>
<br>
Initial Value: 1</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><font size="2" face="Courier New">MAIL_APPT_SEQUENCE_ITEM</font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">StartDate</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">Start date/time of the scheduled event.<br>
The UTC date (&amp; time) the entry begins.<br>
It is derived from StartDateTime and is typically the same for non-repeating entries. This is a separate item from StartTime, even though both share the same information, because a UI change for R5 to split the combo Date/Time picker into two separate items requires two separate items.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">StartDateTime</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">Start date/time of the scheduled event.<br>
The UTC date &amp; time the entry begins.<br>
The number of values in this item must match the number of values in the EndDateTime item.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><font size="2" face="Courier New">MAIL_APPT_STARTTIME_ITEM</font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">StartTime</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">Start date/time of the scheduled event.<br>
The UTC (date &amp;) time the entry begins.<br>
It is derived from StartDateTime and is typically the same for non-repeating entries. This is a separate item from StartDate, even though both share the same information, because a UI change for R5 to split the combo Date/Time picker into two separate items requires two separate items.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">Subject</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">Brief description of the scheduled event.<br>
The Subject of the notice (prefix + topic + date/time).<br>
Prefixes can be:<br>
Invitation:<br>
Accepted:<br>
Tentative:<br>
Declined:<br>
Countered:<br>
Delegated:<br>
Invitation (Delegated):<br>
Information Update - when this is an update, the Chair indicates what is being updated, such as Description has been changed.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><font size="2" face="Courier New">MAIL_SUBJECT_ITEM</font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%">                                                                       <b><font face="Courier">$AlarmDisabled</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">Created only if an alarm was enabled and then disabled by clicking on    Disable. Note that item is not created if user unchecks Notify me. Field    value is 1 when the alarm is disabled.<br>
This item is mutually exclusive with $Alarm, so if $Alarm is set,   $AlarmDisabled must not be set.<br>
Note: When generating a repeating CS note set, this item can be in repeat parent but is not required.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"> <b><font face="Courier">$AlarmMemoOptions</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">A flag indicating to whom an email notification should be sent. This item controls whether the $AlarmSendTo value is used (even if it is set). While the data type is for a string, only the first character of this item is used for determining what kind of email notice may be sent:<br>
0 = None. This indicates that no email notifications are to be sent. (In reality, field value is  if the option is not checked.)<br>
<br>
1 = Event participants only. This indicates that email notifications are sent only to the participants of record on the entry and no one else. May be obsolete.<br>
<br>
2 = Listed names. This indicates that the name(s) in $AlarmSendTo are to be sent an email notification triggering.<br>
Created only if Notify Me is checked, that is, the field Alarms has value 1. Field value is 2 if Send mail with entry title and description is checked in Alarm Settings. Note: Item is not removed if the alarm is disabled.<br>
<br>
Note: When generating a repeating CS note set, this item can be in repeat parent but is not required.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"> <b><font face="Courier">$AlarmSendTo</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">The list of users (or groups) to whom an email notification should be sent when the alarm triggers.<br>
Created only if Notify Me is checked, that is, the field value Alarms has value 1.<br>
<br>
Note: When generating a repeating CS note set, this item can be in repeat parent but is not required.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier">$AlarmSound</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">The name of the sound to play when the alarm triggers. This is not the path to a .WAV or other sound file; rather, it is the system name for a sound, at least on Win32 clients.<br>
Created only if Notify Me is checked, that is, the field value Alarms has value 1.<br>
<br>
Note: When generating a repeating CS note set, this item can be in repeat parent but is not required.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier">$AlarmUnit</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">Indicates the unit of time that the $AlarmOffset is in the default unit (if no value here is specified), in minutes.<br>
Created only if Notify Me is checked, that is, the field value Alarms has value 1.<br>
Note: When generating a repeating CS note set, this item can be in repeat parent but is not required.<br>
Valid values are:<br>
M = Minutes (Default)<br>
H = Hours<br>
D = Days<br>
Any other values are ignored, and the default is used instead.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier">$AltPrincipal</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">Alternate name of the mail file owner. Used when more than one language is present.<br>
On workflow messages, this is the alternate name for the owner of the mail file sending the notice. When there is no alternate name available, this item is set from item Principal.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier">$ApprovalList</font></b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">A list of users who are allowed to do busytime lookups on a particular user. This item is used only on calendar profiles.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier">$AvailableDays</font></b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">This item corresponds to the checkboxes allowing the user to choose which days of the week they work. The resulting item will be a list containing the days of the week that they work.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier">$CSCopyItems</font></b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">Item list used to send custom items on normal C&amp;S workflow messages. Any item names included in the text list will be copied from the current document on to all workflow messages that get sent.<br>
Usage: Add field names that you wish to add to room reservations.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier">$CSFlagsRepaired</font></b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">This appears on entries that the client has repaired/obsoleted. It is the original value of the $CSFlags item.<br>
New for 8.5</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier">$CSTrack</font></b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">Summary field  This item is used to track the flow of CS Notice items to help analyze any CS problem reports. It records each action and client version used for that action, as well as time and date stamps.<br>
<br>
Note: Customized templates or applications should add to the end of the list to help triaging any problems.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier">$CSWISL</font></b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">Watched Item Sequence List. Notes tracks when certain items are updated in the Note. When update is sent, C&amp;S code of recipient can decide if sender or recipient has new version of item.<br>
Watched items are:<br>
$S- Subject<br>
$L- Location<br>
$B- Body<br>
$R- Room<br>
$E- Resource<br>
Notes 7 additions:<br>
$M  OnlineMeeting<br>
$O  OnlinePlaceToReserve<br>
$W  MeetingPassword<br>
See also UpdateSeq</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier">$ExpandGroups</font></b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">Mail field.<br>
Used by the Mailer to decide if local people and groups should be expanded. It is 'On' by default.<br>
<br>
Valid values are:<br>
0 = Do not expand groups<br>
1 = Expand local groups only<br>
2 = Expand public groups only (default)<br>
3 = Expand local and public groups</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier">$FromPreferredLanguage</font></b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">The preferred language of the originating mail database.<br>
IBM Lotus Sametime needs this item to be able to properly set the localization string for the meeting.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b>$LangChair</b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">Language of AltChair.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b>$NameLanguageTags</b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">The language used. Value for English is en.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b>$LangPrincipal </b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">The language used for $AltPrincipal</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b>$LangReservedBy</b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">The language used for ReservedBy</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b>$PreventReplies</b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">Indicates whether or not Chair wants replies back. If the to convey &quot;Do not reply&quot; is 1, all other values (including no item at all) mean the Chair is expecting a reply.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">Alarms</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">User interface field.<br>
Value is 1 when an alarm is enabled and is  when alarm is disabled or was never enabled.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">AllowBusyAccess</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">Calendar profile / R&amp;R room profile item<br>
Value is a list of canonical names of entities allowed to access the busytime of the entity whose profile this list appears on.<br>
The names in the list should not contain any domain names.<br>
A value of  means anyone.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">AllowBusyDetailAccess</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">Calendar profile / R&amp;R room profile item<br>
New for 6.0<br>
Value is a list of caonical names of entities allowed to access the detailed information in busytime of the entity whose profile this list appears on.<br>
A value of  means anyone.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">AllowControversialFields</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">Calendar profile / R&amp;R room profile item<br>
New for 6.0<br>
Value indicates if items deemed to be potentially sensitive may be harvested as part of detail harvesting in busytime. The list of what items are deemed to be harvested if this setting is enabled are found in the ControversialFields item.<br>
<br>
Value(s):<br>
 = No (Default)<br>
0 = No<br>
1 = Yes</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">AltBlindCopyTo</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">Mail recipient field<br>
Alternate names for the Bcc recipients. Defaults to primary name when the alternate name is unavailable.<br>
This list must be kept in sync with the BlindCopyTo field.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">AltChair</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">Alternate Name of the owner.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">AltCopyTo</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">Mail recipient field.<br>
Alternate names for the Cc recipients. Defaults to primary name when the alternate name is unavailable.<br>
This list must be kept in sync with the CopyTo field.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">AltDelegator</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">Alternate name of the calendar owner of delegator.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">AltDelegeeName</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">Alternate name of the person being delegated to.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">AltFYINames</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">C&amp;S attendee field.<br>
Alternate names for users who are not involved in a meeting, but should be aware of it. Only available for the Chair.<br>
This list must be kept in sync with the FYIAttendees field.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">AltOptionalNames</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">C&amp;S attendee field.<br>
Alternate names for users who may participate in a meeting.<br>
<br>
This list must be kept in sync with the OptionalAttendees field.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">AltRequiredNames</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">C&amp;S attendee field.<br>
The alternate name(s) of required users (To) on the entry.<br>
For R5 and later, this list contains the alternate name(s) of any required attendees to an entry. It is organized similar to mail alternate names.<br>
<br>
IMPORTANT: This list must be kept in sync with the RequiredAttendees field.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">AltSendTo</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">Mail recipient field.<br>
Alternate names for the To recipients. Defaults to primary name when the alternate name is unavailable.<br>
<br>
This list must be kept in sync with the SendTo field.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b>AppendEndTime</b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">Has same value as EndTime.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b>AppendStartTime</b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">Overrides the StartTime value for an entry. This value, if found, is used to change the calculated start time of an entry.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">AppointmentLead</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">The default amount of time before an Appointment starts that the alarm should trigger. The value MUST be in minutes and no other unit. The value is only of use when SetAlarmAppointment = 1. This item is used only on calendar profiles.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">ApptUNIDURL</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">The URL used to attend the online meeting place on the Online meeting server. Calculated during the save process.<br>
<br>
Default: value is &quot;&quot;</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b>AssignedTo</b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">A list of users a task is assigned to. This is the task equivalent of RequiredAttendees and should be treated correspondingly.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">AssignedState</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">Used by tasks for communicating status.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">AudioAndVideoFlag</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">R&amp;R room profile item<br>
The audio/video options flag for Sametime meetings.<br>
Valid valuesare:<br>
&quot;0&quot; - None (Default)<br>
&quot;1&quot; - Audio and/or Video settings</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">AudioFlag</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">R&amp;R room profile item<br>
The audio only option flag for Sametime meetings.<br>
<br>
Valid values are:<br>
&quot;&quot; - None (Default)<br>
&quot;1&quot; - Audio only</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">AudioVideoFlags</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">The audio/video options for Sametime meetings.<br>
<br>
Valid values are:<br>
&quot;0&quot; = None (Default)<br>
&quot;1&quot; = Audio only<br>
2 = Audio and Video</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">AudioVideoSelectionList</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">R&amp;R room profile item<br>
This R&amp;R setting only applies to &quot;Online&quot; R&amp;R types.<br>
For regular rooms or resources the value must be: &quot;&quot; (Default)</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">AutoProcessForwardTo</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">R&amp;R room profile item<br>
Stored on the room or resource profile document in the R&amp;R dB. Performs the same function as ResourceOwner on a reservation request. See ResourceOwner.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">AutoProcessType</font></b><font face="Courier New"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">Calendar profile / R&amp;R room profile item<br>
<br>
Indicates what kind of owner restriction, if any, exists for a room or resource. Indicates the autoprocessing settings for a user when on a Calendar profile. Not all values are valid for all profile docs.<br>
<br>
Value(s) are:<br>
0 = None (R&amp;R) / Automatically process meeting invitations from all users (Calendar)<br>
1 = Only the Owner can book (R&amp;R) / Delegate meeting invitations to the following person, the list is specified in AutoProcessUserList (Calendar)<br>
2 = Only people on specified list can book. See AutoProcessUserList (R&amp;R) / Automatically process meeting invitations from specified users (Calendar)<br>
3 = Only people on list can book via autoprocess; others need owner approval (R&amp;R)<br>
4 = Not used<br>
5 = Inbox management: Calendar managed by another . New with R6 and may be obsolete now.<br>
6 = Forward notifications of invites to specified users. New to R6. (Calendar)<br>
7 = Just like 0 and 2 in that you automatically process meeting requests. Supports using AutoProcessFromType to decide which requests to do (Anyone/Only Some/Anyone but). Only really used for &quot;Anyone but&quot; because we map &quot;Anyone&quot; and &quot;Only Some&quot; to0 and 2 on-disk respectively to maximize backwards compatibility. New with R6. (Calendar)<br>
8 = Just like 1 in that you specify a delegate for your meetings requests. Supports using AutoProcessFromType to decide which requests to do (Anyone/Only Some/Anyone but). Used for &quot;Only Some&quot; and &quot;Anyone but&quot; but not &quot;Anyone&quot; because we map &quot;Anyone&quot; to 1 on-disk to maximize backwards compatibility. New with R6. (Calendar)<br>
D = Disabled (R&amp;R) / No autoprocessing of invitations (Calendar).</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">AutoProcessUserList</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">R&amp;R room profile item<br>
<br>
List of the names of the only users (or groups) which are allowed to reserve a Specific People or Autoprocess type of room without requiring owner approval.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">AutoRemoveFromInbox</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">Calendar Profile Item. A user preference to NOT see replies in their Inbox. If a user selects this option, replies are automatically removed from Inbox (but are still visible in the Meetings view).</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">AutoReminder</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">R&amp;R site option<br>
Indicates if the Autoreminder feature is enabled or for the site. If not enabled then all the other autoreminder settings are ignored.<br>
Valid values are:<br>
&quot;On&quot; = Autoreminders are enabled<br>
&quot;Off&quot; = Autoreminders are disabled</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">AVSlctLst</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">R&amp;R room option<br>
Default for non-Sametime rooms is .<br>
Default for Sametime rooms is 1</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">Broadcast</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">Indicates whether the Chair wants to receive any responses. Valid values are:<br>
1 = Broadcast, do not RSVP<br>
Any other value = RSVP (Default)</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">CalForwardChairNotificationTo</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">C&amp;S preference item<br>
Indicates whom notices should be forwarded to when the Chair receives a response back. This is for managed Calendars where another user or users need to be notified of a response back to the Chair.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">CalForwardInviteeNotificationTo</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">C&amp;S preference item<br>
Indicates whom notices should be forwarded to when the user receives a C&amp;S workflow message from a Chair. This is for managed Calendars where another user or users need to be notified of a new C&amp;S notice or update from a meeting Chair.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">CalForwardPrivateMode </font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">C&amp;S preference item<br>
Indicates what level of information should be included on a forwarded notice.<br>
Values are:<br>
0 = None. Do not forward / notify.<br>
1 = Hide details. Only send a summary.<br>
2 = Full details. Send a complete copy (subject of entry, etc).</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">Capacity</font></b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">R&amp;R room option / C&amp;S workflow item<br>
<br>
On an room document the value indcates the capacity of a room can hold. If a reservation request exceedes the capacity of a room it will still be accepted; the Acceptance notice the Chair receives will include a note indicating this since not all invitees may be physically attending.<br>
<br>
On a reservation request the value indicates the number of meeting participants. The value is compared against the value of the specified room in order to warn the Chair if they have possibly exceeded the capacity.<br>
<br>
Values should be positive integer values.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">Categories </font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">Category picked or entered by the user.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">ChairDomain </font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">Notes domain of the user who is chairing or organizing the entry. If Chair is in Internet format, then this item is empty.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">CommonNameResourceName</font></b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">R&amp;R room option<br>
<br>
The friendly or common name part of the room or resource name.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">ConferenceDatabase</font></b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">R&amp;R room option<br>
The name of the Sametime conference database where the request will be forwarded to by the Rooms &amp; Resource Manager. It appears on ALL room or resource documents even if they are not a Sametime entry.<br>
<br>
Value must be stconf.nsf</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">ControversialFields</font></b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">Calendar profile / R&amp;R room profile item<br>
<br>
New for 6.0<br>
<br>
Value indicates which controversial or potentially sensitive items the user will allow to be harvested into busytime. This typically means meeting subjects which can contain information that not everyone should be able to see (eg: Teleconference information).<br>
<br>
The list is only used if AllowControversialFields item is set to 1 and detail harvesting has been enabled on the Default Domain Configuration doc in the NAB.<br>
<br>
Default: </td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">DeclineReason </font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">The reason why a room reservation request was declined by a Room Owner.<br>
Default: </td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">DelegateToList </font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">Text list of delegees in the order in which they were delegated. The original invitee is not on the list. This can be an Internet address.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">DeliveredDate </font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">The date/time stamp when the notice was delivered to the invitees inbox or the R&amp;R database.<br>
This value is set by the Domino mail Router.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">DeliveryPriority</font></b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">The delivery priority chosen by the user (High|H, Low|L, Normal|N)</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">DeliveryReport</font></b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">The Delivery Report options chosen by the user (None|0, Only on Failure|1, Confirm Delivery|2, Trace Entire Path|3)</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">Encrypt </font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">Security mail option Encrypt. Value is 0 when not chosen by the user and 1 when chosen.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">EndTimeZone</font></b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">The Notes timezone string for the EndDateTime.<br>
Time zone strings are in the following format:<br>
Fixed Time Zone:<br>
Z=$DO=0$ZX=0$ZN=<br>
Zone with daylight savings:<br>
Z=$DO=1;$DL= &gt; $ZX=0$ZN=</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">EnterBlindCopyTo</font></b><b><font size="4"> </font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">C&amp;S attendee field.<br>
Primary names for potential users who are not involved in a meeting but should be aware of it. Only available for the Chair.<br>
Present only on a draft meeting and mutually exclusive to FYIAttendees field.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">EnterCopyTo</font></b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">C&amp;S attendee field.<br>
<br>
Primary names for potential users who may participate in a meeting.<br>
Present only on a draft meeting and mutually exclusive to OptionalAttendees field.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">EnterSendTo</font></b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">C&amp;S attendee field.<br>
Primary names for potential users who are required to participate in a meeting.<br>
Present only on a draft meeting and mutually exclusive to RequiredAttendees field.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">ExcludeFromAll</font></b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">C&amp;S preference item.<br>
Indicates that C&amp;S entries should be excluded from the All Documents view of the mail file. A 1 indicates C&amp;S entries should be hidden. and will cause a A to be added to the ExcludeFromView item on the not.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">ExpandedList</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">R&amp;R room option<br>
<br>
The expanded contents of AutoProcessUserList item. If the AutoProcessUserList only contains users then the two items will be the same.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">ExpandedOwners</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">R&amp;R room option<br>
<br>
The expanded contents of AutoProcessForwardTo item. If the AutoProcessForwardTo only contains users then the two items will be the same.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">ExternalAddress</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">R&amp;R room option<br>
<br>
The name of the mail-in database entry where the Rooms &amp; Resource Manager should forward the request for a Sametime meeting. The value should match the name given to the stscnf.nsf entry in the Domino Directory.<br>
<br>
Default value for non-Sametime entries is .</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">FromDomain</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">Contains the Notes domain of the user who created the document. This is normally put on by client mailer code.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">FYIAttendees</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">C&amp;S attendee field.<br>
<br>
Primary names for users who are not involved in a meeting but should be aware of it. Only available for the Chair.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">HowCreated</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">R&amp;R Site option<br>
<br>
Indicates which kinds of reservations should generate autoreminder notices, if the autoreminder feature is enabled.<br>
<br>
Valid values are:<br>
&quot;0&quot; = All reservations<br>
&quot;1&quot; = Direct book reservations only.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">INetFrom</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">RFC822 email address corresponding to From item.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">InetBlindCopyTo</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">Mail recipient field.<br>
<br>
Internet addresses for the Bcc or FYI recipients. Defaults to . when the Internet address is unavailable.<br>
<br>
This list must be kept in sync with the BlindCopyTo field.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">InetCopyTo</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">Mail recipient field.<br>
<br>
Internet addresses for the Cc recipients. Defaults to . when the Internet address is unavailable.<br>
<br>
This list must be kept in sync with the CopyTo field.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">INetFYINames</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">C&amp;S attendee field.<br>
<br>
Internet addresses for users who are not involved in a meeting but should be aware of it. Only available for the Chair.<br>
<br>
This list must be kept in sync with the FYIAttendees field.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">INetOptionalNames</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">C&amp;S attendee field.<br>
<br>
Internet addresses for users who may participate in a meeting.<br>
This list must be kept in sync with the OptionalAttendees field.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">INetRequiredNames</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">C&amp;S attendee field.<br>
<br>
Internet addresses for users who are required to participate in a meeting.<br>
This list must be kept in sync with the RequiredAttendees field.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">InetSendTo</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">Mail recipient field.<br>
<br>
Internet addresses for the To recipients. Defaults to . when the Internet address is unavailable.<br>
This list must be kept in sync with the SendTo field.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">KeepPosted</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">Determines whether participant wants to be kept notified of updates.<br>
This setting is on reply to Chair for decline and delegation.<br>
<br>
0 = Do not want further updates (Default if missing)<br>
<br>
1 = Do want further updates</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">LimitDate</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">R&amp;R room option<br>
<br>
This setting indicates what the last allowed reservable date is for a room or resource. All reservations beyond that date will be declined by the Rooms &amp; Resource Manager.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">LimitDays</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">R&amp;R room option<br>
<br>
This setting indicates the number of days out that a room or resource is allowed to be reserved. All reservations beyond that number of days will be declined by the Rooms &amp; Resource Manager.<br>
<br>
Since this value constitutes a moving value, one that needs to change each day, the Update Blocker Documents Agent must be enabled and configured properly for this kind of limit to work properly.<br>
<br>
The value must be a positive integer value.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">LimitDD</font></b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">R&amp;R room option<br>
<br>
Admins can limit how far out R&amp;R reservations can be made. This setting on the room or resource profile doc indicates that some limit setting has been enabled. The actual kind of limit is determined by the LimitHow item.<br>
<br>
This setting has no effect or relevance for SameTime type resources.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">LimitHow</font></b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">R&amp;R room option<br>
<br>
This setting indicates what kind of future booking limit has been set on a room or resource.<br>
<br>
Values are:<br>
1 = Limit by days. The actual number of days ahead is set in the LimitDays item.<br>
2 = Limit by date. The actual last reservable date is set in the LimitDate item.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">Location</font></b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">The location where the entry will occur. This value may be specified by the user or constructed by the template if the user enters no value but some Room &amp; Resource data exists on the entry.<br>
<br>
The value is not fixed or governed by any rules; it may be some arbitrary information or data inserted by the template. Trying to parse the value for some semanticly usable data may or may not be possible. Instead, the desired data should be parsed from the other items on the entry.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">Logo</font></b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">This is the background design on regular mail. Inherited by C&amp;S note but is not used.<br>
<br>
The value specifies the sending users default letterhead value and is of the base format of stdNotesLtr# where # is some number.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">MailOptions</font></b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">Value appears to be always 0 in this context.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">MeetingType</font></b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">One of the Sametime meeting types.<br>
<br>
Valid values are:<br>
&quot;1&quot; - Collaboration<br>
&quot;2&quot; - Moderated<br>
&quot;3&quot;  Broadcast<br>
<br>
Default: &quot;1&quot; in Notes 6 and 7<br>
Default: 2 in Notes 8</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">MeetingPassword</font></b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">Online Meeting password if used.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">Moderator</font></b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">The canonical name of the moderator of the Sametime meeting.<br>
Note: This does not have to be the same person who schedules the meeting.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">NDays1</font></b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">R&amp;R site option<br>
Used to indiciate how many days prior to a event the first autoreminder should be sent if the autoreminders are configured to be sent Daily.<br>
<br>
The value is ignored if the autoreminder is set to Weekly.<br>
<br>
See the SendWhen item.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">NDays2</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">R&amp;R site option<br>
Used to indiciate how many days prior to a event the second autoreminder should be sent if the autoreminders are configured to be sent Daily.<br>
<br>
The value is ignored if the autoreminder is set to Weekly.<br>
<br>
See the SendWhen item.<br>
<br>
A value of &quot;0&quot; means no second autoreminder should be sent.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">NDays3</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">R&amp;R site option<br>
Used to indiciate how many days prior to a event the third autoreminder should be sent if the autoreminders are configured to be sent Daily.<br>
<br>
The value is ignored if the autoreminder is set to Weekly.<br>
<br>
See the SendWhen item.<br>
<br>
A value of &quot;0&quot; means no third autoreminder should be sent.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">NewEndDateTime</font></b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">The counter-proposed UTC end datetime for a new DueDate or EndDate.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">NewEndTimeZone</font></b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">The Notes timezone string for the NewEndDateTime.<br>
<br>
Time zone strings are in the following format:<br>
<br>
Fixed Time Zone:<br>
Z=$DO=0$ZX=0$ZN=<br>
Zone with daylight saving:<br>
Z=$DO=1;$DL= &gt; $ZX=0$ZN=</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">NewStartDateTime</font></b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">The counter-proposed UTC start date and time for a new StartTime. Although this information could be merged into one item with NewStartTime, there are R5 historical reasons for the creation of StartDate and StartTime, so two items are needed to convey the counter proposal to the Chair. Since tasks have no StartTime, there is no equivalent for it on tasks.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">NewStartTimeZone</font></b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">The Notes time zone string for the NewStartDate<br>
<br>
Time zone strings are in the following format:<br>
<br>
Fixed Time Zone:<br>
Z=$DO=0$ZX=0$ZN=<br>
Zone with daylight saving:<br>
Z=$DO=1;$DL= &gt; $ZX=0$ZN= </td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">NoticeTypeRepaired</font></b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">The original NoticeType item value of a repaired / obsoleted entry.<br>
Valid values are the same as those for NoticeType.<br>
<br>
New for 8.5.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">OnlineMeeting</font></b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">If meeting is an online meeting, value field is 1.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">OnlinePlace</font></b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">Name of the online place found in the Domino Directory. Note that this is where the name is stored after processing has occurred.<br>
<br>
Valid values are:<br>
Taken from the list of Online meeting places in the Domino Directory (in canonical format).</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">OnlinePlaceToReserve </font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">Name of the online place found in the Domino Directory. Note that this is where the name is stored before processing has occurred.<br>
Valid values are:<br>
Taken from the list of Online meeting places in the Domino Directory.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">OrgConfidential</font></b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">Indicates whether the entry is private or not . This was also shared with the Lotus Organizer product.<br>
<br>
Value is  if Mark Private is not checked, and 1 if it is checked.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">OrgRepeat </font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">Indicates whether the entry repeats.<br>
See also Repeats field.<br>
Value is 1 if entry is a repeating one, and  if it is not.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">OrgState</font></b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">C&amp;S item for Lotus Organizer<br>
<br>
Indicates the type of entity the that this was created for: Users, Rooms, Resources or a Sametime meeting. It was added in R5 to support Lotus Organizer. It is currently only present for backwards compatibility.<br>
<br>
Valid values are:<br>
&quot;0&quot; = A person<br>
&quot;5&quot; = A room<br>
&quot;6&quot; = A resource<br>
&quot;7&quot; = A Sametime meeting</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">OrgStatus</font></b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">C&amp;S item for Lotus Organizer  from here: <a href="../images/Calendar_and_Scheduling825.gif">../images/Calendar_and_Scheduling825.gif</a><br>
<br>
Sent on a Status Update notice to an invitee telling them they are either required to attend or removed from a meeting invitation. is currently only present for backwards compatibility<br>
<br>
Valid values are:<br>
2 = Accepted<br>
5 = Removed</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">OriginalDelegator</font></b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">Owner of calendar who was original invitee for this delegation chain. This can be an Internet address.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">OriginalEndDate</font></b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">The original UTC end date &amp; time of the repeat instance that is being rescheduled. This is necessary when the user reschedules a single (or run of) repeating entry so that they know which one to use as the base reference point.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">OriginalEndTimeZone </font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">The Notes timezone string for<br>
<br>
TimeZones strings are in the following format:<br>
<br>
Fixed Time Zone:<br>
Z=$DO=0$ZX=0$ZN=<br>
Zone with daylight saving:<br>
Z=$DO=1;$DL= &gt; $ZX=0$ZN=</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">OriginalStartDate</font></b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">The name of this item is misleading. It is not the original S<br>
Useful in the case of rescheduling.<br>
Do not put on a repeat parent doc.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">OriginalStartTimeZone</font></b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">The Notes<br>
TimeZones strings are in the following format:<br>
<br>
Fixed Time Zone:<br>
Z=$DO=0$ZX=0$ZN=<br>
Zone with daylight savings:<br>
Z=$DO=1;$DL= &gt; $ZX=0$ZN=</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">ParentRepeatDates</font></b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">The current set of repeating dates &amp; times, including all reschedules to that point.<br>
<br>
See RepeatDates for more details on the usage (although its use on a parent document may be slightly different).</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">ParentRepeatInstanceDates</font></b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">The original set of repeating dates &amp; times from when the entry was created.<br>
<br>
See RepeatInstanceDates for more details on the usage (although its use on a parent document may be slightly different).</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">PostedDate</font></b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">The client stamps this date/time on Note when it is mailed.<br>
<br>
This item is used by R&amp;R to distinguish a request sent from a users Calendar from a directly booked request.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">Presenters</font></b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">User</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">PreventCounter </font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">Indicates that the Chair does not want any counter proposals.<br>
<br>
Valid values are:<br>
1 = Do not allow the invitees to counter propose<br>
All other values (including missing) = Allow it</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">PreventDelegate </font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">Used to indicate the Chair does not want to allow any delegation by invitees.<br>
Valid values are:<br>
1 = Do not allow the invitees to delegate<br>
All other values (including missing) = Allow it</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">PreventRepliesFromInbox</font></b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">C&amp;S preference item<br>
<br>
Indicates what kinds of C&amp;S documents the user wants displayed in their Inbox.<br>
<br>
Values are:<br>
0 = Display All Notices<br>
1 = Display All Except Responses<br>
2 = Display No C&amp;S docs in Inbox  (they only show in the miniview)</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">Purpose</font></b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">The purpose of the room or resource reservation.<br>
<br>
Same as the Topic field for reservations created from the Calendar. This is the item used in the R&amp;R template for direct-booked reservations</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">RepeatAdjust </font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">Text list describing the days/dates that the rule should use to calculate the list of repeat dates &amp; times (for example, Monday, 1st of the Month). Currently only repeat types W (Weekly) and M (Monthly) require this parameter.<br>
<br>
In Notes version 4, this item was 0 based, so Sunday (for weekly entries) was 0, and so on. This is legacy now and may not be changed without seriously impacting backward compatibility.<br>
<br>
When dealing with D (Repeat by Month Date) repeats, the list is 1 based and is the list of dates in the month that the entry should repeat. Negative values must not be used here. If you want to have &quot;The 2nd-to-last day&quot; of the month, then use &quot;2&quot; here and set RepeatFromEnd to 1.<br>
<br>
This exists only in the Repeat Parent document and on Notice sent to original invitees. It is informational only, since the UI of the Chair used this information to generate the original repeat dates item.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">RepeatCustom</font></b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">A hard-coded list of dates used mainly for custom repeating entries. Used by the UI code to set custom dates. Once repeat is saved, the items are copied to RepeatDates.<br>
<br>
This exists only in the Repeat Parent document and on Notice sent to original invitees. It is informational only, since the UI of the Chair used this information to generate the original repeat dates item.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">RepeatDates </font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">The set of repeating dates &amp; (start) times at which the entry repeats. The end date &amp; times are not specified on another item; rather, they are derived by shifting the list of start date &amp; times by the entrys duration. The presence of this item or of OrgRepeat is what truly signifies an entry is repeating, not any other checks.<br>
<br>
Note: This exists only in the Parent Doc.<br>
<br>
Important: This serves as the key when a lookup is performed on the ($RepeatLookup) view, in the code.<br>
<br>
This is a peer item to ParentRepeatDates and, depending on some scenarios, one item may be used in place of the other. When creating an outgoing message, this item is the backup to RepeatInstanceDates. If RepeatInstanceDates is not present, then RepeatDates is sent instead.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">RepeatEndDates</font></b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">When a repeating meeting is accepted, the repeat end dates are generated on parent repeat document. They are the corresponding end dates for the dates found in RepeatDates item.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">RepeatFor</font></b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">The number of RepeatForUnits for which the entry repeats This value is a positive integer. Any zero or negative values are automatically treated as 1. Does not have any significance when repeat to date is chosen.<br>
<br>
This exists only in the Repeat Parent document and on Notice sent to original invitees. It is informational only, since the UI of the Chair used this information to generate the original repeat dates item.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">RepeatForUnit</font></b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">The unit of time that the repeat rule is for. Further defined by RepeatUnit value.<br>
<br>
This exists only in the Repeat Parent document and on Notice sent to original invitees. It is informational only, since the UI of the Chair used this information to generate the original repeat dates item.<br>
<br>
Valid values are:<br>
 = Custom<br>
D = Daily<br>
M = Monthly<br>
W = Weekly<br>
Y = Yearly</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">RepeatFromEnd</font></b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">Flag indicating whether the monthly repeat is from the end of the month instead of the start of the month. Valid values are:<br>
<br>
1 = Start from the end (that is, values in RepeatAdjust are relative to the end of the month).<br>
<br>
All other values (or missing) = Start from the beginning of the month<br>
<br>
This exists only in the Repeat Parent Document and on Notice sent to original invitees. It is informational only, since the UI of the Chair used this information to generate the original repeat dates item.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">RepeatHow</font></b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">Indicates how the user wanted the repeat set to be terminated, either by count or by explicit date.<br>
Valid values are:<br>
<br>
F = &quot;For&quot;; indicates a count was desired<br>
<br>
U = &quot;Until&quot;; indicates that an explicit repeat end date/time was desired. The desired date/time is in RepeatUntil.<br>
<br>
This exists only in the Repeat Parent Document and on Notice sent to original invitees. It is informational only, since the UI of the Chair used this information to generate the original repeat dates item.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">RepeatIds</font></b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">A list of UNID(s) of the response documents. One for each repeat instance.<br>
<br>
Note: Exists only in the Repeat Parent document.<br>
<br>
In Notes 6, this exists only for Repeating All Day Events.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">RepeatInstanceDates</font></b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">The set of dates &amp; times that are affected by the message that they are on.<br>
For repeating entries this may be a single date &amp; time if just a single instance is being, say, rescheduled; or it may be a list of dates &amp; times if a range of entries is affected, such as canceling this and all future instances.<br>
<br>
<br>
This item is copied at creation from RepeatDates so that it can become a snapshot of the original set of dates &amp; times. This is a peer item to ParentRepeatInstanceDates and, depending on some scenarios, one item may be used in place of the other.<br>
When an outgoing message is created, this item is the primary to RepeatDates. If RepeatInstanceDates is not present, then RepeatDates is sent instead.<br>
<br>
The number of items in this list must match the number of entries in the StartDateTime and EndDateTime items of a repeating meeting.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">RepeatInterval</font></b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">The interval at which the rule applies. Only positive integer values are valid. The value is used in conjunction with RepeatUnit to calculate the next repeat date for an entry.<br>
<br>
This exists only in the Repeat Parent document and on Notice sent to original invitees. It is informational only, since the UI of the Chair used this information to generate the original repeat dates item.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">Repeats</font></b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">Indicates whether the entry repeats. Value is 1 if entry is repeating and  if it is not.<br>
<br>
See also OrgRepeat field.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">RepeatStartDate</font></b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">The starting date of the repeating entries. The starting time is actually pulled from either the StartTime item (or from EndTime / DueDateTime when calculating the proper end time).<br>
<br>
This exists only in the Repeat Parent document and on Notice sent to original invitees. It is informational only, since the UI of the Chair used this information to generate the original repeat dates item.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">RepeatUnit</font></b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">The unit of time over which the entry repeats.<br>
This exists only in the Repeat Parent document and on Notice sent to original invitees. It is informational only, since the UI of the Chair used this information to generate the original repeat dates item.<br>
<br>
Valid values are:<br>
C = Custom set of explicit dates<br>
D = Daily<br>
MD = Monthly by date (that is, the 1st of each month)<br>
MP = Monthly by day (that is, the 1st Monday of each month)<br>
Y = Yearly</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">RepeatUntil</font></b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">The UTC date (&amp; time) up to which the entry set repeats. Since Notes does not currently have the concept of a repeat set that occurs more than once a day (for example, Repeat @ 9AM and 3PM every day for a week&quot;), the time sub value is not used or necessarily set properly. This item is meaningful only if the RepeatHow is set to repeat how until.<br>
<br>
This exists only in the Repeat Parent document and on Notice sent to original invitees. It is informational only, since the UI of the Chair used this information to generate the original repeat dates item.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">RepeatWeekends</font></b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">Indicate what, if anything, should happen to a repeat instance that occurs on a weekend. This items value is checked only in some cases of repeating entries.<br>
As of Notes R5, this item is used only if the entry is Daily (D), Monthly (D only), or Yearly (Y); all other types of repeat sets cause this value not to be useful.<br>
This exists only in the Repeat Parent Document and on Notice sent to original invitees. It is informational only, since the UI of the Chair used this information to generate the original repeat dates item.<br>
Valid values are:<br>
D = Dont move weekend occurrence<br>
F = Move weekend occurrence to previous workday, presumably Friday<br>
M = Move weekend occurrence to next workday, presumably Monday<br>
N = Move weekend occurrence to closest workday (forward or backward)<br>
X = Remove weekend occurrence from the repeat set</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">RequiredAttendees</font></b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">C&amp;S attendee field.<br>
<br>
Primary names for users who are required to participate in a meeting.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">RequiredResources</font></b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">C&amp;S attendee field.<br>
<br>
A list of resources the Chair wants/needs to have.<br>
<br>
Notes version 4: For repeating entries, this entry is stored on the parent document.<br>
Version 5 and later: For repeating entries, this entry is stored on the individual child document(s).</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">RescheduleEndDateTimes </font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">C&amp;S workflow message.<br>
<br>
The set of EndDateTimes for the repeat set to which this invitee is being invited after notice is applied. For example, if the invitee is being invited to only the last three days of the repeat meeting, then RescheduleEndDateTimes contains the new end datetime values for the last three dates of the repeat set.<br>
<br>
For other actions such as Cancel, Remove, and Update, the set of EndDateTimes for the repeat set determines what dates should be used when this action is applied.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">RescheduleInstanceDates</font></b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">C&amp;S workflow message.<br>
<br>
The initial set of DateTimes values for the repeat set over which this action should be applied.<br>
<br>
This set must be in sync with RescheduleEndDateTime and RescheduleStartDateTime.<br>
<br>
For example, if the invitee is being invited to only the last three days of the repeat meeting, then RescheduleInstanceDates contains the initial datetime values for the last three dates of the repeat set.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">RescheduleStartDateTimes</font></b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">C&amp;S workflow message.<br>
<br>
The set of StartDateTimes for the repeat set to which this invitee is being invited after notice is applied. For example, if the invitee is being invited only to the last three days of the repeat meeting, then RescheduleStartDateTimes contains the new start datetime values for the last three dates of the repeat set.<br>
<br>
For other actions such as Cancel, Remove, and Update, the set of EndDateTimes for the repeat set determines what dates should be used when this action is applied.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">RescheduleWhich</font></b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">Indicates which repeat entry or range of entries is being modified/cancelled. This is for backward compatibility.<br>
If the recipient is Notes 6 and later, then the information in RescheduleStartDateTimes, RescheduleEndDateTimes, and RescheduleInstanceDates is used instead.<br>
<br>
Valid values are:<br>
<br>
<br>
0 = Current (single) instance only<br>
1 = All instances<br>
2 = Current and all previous<br>
3 = Current and all future<br>
-1 = User-cancelled modifying repeat</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">ResourceOwner</font></b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">R&amp;R owner list<br>
<br>
Used on R&amp;R documents<br>
<br>
Value indicates the name(s) of any room or resource owner(s) whose approval is required for a reservation request.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">Resources</font></b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">User interface field.<br>
<br>
Value is always  in this context, since no resources can be picked for Appointments. (See Meetings)</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">ResourceName</font></b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">R&amp;R item<br>
<br>
Used on R&amp;R related documents to indicate which room or resource the document is for. The item is single valued as a separate document is created if multiple rooms or resources are involved.<br>
<br>
Value indicates the canonical room or resource associated with the workflow message.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">ResourceType</font></b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">R&amp;R type indicator.<br>
<br>
Used on R&amp;R documents only.<br>
<br>
Value indicates the type of resource specified in ResourceName. Values are:<br>
<br>
1 = Room<br>
2 = Resource<br>
<br>
There is no 3 for Online (Sametime) Meetings because those entries are never stored in the R&amp;R dB. They are forwarded along to the Sametime Server and are not kept in the R&amp;R database.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">RestrictAttendance</font></b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">	Indicates whether the online meeting is restricted to only those people/groups in the restricted list.<br>
Default is 0. </td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">RestrictToInviteList</font></b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">The list of users/groups that are allowed to attend this online meeting.<br>
<br>
Valid values are:<br>
The list of names are the people/groups in the From, Moderator, SendTo, CopyTo, BlindcopyTo fields.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">ReturnReceipt</font></b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">Indicates whether user wants a return receipt.<br>
<br>
Value is 1 when user has picked return receipt and  otherwise.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">RmRsrList </font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">R&amp;R site option<br>
<br>
Value indicates which specific rooms or resources have are configured to be subject to sending of autoreminders when the feature is enabled.<br>
<br>
The list is ignored if the RRChoice item is not set to &quot;1&quot;.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">Room</font></b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">C&amp;S Attendee field.<br>
<br>
The fully qualified name of the room (Roomname/site) for mailing notices to the Resource Reservation database.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">RoomToReserve</font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">User interface field.<br>
<br>
Value is always  in this context, since no rooms can be picked for Appointments. (See Meetings)</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">RQStatus</font></b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">Rooms &amp; Resource Request Status<br>
<br>
New to 7.0<br>
<br>
All newly created room reservation requests should have a value of T<br>
<br>
Valid values are:<br>
T = Request is tentative. Awaiting Room Owner or Rooms &amp; Resource Manager approval.<br>
A = Request has been approved by Rooms &amp; Resource Manager.<br>
R = Request has been rejected by a Room Owner or the Rooms &amp; Resource Manager. If the Room Owner provided a reason it will be saved in the DeclineReason item.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">RRChoice</font></b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">R&amp;R site option<br>
<br>
Value indicates which rooms or resources should be subject to sending of autoreminders when the feature is enabled.<br>
<br>
Valid values are:<br>
&quot;0&quot; = All rooms / resources<br>
&quot;1&quot; = Particular rooms / resources. The selected names are stored in the RmRsrList item.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">SametimeServer</font></b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">Name of the Sametime server on which the online meeting takes place.<br>
Values: Taken from the Domino Directory.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">SametimeType</font></b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">Calendar profile setting.<br>
<br>
Type of Sametime server the user wants to default to when scheduling online meetings.<br>
<br>
Valid values are:<br>
0 = Sametime meeting (Default)<br>
1 = Sametime Unyte meeting</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">SendWhen</font></b><font face="Courier New"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">R&amp;R site option<br>
<br>
Used to indiciate if autoreminders, when enabled, should be sent weeky or daily.<br>
<br>
Valid values are:<br>
&quot;0&quot; = Weekly (Default)<br>
&quot;1&quot; = Daily</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">SendAttachments</font></b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">Indicates whether the people who are invited to the meeting receive the attachments that will appear in the online meeting.<br>
<br>
Default: &quot;0&quot;</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">Sign</font></b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">Allows the user to Sign the entry for security purposes.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">Site</font></b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">R&amp;R item<br>
<br>
Stored on each reservation request to incidate the Site of the room or resource being requested.<br>
<br>
The value matchs the last component value of the room or resource name. So if a room or resource is renamed, this value needs to be updated to match any change.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">StartTimeZone</font></b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">The Notes timezone string for the StartDateTime.<br>
<br>
Time zone strings are in the following format:<br>
<br>
Fixed Time Zone:<br>
Z=$DO=0$ZX=0$ZN=<br>
Zone with daylight saving:<br>
Z=$DO=1;$DL= &gt; $ZX=0$ZN=</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">StartWeek</font></b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">R&amp;R site option<br>
<br>
Used to indicate which day the week starts on and thus when weekly autoreminders should be sent.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">StorageFYINames</font></b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">C&amp;S attendee field<br>
<br>
Mail formatting preferences for users who are not involved in a meeting but should be aware of it. Defaults to 1 or . when the preference is unavailable. Only available for the Chair.<br>
<br>
Formatting types are:<br>
0  Prefers Notes Rich Text<br>
1  Keep in senders format (no preference)<br>
2  Prefers MIME<br>
. (Period)  Keep in senders format (no preference)<br>
<br>
This list must be kept in sync with the FYIAttendees field.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">StorageOptionalNames</font></b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">C&amp;S attendee field<br>
<br>
Mail formatting preferences for users who may participate in a meeting. Defaults to 1 or . when the preference is unavailable.<br>
<br>
Formatting types are:<br>
0  Prefers Notes Rich Text<br>
1  Keep in senders format (no preference)<br>
2  Prefers MIME<br>
. (Period)  Keep in senders format (no preference)<br>
<br>
This list must be kept in sync with the OptionalAttendees field.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">StorageRequiredNames </font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">C&amp;S attendee field<br>
<br>
Mail formatting preferences for users who are required to participate in a meeting. Defaults to 1 or . when the preference is unavailable.<br>
<br>
Formatting types are:<br>
0  Prefers Notes Rich Text<br>
1  Keep in senders format (no preference)<br>
2  Prefers MIME<br>
. (Period)  Keep in senders format (no preference)<br>
<br>
This list must be kept in sync with the RequiredAttendees field.<br>
<br>
This item can be overloaded in version 6 and later, to contain a copy of the RescheduleInstanceDates item, due to backward compatibility with R5. When an R5 user accepts, StorageRequiredNames is sent back on the acceptance, allowing the Chair to know what days the invitee is accepting.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">STPermissions</font></b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">Sametime Unyte setting<br>
<br>
Setting to control who can attend the Sametime meeting.<br>
<br>
Valid values are:<br>
0 = Limit attendance to only meeting invitees<br>
1 = Open meeting to all users</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">STPermPresent</font></b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">Sametime Unyte setting<br>
<br>
Setting to indicate who will be allowed to present content during the Sametime Unyte meeting.<br>
<br>
Valid values are:<br>
0 = All participants have permission to present content.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">STRecordMeeting</font></b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">Sametime Unyte setting<br>
<br>
Setting to indicate if the Sametime meeting should be recorded or not.<br>
<br>
Valid values are:<br>
1 = Record this meeting so others can replay it later</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">STRoomName </font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">Sametime Unyte setting<br>
<br>
Textual label that the Chair has given to their Sametime Unyte meeting. This label is used to identify which Sametime settings are to be used on the calendar entry.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">STServiceInfo</font></b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">Sametime Unyte setting<br>
<br>
Valid values are:</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">STUnyteConferenceID</font></b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">Sametime Unyte setting<br>
<br>
The Sametime Unyte conference password. This setting is stored on both the Calendar Profile (for creating new online meetings easily) and on any workflow documents where the chair has scheduled a Sametime Unyte meeting.<br>
<br>
For backwards compatability this value is also stuffed into the MeetingPassword item.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">STUnyteConferenceURL</font></b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">Sametime Unyte setting<br>
<br>
The Sametime Unyte conference URL. This setting is stored on both the Calendar Profile (for creating new online meetings easily) and on any workflow documents where the chair has scheduled a Sametime Unyte meeting.<br>
<br>
For backwards compatability this value is also stuffed into the ApptUNIDURL item.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">TaskLead</font></b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">The default amount of time before an Task starts (or ends) that the alarm should trigger. The value MUST be in days, NOT minutes as the value is automatically adjusted internally before use. The value is only of use when SetAlarmTask = 1. This item is used only on calendar profiles.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">TaskType </font></b></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">Identifies the kind of task this is. Valid values are:<br>
1 = Personal task and personal todo<br>
2 = Group task and group todo</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">Topic</font></b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">The original Subject as entered by the Chair. This item is only on workflow meeting messages.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">UpdateSeq</font></b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">Indicates sequence of updated items in note.<br>
Tracks non-date/time changes (eg: Subject, Location). Always greater than or equal to the SequenceNum item. This value is tied to the entries in the $CSWISL item.</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><b><font face="Courier New">WhiteBoardContent</font></b><font size="4"> </font></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%">The attachments that are presented in the white board during the online meeting.<br>
Values: Files that the user chooses. (Note: works in conjunction with $FILE field.)</td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="15%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="30%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="21%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="1%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>
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

<tr valign="top"><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="20%"><b><font face="Courier New">CopyTo </font></b></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="47%">Fully distinguished name(s) of the Optional invitee(s).<br>
Mail recipient field.<br>
Primary names for the CC recipients.<br>
Contains the names of the optional invitees to which this workflow message is being sent.</td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="26%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="20%"><b><font face="Courier New">SendTo</font></b></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="47%">Fully distinguished name(s) of the Primary invitee(s)<br>
Mail recipient field.<br>
Primary names for the To recipients.<br>
Contains the names of the required invitees to which this workflow message is being sent. Or, in the case of a response, the Chairs address.</td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="26%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="20%"><b><font face="Courier New">BlindCopyTo</font></b></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="47%">Fully distinguished name(s) of FYI invitee(s).<br>
Mail recipient field.<br>
Primary names for the Bcc recipients. Each recipient is only able to see their own name in this field.</td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="26%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>
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

<tr valign="top"><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="20%"><font face="Courier New">$CSFlags </font></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="47%">Mainly used for repeating entries; Determines what type of repeating entry a document is.<br>
Flags used to control C&amp;S operations. Multiple values are allowed; they are simply concatenated into a single string.<br>
Valid values are:<br>
c = Repeat instances have been created (only appears on repeat parent)<br>
e = Document is a repeat exception<br>
h = Document is a Holiday document created by the Import Holiday agent<br>
i = Document is a repeating instance<br>
m = Document is a repeating workflow message. This is the most commonly used value and must be on any repeating entry.<br>
r = Document is a request for information<br>
u = Document is updated information<br>
w = Event is workflow enabled</td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="26%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="20%"><b><font face="Courier New">_ViewIcon2</font></b></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="47%">Secondary icon to display in a view column.<br>
The icon to display in the calendar views for the entry.<br>
Valid values are:<br>
11 = Blue informational icon. Indicates that the message contains a personal comment from the sender.<br>
33 = Reschedule</td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="26%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="20%"><b><font face="Courier New">Delegator</font></b></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="47%">Fully distinguished name of the delegator.<br>
Owner of calendar who is delegator. This can be an Internet address.</td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="26%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="20%"><b><font face="Courier New">Delegee</font></b></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="47%">Fully distinguished name of the person being delegated to.<br>
Person being delegated to. This can be an Internet address.</td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="26%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="20%"><b><font face="Courier New">FormToUse</font></b></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="47%">Only used by UI when sending a notice with additional comments</td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="26%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="20%"><b><font face="Courier New">NewEndDate</font></b></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="47%">New End date/time of the scheduled event.<br>
The counter-proposed UTC end date (not time) for a new DueDate or EndDate.</td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="26%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="20%"><b><font face="Courier New">NewEndTime</font></b></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="47%">New End date/time of the scheduled event.<br>
The counter-proposed UTC end time (not date) for a new EndDate. Since tasks have no EndTime, there is no equivalent for it.</td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="26%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="20%"><b><font face="Courier New">NewStartDate</font></b></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="47%">New Start date/time of the scheduled event.<br>
The counter-proposed UTC end date (not time) for a new StartDate. Although this information could be merged into one item with NewStartTime, there are Notes R5 historical reasons for the creation of StartDate and StartTime, so two items are needed to convey the counter proposal to the Chair.</td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="26%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="20%"><b><font face="Courier New">NewStartTime</font></b></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="47%">New Start date/time of the scheduled event.<br>
The counter-proposed UTC end time (not date) for a new StartTime. Although this information could be merged into one item with NewStartTime, there are R5 historical reasons for the creation of StartDate and StartTime, so two items are needed to convey the counter proposal to the Chair. Since tasks have no StartTime, there is no equivalent for it on tasks.</td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="26%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="20%"><b><font face="Courier New">NoticeType</font></b></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="47%">Type of the notice.<br>
Type of notice being sent. While the data type is for a string, only the first character of this item is used for determining what kind of notice it is.<br>
<br>
For R&amp;R in R7 or later, the only valid values to use are I on the initial invitation or U on an update / reschedule notice. The Rooms &amp; Resource Manager will handle changing it when the request is processed.<br>
<br>
Valid values are:<br>
A = User accepted request<br>
B = Chair has accepted a counter proposal<br>
C = Chair cancelled event<br>
D = User is delegating request; sent to Chair<br>
E = Participant would like fresh copy of event. Notice is refreshed info from Chair or Update info from Chair.<br>
When participant is requesting info, the $CSFlags contains r. When Chair is responding to request, the $CSFlags contains u.<br>
If Chair is merely sending an update, $CSFlags will not contain either of these flags.<br>
F = User has completed request<br>
G = User wants to add event to calendar (may not be stored on disk, only in memory use.)<br>
H = User is deleting event<br>
I = Invitation request<br>
J = Chair declines a counter-proposal request<br>
K = Chair is sending updated info to all invitees<br>
L = User is delegating request; Notice is sent to delegee<br>
N = Event is being confirmed by Chair<br>
P = User has tentatively accepted the invitation<br>
R = User declined the invitation<br>
S = Status update from Chair<br>
T = User is counter-proposing request<br>
U = Chair has rescheduled the event<br>
W = Waiting for reply from user<br>
X = Placeholder for &quot;Extended NoticeType&quot;; may not be in actual use.<br>
Y = Chair wants to remove rooms/resources<br>
Z = User has been removed (may not be stored on disk, only in memory use.)</td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="26%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="20%"><b><font face="Courier New">OptionalAttendees</font></b></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="47%">Fully distinguished name(s) of the Optional invitee(s).<br>
C&amp;S attendee field.<br>
Primary names for users who may participate in a meeting.</td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="26%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="20%"><b><font face="Courier New">Recipients</font></b></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="47%">Complete list of invitees.</td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="26%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="20%"><b><font face="Courier New">Requiredattendees</font></b></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="47%">Fully distinguished name(s) of thePrimary invitee(s).<br>
C&amp;S attendee field.<br>
Primary names for users who may participate in a meeting. </td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="26%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="20%"><b><font face="Courier New">StatusUpdate</font></b></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="47%">Details of the event status.<br>
Contains the comment when doing Accept/Decline with comment or when the Chair is rescheduling with comment.</td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="26%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="20%"><b><font face="Courier New">$Ref</font></b><font size="4" face="Calibri"> </font></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="47%"> The UNID of the parent document. Since the parent document should have a UNID equivalent to the ApptUNID,           use the ApptUNID to create the $Ref item.<br>
Do not put $Ref on a parent document.</td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="26%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="20%"><b><font face="Courier New">$RefOptions</font></b><font size="4"> </font></td><td width="2%">  </td><td width="47%">Value is 1. This must only be on Note if $Ref is on Note.<br>
Do not put $RefOptions on a note that does not contain a $Ref item. </td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="26%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="20%"><b><font face="Courier New">$Revisions</font></b><font size="4"> </font></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="47%"><font size="4">List of date/time stamps on which the document was revised. Item does not exist if document has not        been revised.</font></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="26%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="20%"><b><font face="Courier New">$Seal</font></b><b> </b></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="47%">The seal when the Encrypt option is chosen under Delivery options / Security Options.</td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="26%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="20%"><b><font face="Courier New">$SealData</font></b><font size="4"> </font></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="47%">The seal data when the Encrypt option is chosen under Delivery options / Security Options. When the owner chooses the option to encrypt mail, the body item of the document is encrypted and put into this item.</td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="26%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="20%"><b><font face="Courier New">$Signature</font></b><font size="4"> </font></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="47%">Digital signature of the items on the document.<br>
Item exists if the Chair chose Sign Delivery options / Security Options when sending the notice.</td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="26%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="20%"><b><font face="Courier New">$SMTPKeepNotesItems</font></b><font size="4"> </font></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="47%">Mail field<br>
This is a note to the mailer to store X-Notes-items in MIME stream when sending via SMTP. Value is 1.</td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="26%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="20%"><b><font face="Courier New">$SrvrHldy</font></b><font size="4"> </font></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="47%">Server Holiday<br>
<br>
This item is used to mark an entry as a Holiday that was imported from the server. If the item exists, the entry is some kind of Holiday otherwise it is not.<br>
<br>
There are no defined valid values. The presence of this item alone indicates it is imported from a Holiday set.</td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="26%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="20%"><b><font face="Courier New">$StorageBcc</font></b><font size="4"> </font></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="47%">Mail recipient field.<br>
<br>
Mail formatting preferences for the Bcc recipients. Defaults to 1 or . when the preference is unavailable.<br>
<br>
This list must be kept in sync with the BlindCopyTo field.<br>
<br>
Valid values are:<br>
0  Prefers Notes Rich Text<br>
1  Keep in senders format (no preference)<br>
2  Prefers MIME<br>
. (Period)  Keep in senders format (no preference)</td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="26%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="20%"><b><font face="Courier New">$StorageCc</font></b><font size="4"> </font></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="47%">Mail recipient field.<br>
<br>
Mail formatting preferences for the Cc recipients. Defaults to 1 or . when the preference is unavailable.<br>
<br>
This list must be kept in sync with the CopyTo field.<br>
<br>
Valid values are:<br>
0  Prefers Notes Rich Text<br>
1  Keep in senders format (no preference)<br>
2  Prefers MIME<br>
. (Period)  Keep in senders format (no preference)</td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="26%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="20%"><b><font face="Courier New">$StorageTo</font></b><font size="4"> </font></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="47%">Mail recipient field.<br>
<br>
Mail formatting preferences for the To recipients. Defaults to 1 or . when the preference is unavailable.<br>
<br>
This list must be kept in sync with the SendTo field.<br>
<br>
Valid values are:<br>
0  Prefers Notes Rich Text<br>
1  Keep in senders format (No preference)<br>
2  Prefers MIME<br>
. (Period)  Keep in senders format (No preference)</td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="26%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="20%"><b><font face="Courier New">$Times1</font></b><font size="4"> </font></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="47%">Hours that the user works on Sunday. This item is used only on calendar profiles.</td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="26%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="20%"><b><font face="Courier New">$Times2</font></b></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="47%">Hours that the user works on Monday. This item is used only on calendar profiles.</td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="26%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="20%"><b><font face="Courier New">$Times3</font></b></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="47%">Hours that the user works on Tuesday. This item is used only on calendar profiles.</td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="26%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="20%"><b><font face="Courier New">$Times4</font></b></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="47%">Hours that the user works on Wednesday. This item is used only on calendar profiles</td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="26%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="20%"><b><font face="Courier New">$Times5</font></b></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="47%">Hours that the user works on Thursday. This item is used only on calendar profiles.</td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="26%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="20%"><b><font face="Courier New">$Times6</font></b></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="47%">Hours that the user works on Friday. This item is used only on calendar profiles<font size="4">.</font><font size="4"> </font></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="26%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="20%"><b><font face="Courier New">$Times7</font></b></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="47%">Hoursthat the user works on Satuday. This item is used only on calendar profiles.</td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="26%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="20%">$UpdatedBy<font size="4"> </font></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="47%">List of user names who modified the document.</td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="26%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td><td width="2%"><img width="1" height="1" src="../images/Calendar_and_Scheduling0.gif" border="0" alt=""></td></tr>

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
