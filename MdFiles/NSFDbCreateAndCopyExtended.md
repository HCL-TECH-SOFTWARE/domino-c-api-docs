




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




**Initial Release 6.0.2**



**Function : Clusters; Database**



**NSFDbCreateAndCopyExtended** **- Creates a
new copy of a database based on the original.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



STATUS
LNPUBLIC **NSFDbCreateAndCopyExtended(**  

      const char far \*srcDb,  

      const char far \*dstDb,  

      WORD  NoteClass,  

      WORD  limit,  

      DWORD  flags,  

      DHANDLE  hNames,  

      DBHANDLE far \*DBHANDLE far \***);**



**Description :**



This
function creates a new copy of a Domino database based on the one supplied in
SrcPathName and allows for a NAMES\_LIST structure UserName to provide
authentication for trusted servers.  The database class of the new database is
based on the file extension specified by SrcPathName.  Specifically, the new
copy will contain the replication settings, database options, Access Control
List, Full Text Index (if any),  as well as data and non-data notes (dependent
on the NoteClass argument) of  the original database. 


 


You may
specify the types of notes that you want copied to the new database with the
NoteClass argument.  You may also specify the maximum size (database quota)
that the database can grow to (in megabytes) with the Limit argument. 
Additionally, you may specify that the new database is to be a replica copy of
the original database, meaning that it will share the same replica ID.  If
successful, this function will return a handle to the newly created Domino
database in rethDB.  The handle can then be used in other C API functions that
accept a DBHANDLE as input.  You will need to call NSFDbClose to close the
newly created database when done with the handle.


 


If the
source database is a replica copy that has not yet been initialized or the
replication settings in the source database are set to never replicate,  then a
new copy will not be permitted if the DBCOPY\_REPLICA flag is set.


 


Note: 
NFSDbCreateAndCopy will return the error ERR\_NOACCESS if the source database is
located on a server and contains private design elements (view, folder, etc...)
not owned by the current user and the NOTE\_CLASS\_PRIVATE flag is not cleared in
the NoteClass argument.


 


**Parameters :**



Input :  

srcDb  -  A fully qualified pathname of the source database.  

  

dstDb  -  A fully qualified pathname of the destination database.  

  

NoteClass  -  Class of notes to be copied.  This field may specify more than
one NoteClass by passing a Bitwise OR of NOTE\_CLASS constants.  

  

limit  -  Size limit for new database.  Specified in megabytes (e.g. a value of
1 indicates size limit of 1 MB).  This argument will control how large the new
copy can grow to.  Specify a value of zero if you do not wish to place a size
limit on the newly copied database.  

  

flags  -  Option flags determining type of copy.  Currently, the only supported
flags are DBCOPY\_REPLICA, , DBCOPY\_ENCRYPT\_SIMPLE, DBCOPY\_ENCRYPT\_MEDIUM,
DBCOPY\_ENCRYPT\_STRONG, DBCOPY\_REPLICA\_NAMELIST, DBCOPY\_DEST\_IS\_NSF,
DBCOPY\_DEST\_IS\_DB2, and DBCOPY\_OVERRIDE\_DEST.  

  

If the DBCOPY\_REPLICA flag is set then the newly copied database will be a
replica copy of the original database.  If the DBCOPY\_REPLICA flag is not set
then the new copy will have a unique replica ID.  

  

hNames  -  May be NULLHANDLE or a HANDLE to a NAMES\_LIST structure that
contains a UserName that is used to provide authentication for trusted
servers.  This causes the UserName's ACL permissions in the database to be
enforced.  Please see NSFBuildNamesList for more information on building a
NAMES\_LIST structure.  

  




Output :  

(routine)  -  If successful,  returns NOERROR; otherwise, returns database
access errors.  

  

  

DBHANDLE far \*  -  Address of location to store handle to newly created
database.  

  




 **See Also :**


**[DBCOPY\_xxx](notes:///852584E300582C9D/61FD4E9848264AD28525620B006BA8BD/B6248E49ABC59CF08525629000533E97)**


**[NOTE\_CLASS\_xxx](NOTE_CLASS_xxx.md)**


**[NSFDbCreateAndCopy](NSFDbCreateAndCopy.md)**



----------------------------------------------------------------------------------------------------------


 





