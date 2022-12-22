




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



**CalGetUIDfromNOTEID** **- This is a
convinience method that returns a UID from a NOTEID.**


**----------------------------------------------------------------------------------------------------------**



**#include <calapi.h>**



STATUS **CalGetUIDfromNOTEID(**  

      DBHANDLE  hDB,  

      NOTEID  noteid,  

      char\*pszUID,  

      WORD  wLen,  

      void\*pReserved,  

      DWORD  dwFlags,  

      void\*pCtx**);**



**Description :**



This is a
convinience method that returns a UID from a NOTEID.  NOTEID->UID is a many
to one mapping since one or several notes may represent a calendar entry
(especially if it repeats) and its related notices.


As
such, the UID output will be the same for all notes that refer to the same
calendar entry.


This
method may incur a note open, so there could be performance impact.


 


**Parameters :**



Input :  

hDB  -  The database containing the note referenced by noteid.  

  

noteid  -  NOTEID of a calendar note.  

  

wLen  -  Length of pszRetUID buffer(reccomended to be at least 64).  

  

pReserved  -  RESERVED - MUST be NULL.  

  

dwFlags  -  Flags - none currently.  

  

pCtx  -  RESERVED - MUST be NULL.  

  




Output :  

(routine)  -  NOERROR on success  

ERR\_NULL\_DBHANDLE                                   The database handle is NULL  

ERR\_INVALID\_NOTE                           Note is not valid or is not a
calendar note  

ERR\_MISC\_INVALID\_ARGS                 Unexpected arguments provided  

ERR\_VALUE\_LENGTH                         The value is too long for the
allocated buffer  

  

  

pszUID  -  Buffer to populate with the UID.  

  




 




----------------------------------------------------------------------------------------------------------


 





