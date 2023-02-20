##### Chapter 11-5
##### Performing scheduling actions on calendar notices

<b><font size="5" color="#000080">Performing scheduling actions on calendar notices</font></b><br>
<br>
Similar to CalEntryAction, actions can be taken on notices via CalNoticeAction or CalNoticeActionUNID.  Different actions are possible depending on the type of notice.
<p>Invitations or reschedules can be accepted, declined, delegated, countered, etc.  In addition to updating the mailfile with the result of the action, these will result in corresponding notices being sent to the meeting organizer.  Information updates and cancelations are applied without sending notices to the organizer since they do not require responses.
<p>Meeting organizers can also respond to notices from participants.  For instance, counterproposals can be accepted or declined and requests for information can be granted.
<p><b><span class="domino-highlight-yellow" style="background-color: yellow"><font size="4" color="#000080">Example Using Calendar and Scheduling Functions</font></span></b><br>

<ul type="disc">
<li>Accept</ul>
/*<br>
code snippet<br>
<br>
if organizer has sent an invitation, attendee can accept it using CalNoticeAction.<br>
first, call CalGetNewInvitations to find the noteID of the notice.<br>
second, call CalNoticeAction to accept it.<br>
<br>
*/<br>
<br>
STATUS	error = NOERROR;<br>
<br>
WORD wNumNotices = 0;<br>
MEMHANDLE hRetCalData = NULL;<br>
<br>
error = CalNoticeAction(hDB, noteID, CAL_PROCESS_ACCEPT, NULL, NULL, CAL_ACTION_DO_OVERWRITE_CHECK, NULL);<br>
<br>

---
