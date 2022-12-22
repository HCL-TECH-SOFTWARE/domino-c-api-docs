




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



**CalCreateEntry** **- Creates a
calendar entry.**


**----------------------------------------------------------------------------------------------------------**



**#include <calapi.h>**



STATUS **CalCreateEntry(**  

      DBHANDLE  hDB,  

      const char\*pszCalEntry,  

      DWORD  dwFlags,  

      MEMHANDLE\*hRetUID,  

      void\*pCtx**);**



**Description :**




Creates
a calendar entry.  This supports either a single entry, or a recurring entry
which may contain multiple VEVENTS represenging both the series and exception
data.The iCalendar input must only contain data for a single UID.For meetings,
ATTENDEE PARTSTAT data is ignored.If the mailfile owner is the meeting
organizer, invitations will be sent out to meeting participants (unless
CAL\_WRITE\_DISABLE\_IMPLICIT\_SCHEDULING is specified)


 


 


**Parameters :**



Input :  

hDB  -  The database where the entry will be created.  

  

pszCalEntry  -  The iCalendar data representing the entry to create  

  

dwFlags  -  CAL\_WRITE\_xxx flags to control non-default behavior  

  

pCtx  -  RESERVED - MUST be NULL  

  




Output :  

(routine)  -  status of create entry  

            NOERROR on success  

            ERR\_NULL\_DBHANDLE                                   The database
handle is NULL  

            ERR\_MISC\_INVALID\_ARGS                 Unexpected arguments provided  

            ERR\_NO\_CALENDAR\_FOUND             Unable to find the entry because
the required view does not exist in this database  

            ERR\_EXISTS                                       An entry already
exists  

            ERR\_CS\_PROFILE\_NOOWNER           Calendar Profile does not specify
owner  

            ERR\_UNEXPECTED\_METHOD            Provided iCalendar contains a
method (no method expected here)  

            ERR\_MissingVEventComponents                      Missing required
VEvent components  

            ERR\_InvalidVEventPropertyFound         Invalid VEvent property found,
such as mismatched UIDs  

            ERR\_ICAL2NOTE\_CONVERT              Error interpereting iCalendar
input  

            ERR\_MISC\_UNEXPECTED\_ERROR    Unexpected internal error  

            ERR\_IMPLICIT\_SCHED\_FAILED          Entry created, but errors were
encountered sending notices to meeting participants  

  

  

hRetUID  -  If non-null, the UID of the created iCalendar will be placed here  

  




 **See Also :**


**[CalReadEntry](CalReadEntry.md)**



----------------------------------------------------------------------------------------------------------


 





