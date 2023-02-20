##### Chapter 11-4
##### Reading calendar notices

<b><font size="5" color="#000080">Reading calendar notices</font></b><br>
<br>
Notices can be read in very similar ways to calendar entries.  However, there can be multiple notices for a UID, and even for a RECURRENCE-ID.  As such, the identifier for a notice is either a UNID or a NOTEID.
<p>The CalGetNewInvitaitons method returns lists of notices representing invitations for meetings that occur within a specified time range.This also has capabilities to limit output to only notices that have arrived since a given time (ie the last time you searched).
<p>The CalGetUnappliedNotices method returns lists of notices that remain unprocessed for a particular meeting (by UID).  This applies only for entries as the PARTICIPANT and returns any notices from the organizer that have not yet been applied to the calendar entries.  This includes any invitations, updates, reschedules, cancelations, etc. 
<p>Both CalGetNewInvitaitons and CalGetUnappliedNotices populate one or more of the following (if the caller provides a non-NULL argument): The number of notices that meet the criteria, a DHANDLE that points to a list of UNID data, and a DHANDLE representing IDTABLE information containing NOTEID data.
<p>To read a notice, use the identifier to call into CalReadNotice or CalReadNoticeUNID to return iCalendar data representing that notice.  iCalendar data is returned as char* data in a DHANDLE.
---
