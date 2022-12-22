




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



**Function : iCalendar**



**CalGetUnappliedNotices** **- Retrieve
the unapplied notices that exist for a participant of calendar entry
representing a meeting.**


**----------------------------------------------------------------------------------------------------------**



**#include <calapi.h>**



STATUS **CalGetUnappliedNotices(**  

      DBHANDLE  hDB,  

      const char\*pszUID,  

      WORD\*pwNumNotices,  

      MEMHANDLE \*phRetNOTEIDs,  

      MEMHANDLE \*phRetUNIDs,  

      void\*pReserved,  

      DWORD  dwFlags,  

      void\*pCtx**);**



**Description :**



Retrieve the
unapplied notices that exist for a participant of calendar entry representing a
meeting.


This
will return things like: Reschedules, informational updates, cancelations,
confirmations, etc.


Notices
will only be returned if the initial invitaiton has already been responded to,
otherwise this method will return ERR\_INVITE\_NOT\_ACCEPTED.


For
recurring meetings, notices that apply to any instances in the series will be
returned, with the exception of instances where the initial invitation has not
yet been responded to.


Calendar
entries that are not meetings will return ERR\_INVALID\_NOTE.


We
do not currently support getting unprocessed calendar entries if you are the
owner (such as a counter proposal request or a request for updated
information), so this will return ERR\_NOT\_YET\_IMPLEMENTED.


Note:
For recurring meetings, it is possible that multiple notices will contain
current information for a particular occurence, so it is not possible to
guarantee that there is a single "most current" notice.  For example,
the subject might be changed for a single instance, and then the time may be
changed across instances.  Because only one notice will have the current
subject and another notice will have the current time but NOT the current
subject, both notices will be returned and both must be processed to guarantee
accuracy.  Process returned notices via the CalNoticeAction method.


 


**Parameters :**



Input :  

hDB  -  The database to search for calendar entries.  

  

pszUID  -  The UID of the entry to return notices for.  

  

pReserved  -  RESERVED - MUST be NULL.  

  

dwFlags  -  Flags - currently unused.  

  

pCtx  -  RESERVED - MUST be NULL  

  




Output :  

pwNumNotices  -  The number of unapplied notices for this meeting (and thus
also the length of phRetNOTEIDs and/or phRetUNIDs if they are non-NULL).
Ignored if NULL.  

  

phRetNOTEIDs  -  Handle to the returned NOTEID data.  It is the caller's
responsibility to free this memory via OSMemoryFree (if non-NULL). Access the
data via casting the result of OSMemoryLock to a (NOTEID\*). Ignored if NULL.  

  

phRetUNIDs  -  Handle to the returned UNID data.  It is the caller's
responsibility to free this memory via OSMemoryFree (if non-NULL). Access the
data via casting the result of OSMemoryLock to a (UNID\*). Ignored if NULL.  

  




 




----------------------------------------------------------------------------------------------------------


 





