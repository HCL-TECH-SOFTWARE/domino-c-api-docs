##### Chapter 11-3
##### Performing scheduling actions on calendar entries

<b><font size="5" color="#000080">Performing scheduling actions on calendar entries</font></b><br>
<br>
Calendar entries that represent meeting data can be acted upon using the CalEntryAction method (similar to deleting).   Unlike CalUpdateAction, CalEntryAction can act on an entire series, a particular instance, or a range (this and future).
<p>For participants, this method can be used to change response status (accept, decline, counter, delegate, etc) or request information from the meeting organizer.
<ul type="disc">
<li>Decline</ul>
/*
<p>code snippet<br>
<br>
<br>
STATUS	error = NOERROR;<br>
char pszICalenderUID[] = &quot;<font size="2">20121120T172345Z-JJU9O5@example.com</font>&quot;;<br>
DWORD dwAction = CAL_PROCESS_DECLINE;<br>
DWORD dwRange = 0;<br>
PEXT_CALACTION_DATA pExtActionInfo = NULL;<br>
<br>
error = CalEntryAction(hDB, pszICalenderUID, NULL, dwAction, dwRange, &quot;decline&quot;, pExtActionInfo, 0, NULL);<br>
*/
<p>For meeting organizers, this can be used to cancel a meeting.
<ul type="disc">
<li>Cancle</ul>
/*
<p>code snippet<br>
<br>
<br>
STATUS	error = NOERROR;<br>
char pszICalenderUID[] = &quot;<font size="2">20121120T172345Z-JJU9O5@example.com</font>&quot;;<br>
DWORD dwAction = CAL_PROCESS_SMARTREMOVE;<br>
DWORD dwRange = 0;<br>
PEXT_CALACTION_DATA pExtActionInfo = NULL;<br>
<br>
error = CalEntryAction(hDB, pszICalenderUID, NULL, dwAction, dwRange, &quot;decline&quot;, pExtActionInfo, 0, NULL);<br>
*/
---
