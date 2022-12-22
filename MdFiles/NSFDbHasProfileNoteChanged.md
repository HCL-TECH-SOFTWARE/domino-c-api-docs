




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




**Initial Release 6.0.3**



**Function : Database**



**NSFDbHasProfileNoteChanged** **- Determine
whether a profile note has been modified since a given time.** 


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



STATUS
LNPUBLIC **NSFDbHasProfileNoteChanged(**  

      DBHANDLE  hDb,  

      NOTEID  noteid,  

      DWORD \*pSeqNum,  

      TIMEDATE \*Since,  

      BOOL \*HasChanged,  

      TIMEDATE \*retModTime**);**



**Description :**



This
function determines whether a profile note has been modified since a given
time.  The profile note modified sequence number for the database is also
checked.  If the profile note has been modifed, its modified time is returned ,
along with the current profile note modified sequence number.


 


**Parameters :**



Input :  

hDb  -  A handle to an open Domino database.  

  

noteid  -  The NOTEID of the note whose particulars you wish to retrieve.  

  

pSeqNum  -  Sequence number.  

  

Since  -  Timedate since.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR - Successfully retrieved the note information.  

  

ERR\_NOTE\_DELETED - Document has been deleted.  

  

ERR\_xxx - Errors returned by lower level functions.  There are so many possible
causes, that It is best to use the code in a call to OSLoadString and
display/log the error for the user.  

  

  

pSeqNum  -  Updated sequence number  

  

HasChanged  -  TRUE - Note has changed  FALSE - Note has not changed  

  

retModTime  -  Returns the populated TIMEDATE structure containing the note's
last modified time and date normalized to Greenwich Mean Time (GMT).  

  




 **See Also :**


**[EM\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/CCB2911F1DF6C7AF8525681000480140)**



----------------------------------------------------------------------------------------------------------


 





