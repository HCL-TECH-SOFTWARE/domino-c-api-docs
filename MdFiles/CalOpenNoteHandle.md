




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



**CalOpenNoteHandle** **- This is a
method to get a note handle for an entry on the calendar.**


**----------------------------------------------------------------------------------------------------------**



**#include <calapi.h>**



STATUS **CalOpenNoteHandle(**  

      DBHANDLE  hDB,  

      const char\*pszUID,  

      const char\*pszRecurID,  

      NOTEHANDLE far \*rethNote,  

      DWORD  dwFlags,  

      void\*pCtx**);**



**Description :**



This is a
method to get a note handle for an entry on the calendar.


The
intent is that the note handle can be used to get information about an entry or
instance or to write additional information to the entry or instance (beyond
what is defined in iCalendar and/or available in this API).


It
is the callers responsibility to close the note via NSFNoteClose.


When
opening a recurring entry, a valid recurrence ID MUST also be provided.  A note
representing the single instance will be returned.


This
might cause notes to be created or modified as a side effect.


 


**Parameters :**



Input :  

hDB  -  The database containing the entry to open.  

  

pszUID  -  The UID of the entry to get a note handle for.  

  

pszRecurID  -  The RECURRENCE-ID of the instance to get a note handle for. 
Timezones not permitted (time values must be in UTC time). NULL for single
entries.  Must be present for recurring entries.  

  

dwFlags  -  CAL\_NOTEOPEN\_xxx flags to control non-default behavior. Supported:
CAL\_NOTEOPEN\_HANDLE\_NOSPLIT.  

  

pCtx  -  RESERVED - MUST be NULL.  

  




Output :  

(routine)  -  NOERROR on success  

ERR\_NULL\_DBHANDLE                                   The database handle is NULL  

ERR\_NO\_CALENDAR\_FOUND             Unable to find the entry because the required
view does not exist in this database  

ERR\_NOT\_FOUND                                          There are no entries
that match the specified UID or UID/recurid in the database  

ERR\_MISC\_INVALID\_ARGS                 Unexpected arguments provided  

ERR\_TDI\_CONV                                              The recurrence ID
specified cannot be interpreted  

ERR\_MISC\_UNEXPECTED\_ERROR    Unexpected internal error  

  

  

rethNote  -  The returned open note handle of the calendar entry.  

  




 




----------------------------------------------------------------------------------------------------------


 





