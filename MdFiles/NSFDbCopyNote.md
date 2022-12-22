




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



**NSFDbCopyNote** **- Copy a
single note from one database to another.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



STATUS
LNPUBLIC **NSFDbCopyNote(**  

      DBHANDLE  hSrcDB,  

      DBID far \*SrcDbID,  

      DBID far \*SrcReplicaID,  

      NOTEID  SrcNoteID,  

      DBHANDLE  hDstDB,  

      DBID far \*DstDbID,  

      DBID far \*DstReplicaID,  

      NOTEID far \*retDstNoteID,  

      WORD far \*retNoteClass**);**



**Description :**



This
function copies a single note from a source database to the destination
database.  This routine detects if the source and destination databases are
replicas of each other, and sets ID information in reference items in notes
appropriately.  If the two databases are replicas of each other, the internal
identifier (OID) is preserved during the copy, so the two notes appear as
replicas of each other.  This function can also be used to copy notes between
non-replica databases or between totally unrelated databases.  The copy
operation does NOT flush the I/O buffers in the destination database to disk
until the destination database is closed, in order to improve the speed of a
repeated number of calls to this function.


 


**Parameters :**



Input :  

hSrcDB  -  A database handle to the source database.  

  

SrcDbID  -  Not used.  Pass NULL for this parameter.  

  

SrcReplicaID  -  Optional.  A pointer to the replica ID (also a DBID) of the
source database.  NULL may be used for this pointer.  If you pass in NULL for
this value, SrcReplicaID will be determined by using the hSrcDb.  Pass in a
pointer to the replica ID of the source database, if you happen to already have
the ID, to optimize this call.  

  

SrcNoteID  -  The NOTEID of the source note.  

  

hDstDB  -  A database handle to the destination database.  

  

DstDbID  -  Optional.  A pointer to the database ID (DBID) of the destination
database.  NULL may be used for this pointer.  

  

DstReplicaID  -  Optional.  A pointer to the replica ID (also a DBID) of the
destination database.  NULL may be used for this pointer.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR - Successfully copied note to destination database.  

ERR\_NOTE\_DELETED - Document has been deleted.  

ERR\_xxx - Errors returned by lower level functions.  There are so many possible
causes, that It is best to use the code in a call to OSLoadString and
display/log the error for the user.  

  

  

retDstNoteID  -  Optional.  The address of a NOTEID in which the Note ID of the
newly copied note is returned.  Use NULL if you do not need this returned
information.  If the Note copy is created in a non-replica database, a new
Originator ID (OID) will be generated, so that the copy appears as a unique new
note in the destination database.  

  

retNoteClass  -  Optional.  The address of a WORD in which the NOTE\_CLASS\_xxx
of the copy is returned.  Use NULL if you do not need this returned
information.  

  




 **Sample Usage :**



if (error\_status =
NSFDbCopyNote(db\_handle\_src,  

                                 NULL,  

                                 &replica\_info\_src.ID,


                                
policy\_nid\_src,  

                                 db\_handle\_dst,


                                
&database\_id\_dst,  

                                 &replica\_info\_dst.ID,


                                
&policy\_nid\_dst,  

                                 &copy\_class))  

  goto Exit;


 **See Also :**


**[NSFDbCopy](NSFDbCopy.md)**


**[NSFDbCopyNoteExt](NSFDbCopyNoteExt.md)**


**[NSFDbIDGet](NSFDbIDGet.md)**



----------------------------------------------------------------------------------------------------------


 





