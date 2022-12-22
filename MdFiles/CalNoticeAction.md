




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



**CalNoticeAction** **- Process a
calendar notice.**


**----------------------------------------------------------------------------------------------------------**



**#include <calapi.h>**



STATUS **CalNoticeAction(**  

      DBHANDLE  hDB,  

      NOTEID  noteID,  

      DWORD  dwAction,  

      const char\*pszComments,  

      PEXT\_CALACTION\_DATA  pExtActionInfo,  

      DWORD  dwFlags,  

      void\*pCtx**);**



**Description :**



Process a
calendar notice. This makes the appropriate modifications to the calendar entry
and also sends appropriate notices out.


 


**Parameters :**



Input :  

hDB  -  The database containing the notice to act on.  

  

noteID  -  The noteid of the notice to act on.  

  

dwAction  -  The action to perform as defined in CAL\_PROCESS\_xxx values.  

  

pszComments  -  Comments to include on the outgoing notice(s) to organizer or participants
(can be NULL).  

  

pExtActionInfo  -  Conveys any additional information required to perform
dwAction - NULL for actions that do not require additional information to
perform, required for CAL\_PROCESS\_DELEGATE and CAL\_PROCESS\_COUNTER.  

  

dwFlags  -  Flags - (a CAL\_ACTION \_xxx value).  

  

pCtx  -  RESERVED - MUST be NULL.  

  




 


 




----------------------------------------------------------------------------------------------------------


 





