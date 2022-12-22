




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Helv;
 panose-1:2 11 6 4 2 2 2 3 2 4;}
@font-face
 {font-family:"Cambria Math";
 panose-1:2 4 5 3 5 4 6 3 2 4;}
 /\* Style Definitions \*/
 p.MsoNormal, li.MsoNormal, div.MsoNormal
 {margin-top:0cm;
 margin-right:0cm;
 margin-bottom:8.0pt;
 margin-left:0cm;
 line-height:107%;
 font-size:11.0pt;
 font-family:"Calibri",sans-serif;}
.MsoChpDefault
 {font-size:11.0pt;}
.MsoPapDefault
 {margin-bottom:8.0pt;
 line-height:107%;}
 /\* Page Definitions \*/
 @page WordSection1
 {size:612.0pt 792.0pt;
 margin:72.0pt 72.0pt 72.0pt 72.0pt;}
div.WordSection1
 {page:WordSection1;}
-->




**Initial Release 9.0**



**Symbolic Value : iCalendar**



**CAL\_PROCESS\_xxx** **-** CAL\_PROCESS\_xxx
values are used to define the action taken by CalNoticeAction and
CalEntryAction


**----------------------------------------------------------------------------------------------------------**



**#include <calapi.h>**


 **Symbolic Values :**      CAL\_PROCESS\_ACCEPT    -  Accept (regardless of conflicts).  

For Information update notices or confirm notices, this will apply the changes
to the relavent calendar entry.  

Can be used by the organizer to accept a counter or to respond to a request for
updated info if done off of such a notice.  

  

      CAL\_PROCESS\_TENTATIVE           -  Tentatively accept (regardless of
conflicts)  

  

      CAL\_PROCESS\_DECLINE   -  Decline.Can be used by the organizer to decline
a counter if done from a counter notice.  

  

      CAL\_PROCESS\_DELEGATE            -  Delegate to EXT\_CALACTION\_DATA::pszDelegateTo  

  

      CAL\_PROCESS\_COUNTER             -  Counter to a new time (requires
populating EXT\_CALACTION\_DATA::ptdChangeTo values)  

  

      CAL\_PROCESS\_REQUESTINFO      -  Request information from the organizer
for this meeting  

  

      CAL\_PROCESS\_REMOVECANCEL              -  This will process a cancelation
notice, removing the meeting from the calendar  

  

      CAL\_PROCESS\_DELETE     -  This will physically delete a meeting from the
calendar. This will NOT send notices out  

  

      CAL\_PROCESS\_SMARTREMOVE    -  This will remove the meeting or appointment
from the calendar and send notices if necessary.  

It is treated as a CAL\_PROCESS\_CANCEL if the entry is a meeting the mailfile
owner is the organizer of.   

It is treated as a CAL\_PROCESS\_DECLINE if the entry is a meeting that the
mailfile owner is not the organizer of except when the entry is a broadcast.In
that case it is treated as a CAL\_PROCESS\_DELETE.  

It is treated as a CAL\_PROCESS\_DELETE if the entry is a non-meeting.  

  

      CAL\_PROCESS\_CANCEL    -  This will cancel a meeting that the mailfile
owner is the organizer of  

  

>    CAL\_PROCESS\_UPDATEINVITEES             -  This will update the invitee
lists on the specified entry (or entries) to include or remove those users
specified in lists contained in the EXT\_CALACTION\_DATA::pAddNames and
EXT\_CALACTION\_DATA::pRemoveNames values  

  




 




----------------------------------------------------------------------------------------------------------


 





