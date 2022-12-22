




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Courier;
 panose-1:2 7 4 9 2 2 5 2 4 4;}
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



**NSFDbCopy** **- Copies
notes from one database to another.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



STATUS
LNPUBLIC **NSFDbCopy(**  

      DBHANDLE  hSrcDB,  

      DBHANDLE  hDstDB,  

      TIMEDATE  Since,  

      WORD  NoteClassMask**);**



**Description :**



This function
copies notes from one database to another.  You may specify two conditions that
will filter which notes are copied: a cutoff time/date, and a NOTE\_CLASS\_xxx
mask.


 


The Cutoff
Date and Cutoff Interval (from the Replication Settings) are copied from the
source database to the destination database along with the selected notes.


 


To create a
replica copy of a database, use NSFDbCopyExtended with the Flag DBCOPY\_REPLICA.


 


Please note
that NSFDbCopy does not copy the ACL or the database information buffer to the
destination database.  These operations can be completed using the appropriate
Database API functions.


 


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

  




Output :  

(routine)  -  Return status from this call -- indicates either success, or what
the error is.  The return codes include:  

  

NOERROR  

ERR\_NO\_MODIFIED\_NOTES  

  

  




 **Sample Usage :**


  

       /\* if New DB from a template \*/  

       if (error\_status = NSFDbCopy(db\_handle\_src, db\_handle\_dst,  

                              copy\_cutoff\_td, NOTE\_CLASS\_ALLNONDATA))  

           goto Exit;  

       if (error\_status = NSFDbCopyTemplateACL(db\_handle\_src,  

                              db\_handle\_dst, user\_name,  

                              ACL\_LEVEL\_MANAGER))  

           goto Exit;  

   }  

  




 **See Also :**


**[NSFDbCopyACL](NSFDbCopyACL.md)**


**[NSFDbCopyTemplateACL](NSFDbCopyTemplateACL.md)**


**[NSFDbInfoGet](NSFDbInfoGet.md)**


**[NSFDbInfoSet](NSFDbInfoSet.md)**


**[NSFDbReplicaInfoGet](NSFDbReplicaInfoGet.md)**


**[NSFDbReplicaInfoSet](NSFDbReplicaInfoSet.md)**


**[NOTE\_CLASS\_xxx](NOTE_CLASS_xxx.md)**



----------------------------------------------------------------------------------------------------------


 





