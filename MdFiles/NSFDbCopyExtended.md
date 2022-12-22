




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




**Initial Release 4.0**



**Function : Database**



**NSFDbCopyExtended** **- Copies
notes from one database to another.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



STATUS
LNPUBLIC **NSFDbCopyExtended(**  

      DBHANDLE  hSrcDB,  

      DBHANDLE  hDstDB,  

      TIMEDATE  Since,  

      WORD  NoteClassMask,  

      DWORD  Flags,  

      TIMEDATE far \*retUntil**);**



**Description :**



This
function copies notes from one database to another.  You may specify two
conditions that will filter which notes are copied: a cutoff time/date, and a
NOTE\_CLASS\_xxx mask.  In addition, flag values may be used to control
additional options (the flags are described in the entry DBCOPY\_xxx).


 


The Cutoff
Date and Cutoff Interval (from the Replication Settings) are copied from the
source database to the destination database along with the selected notes.  

  




The TIMEDATE
of the most recent note copied may be obtained by supplying a pointer to a
TIMEDATE in the argument retUntil.  This argument is optional;  pass NULL if
this result is not wanted.


 


If the two
databases are replicas, the notes copied will appear as replicas.  If the
databases are not replicas, the notes copied will appear as new notes in the
destination database.


 


 


**Parameters :**



Input :  

hSrcDB  -  The handle of the souce database.  

  

hDstDB  -  The handle of the destination database.  

  

Since  -  A TIMEDATE structure that specifies the earliest note that is
copied.  To copy all notes, use TimeConstant() with the TimeConstantType
argument set to TIMEDATE\_WILDCARD.  

  

NoteClassMask  -  The classes of notes that are copied.  Note classes are
defined by the bit masks, NOTE\_CLASS\_xxx, and may be OR'ed together to copy
more than one class of notes.  

  

Flags  -  Option flags (see DBCOPY\_xxx).  DBCOPY\_DEST\_IS\_NSF,
DBCOPY\_DEST\_IS\_DB2, and DBCOPY\_OVERRIDE\_DEST are not supported.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success, or what
the error is.  The return codes include:  

  

NOERROR  

ERR\_NO\_MODIFIED\_NOTES  

  

  

retUntil  -  Optional;  if not NULL, the TIMEDATE of the most recent note
copied is stored at this address.  

  




 **See Also :**


**[NSFDbCopy](NSFDbCopy.md)**


**[DBCOPY\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/B6248E49ABC59CF08525629000533E97)**


**[NOTE\_CLASS\_xxx](NOTE_CLASS_xxx.md)**



----------------------------------------------------------------------------------------------------------


 





