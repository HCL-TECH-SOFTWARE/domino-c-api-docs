




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:"Tms Rmn";
 panose-1:2 2 6 3 4 5 5 2 3 4;}
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




 


**Function : Database**



**NSFDbGetNoteInfoByUNID** **- Get 
information from a note's on-disk header.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



STATUS
LNPUBLIC **NSFDbGetNoteInfoByUNID(**  

      DBHANDLE  hDB,  

      UNID far \*pUNID,  

      NOTEID far \*retNoteID,  

      OID far \*retOID,  

      TIMEDATE far \*retModTime,  

      WORD far \*retClass**);**



**Description :**



This
function takes a database handle and Universal Note ID.  It returns the note
id, the note's Originator ID (OID) structure, the time and date the note was
last modified, and the NOTE\_CLASS\_xxx. 


 


**Parameters :**



Input :  

hDB  -  A handle to an open Domino database.  

  

pUNID  -  The Universal Note ID.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR - Successfully retrieved the note information.  

  

ERR\_NOTE\_DELETED - Document has been deleted.  

  

ERR\_xxx - Errors returned by lower level functions.  There are so many possible
causes, that It is best to use the code in a call to OSLoadString and
display/log the error for the user.  

  

  

retNoteID  -  (Optional)  Pointer to the returned note id;  may be NULL.  

  

retOID  -  (Optional)  Pointer to the returned populated ORIGINATORID (OID)
structure containing the database creation time/date, note creation time/date,
note sequence number, and the sequence time/date (when added to database).  May
be NULL.  

  

retModTime  -  (Optional)  Pointer to the returned populated TIMEDATE structure
containing the note's last modified time and date normalized to Greenwich Mean
Time (GMT).  May be NULL.  

  

retClass  -  (Optional)  Pointer to the returned NOTE\_CLASS\_xxx (type of
note);  may be NULL.  

  




 **See Also :**


**[NSFDbGetNoteInfo](NSFDbGetNoteInfo.md)**



----------------------------------------------------------------------------------------------------------


 





