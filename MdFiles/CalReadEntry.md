




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



**CalReadEntry** **- This will
return complete iCalendar data for the specified entry.**


**----------------------------------------------------------------------------------------------------------**



**#include <calapi.h>**



STATUS **CalReadEntry(**  

      DBHANDLE  hDB,  

      const char\*pszUID,  

      const char\*pszRecurID,  

      MEMHANDLE far \*hRetCalData,  

      DWORD\*pdwReserved,  

      DWORD  dwFlags,  

      void\*pCtx**);**



**Description :**




This
will return complete iCalendar data for the specified entry.  


For
recurring entries, this may result in multiple VEVENTs in the returned
iCalendar data.  In this case, the first VEVENT represents the recurrence set
and additional entries represent exceptions to the recurrence set.


All
instances that differ from the recurrence set will be returned as additional
VEVENTs containing the exceptional data. There is no concept of 'runs' of
instances or RANGE of instances.


Alternatively,
a specific instance may be requested using pszRecurID and only the data for
that instance will be returned.


Returned
data will not include rich text description.


All
participants of a meeting will be returned as PARTSTAT=NEEDS-ACTION even if
they have responded.


 


**Parameters :**



Input :  

hDB  -  The database from which entries are returned.  

  

pszUID  -  The UID of the entry to be returned.  

  

pszRecurID  -  NULL for single entries or to read data for an entire recurring
series.If populated, this is the RECURRENCE-ID of the specific instance to
read.  

  

pdwReserved  -  RESERVED - MUST be NULL  

  

dwFlags  -  CAL\_READ\_xxx flags to control non-default behavior  

  

pCtx  -  RESERVED - MUST be NULL  

  




Output :  

(routine)  -  status of read entry  

            NOERROR on success  

            ERR\_NULL\_DBHANDLE                                   The database
handle is NULL  

            ERR\_MISC\_INVALID\_ARGS                 Unexpected arguments provided  

            ERR\_TDI\_CONV                                              The
recurrence ID specified cannot be interpreted  

            ERR\_NO\_CALENDAR\_FOUND             Unable to find the entry because
the required view does not exist in this database  

            ERR\_NOT\_FOUND                                          There are no
entries that match the specified UID or UID/recurid in the database  

            ERR\_NOTE2ICAL\_CONVERT              Unable to convert to iCalendar  

            ERR\_MISC\_UNEXPECTED\_ERROR    Unexpected internal error  

  

  

hRetCalData  -  Handle to the returned iCalendar data.  It is the caller's
responsibility to free this memory.  

  




 




----------------------------------------------------------------------------------------------------------


 





