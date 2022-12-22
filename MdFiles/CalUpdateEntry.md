




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



**CalUpdateEntry** **- This will
modify an existing calendar entry.**


**----------------------------------------------------------------------------------------------------------**



**#include <calapi.h>**



STATUS **CalUpdateEntry(**  

      DBHANDLE  hDB,  

      const char\*pszCalEntry,  

      const char\*pszUID,  

      const char\*pszRecurID,  

      const char\*pszComments,  

      DWORD  dwFlags,  

      void\*pCtx**);**



**Description :**




This
will modify an existing calendar entry.  This supports either single entries or
recurring entries, but recurring entries will only 


support
updates for a single instance specified via RECURRENCE-ID that may not include
a RANGE (This may be permitted in the future but 


for
now will return an error).


The
iCalendar input may only contain a single VEVENT and must contain a UID.


By
default, attachments and custom data (for fields contained in $CSCopyItems)
will be maintained from the


existing
calendar entry.  Similarly, description will also be maintained if it is not
specified in the iCalendar


content
that is updating.  Both of these behaviors can be canceled via the
CAL\_WRITE\_COMPLETE\_REPLACE flag.


If
the mailfile owner is the meeting organizer, appropriate notices will be sent
out to meeting participants (unless


CAL\_WRITE\_DISABLE\_IMPLICIT\_SCHEDULING
is specified)


 


**Parameters :**



Input :  

hDB  -  The database containing the entry to update  

  

pszCalEntry  -  The iCalendar data representing the updated entry  

  

pszUID  -  If non-NULL, this value MUST match the UID value in the iCalendar
input if present,or else this returns ERR\_InvalidVEventPropertyFound.  If the
iCalendar input has no UID this value will be used.  

  

pszRecurID  -  If non-NULL, this value MUST match the RECURRENCE-ID value in
the iCalendar input if present, or else this returns
ERR\_InvalidVEventPropertyFound.  If the iCalendar input has no RECURRENCE-ID
this value will be used.  

  

pszComments  -  If non-NULL, this text will be sent as comments on any notices
sent to meeting participants as a result of this call. that will be included on
the notices. Can be NULL.  

  

dwFlags  -  CAL\_WRITE\_xxx flags to control non-default behavior. Supported:
CAL\_WRITE\_MODIFY\_LITERAL, CAL\_WRITE\_DISABLE\_IMPLICIT\_SCHEDULING, CAL\_WRITE\_IGNORE\_VERIFY\_DB.  

  

pCtx  -  RESERVED - MUST be NULL  

  




Output :  

(routine)  -  status of updating entry  

            NOERROR on success  

            ERR\_NULL\_DBHANDLE                                   The database
handle is NULL  

            ERR\_MISC\_INVALID\_ARGS                 Unexpected arguments provided  

            ERR\_CALACTION\_INVALID                 This calendar entry is not in
a state where updating it is supported.  

            ERR\_NO\_CALENDAR\_FOUND             Unable to find the entry because
the required view does not exist in this database  

            ERR\_NOT\_FOUND                                          There are no
entries that match the specified UID or UID/recurid in the database  

            ERR\_NOT\_YET\_IMPLEMENTED          This update is not yet supported
(update range or multiple VEVENTs?)  

            ERR\_CS\_PROFILE\_NOOWNER           Calendar Profile does not specify
owner  

            ERR\_UNEXPECTED\_METHOD            Provided iCalendar contains a
method (no method expected here)  

            ERR\_ICAL2NOTE\_OUTOFDATE          iCalendar input is out of date in
regards to sequence information.  

            ERR\_MissingVEventComponents                      Missing required
VEvent components  

            ERR\_InvalidVEventPropertyFound         Invalid VEvent property
found  

            ERR\_ICAL2NOTE\_CONVERT              Error interpereting iCalendar
input  

            ERR\_MISC\_UNEXPECTED\_ERROR    Unexpected internal error  

            ERR\_IMPLICIT\_SCHED\_FAILED          Entry was updated, but errors
were encountered sending notices to meeting participants  

  

  




 **See Also :**


**[CalCreateEntry](CalCreateEntry.md)**


**[CalReadEntry](CalReadEntry.md)**



----------------------------------------------------------------------------------------------------------


 





