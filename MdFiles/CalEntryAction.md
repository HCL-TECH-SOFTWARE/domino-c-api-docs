




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



**CalEntryAction** **- Perform
an action on a calendar entry**


**----------------------------------------------------------------------------------------------------------**



**#include <calapi.h>**



STATUS **CalEntryAction(**  

      DBHANDLE  hDB,  

      const char\*pszUID,  

      const char\*pszRecurID,  

      DWORD  dwAction,  

      DWORD  dwRange,  

      const char\*pszComments,  

      PEXT\_CALACTION\_DATA  pExtActionInfo,  

      DWORD  dwFlags,  

      void\*pCtx**);**



**Description :**



Perform an
action on a calendar entry.  For instance, change the response of an accepted
meeting to counter or delegate.This must be applied to meetings (with the
exception of CAL\_PROCESS\_DELETE, which can be applied to any calendar
entry).This makes the appropriate modifications to the invitee calendar and
also sends appropriate notices out.


 


**Parameters :**



Input :  

hDB  -  The database containing calendar entries to act on  

  

pszUID  -  The UID of the entry to act on  

  

pszRecurID  -  The RECURRENCE-ID of the instance to act onMay be specified for
recurring meetings (omission acts on all).MUST be NULL for single meetings.Timezones
not permitted (time values must be in UTC time)  

  

dwAction  -  The action to perform as defined in CAL\_PROCESS\_xxx values  

  

dwRange  -  RANGE\_REPEAT\_xxx as defined above (ignored for non-repeating
entries)  

  

pszComments  -  Comments to include on the outgoing notice(s) to organizer or
participants (can be NULL).  

  

|    pExtActionInfo  -  Conveys any additional information required to perform
dwAction - NULL for actions that do not require additional information to
perform, required for CAL\_PROCESS\_DELEGATE,CAL\_PROCESS\_DECLINE and
CAL\_PROCESS\_COUNTER and CAL\_PROCESS\_UPDATEINVITEES.  

  

|    dwFlags  -  Flags - Only CAL\_ACTION\_UPDATE\_ALL\_PARTICIPANTS is allowed
(and only for CAL\_PROCESS\_UPDATEINVITEES)  

  

pCtx  -  RESERVED - MUST be NULL  

  




Output :  

(routine)  -  status of the function  

            NOERROR on success  

            ERR\_NULL\_DBHANDLE                                   The database
handle is NULL  

            ERR\_MISC\_INVALID\_ARGS                 Unexpected arguments provided  

            ERR\_CALACTION\_INVALID                 The action requested is not
valid for this entry  

            ERR\_NO\_CALENDAR\_FOUND             Unable to find the entry because
the required view does not exist in this database  

            ERR\_NOT\_FOUND                                          There are no
entries that match the specified UID in the database  

            ERR\_TDI\_CONV                                              The
recurrence ID specified cannot be interpreted  

            ERR\_MISC\_UNEXPECTED\_ERROR    Unexpected internal error  

  

  




 **See Also :**


**[CalCreateEntry](CalCreateEntry.md)**


**[CalReadEntry](CalReadEntry.md)**



----------------------------------------------------------------------------------------------------------


 





