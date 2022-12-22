




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



**CalReadNotice** **- This will
return iCalendar data representing a notice with the specified NOTIED.**


**----------------------------------------------------------------------------------------------------------**



**#include <calapi.h>**



STATUS **CalReadNotice(**  

      DBHANDLE  hDB,  

      NOTEID  noteID,  

      MEMHANDLE far \*hRetCalData,  

      void\*pReserved,  

      DWORD  dwFlags,  

      void\*pCtx**);**



**Description :**



This will
return iCalendar data representing a notice with the specified NOTIED.  A
notice may not yet be applied to the calendar entries itself, but an
application may want to read the notice (and process it).  Examples of notices
include invitations, reschedules, information updates, confirmations,
cancelations, counterproposals, requests for information, acceptances,
declines, tenative acceptances, etc.


 


**Parameters :**



Input :  

hDB  -  The database from which entries are returned.  

  

noteID  -  The NOTEID of the notice to be returned.  

  

pReserved  -  RESERVED - MUST be NULL.  

  

dwFlags  -  CAL\_READ\_xxx flags to control non-default behavior. Supported:
CAL\_READ\_HIDE\_X\_LOTUS, CAL\_READ\_INCLUDE\_X\_LOTUS.  

  

pCtx  -  RESERVED - MUST be NULL.  

  




Output :  

hRetCalData  -    

  




 




----------------------------------------------------------------------------------------------------------


 





