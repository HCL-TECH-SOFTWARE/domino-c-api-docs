




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



**CAL\_WRITE\_xxx** **-** Flags that
control behavior of the calendar APIs - Used when APIS take iCalendar input to
modify calendar data


**----------------------------------------------------------------------------------------------------------**



**#include <calapi.h>**


 **Symbolic Values :**      CAL\_WRITE\_COMPLETE\_REPLACE           -  Used when APIs
modify entry data via CalUpdateEntry.  

This flag means that NO data is preserved from the original entry and the
resulting entry is 100% a product of the iCalendar passed in.  

NOTE: When this flag is NOT used, some content may be preserved during an
update if that particular content was not included in the iCalendar input.  

This includes:Body,Attachments,Custom data properties as specified in
$CSCopyItems  

  

      CAL\_WRITE\_DISABLE\_IMPLICIT\_SCHEDULING     -  Used when APIs create or
modify calendar entries where the organizer is the mailfile owner.  

When a calendar entry is modified with CAL\_WRITE\_DISABLE\_IMPLICIT\_SCHEDULING
set, no notices are sent (invites, updates, reschedules, cancels, etc)  

Note: This is not intended for cases where you are saving a meeting as a draft
(since there is currently not a capability to then send it later. It will also
not allow some notices to go out but other notices not to go out (such as, send
invites to added invitees but dont send updates to existing invitees).  

Rather, this is targeted at callers that prefer to be responsible for sending
out notices themselves through a separate mechanism.  

  

      CAL\_WRITE\_IGNORE\_VERIFY\_DB              -  Used when APIs create or
modify entries on the calendar  

This will allow creation/modification of calendar entries, even if the database
is not a mailfile  

  

      CAL\_WRITE\_USE\_ALARM\_DEFAULTS        -  By default, alarms will be created
on calendar entries based on VALARM content of iCalendar input. Use of this
flag will disregard VALARM information in the iCalendar and use the user's
default alarm settings for created or updated entries.  

  




 




----------------------------------------------------------------------------------------------------------


 





