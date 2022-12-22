




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



**Symbolic Value : Database**



**DBCOPY\_xxx** **-** Option flags
for NSFDbCopyExtended, NSFDbCreateAndCopy, and NSFDbCreateAndCopyExtended.


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**


 **Symbolic Values :**      DBCOPY\_REPLICA              -  New database is a replica of
the original.  

  

      DBCOPY\_SUBCLASS\_TEMPLATE   -  Copy template notes. Only supported for
NSFDbCopyExtended.  

  

      DBCOPY\_DBINFO2              -  Copy secondary header (such as database
quota information). This flag may only be used with a local database; using
this flag with a remote database will return the error ERR\_NOT\_LOCAL. Only
supported for NSFDbCopyExtended.  

  

      DBCOPY\_SPECIAL\_OBJECTS         -  Copy mail router objects. This flag may
only be used with a local database; using this flag with a remote database will
return the error ERR\_NOT\_LOCAL. Only supported for NSFDbCopyExtended.  

  

      DBCOPY\_NO\_ACL   -  Do not copy access control list. Only supported for
NSFDbCopyExtended.  

  

      DBCOPY\_NO\_FULLTEXT     -  Do not copy full text index. Only supported for
NSFDbCopyExtended.  

  

      DBCOPY\_ENCRYPT\_SIMPLE          -  Use simple encryption in new database.  

  

      DBCOPY\_ENCRYPT\_MEDIUM         -  Use middle level of encryption in new
database.  

  

      DBCOPY\_ENCRYPT\_STRONG        -  Use strongest level of encryption in new
database.  

  

      DBCOPY\_KEEP\_NOTE\_MODTIME   -  Do not update each note's modification
time. Only supported for NSFDbCopyExtended.  

  

      DBCOPY\_REPLICA\_NAMELIST       -  Copy the NameList (applicable only when
DBCOPY\_REPLICA is specified).  

  

      DBCOPY\_DEST\_IS\_NSF      -  Destination is NSF database. Only supported
for NSFDbCreateAndCopy and NSFDbCreateAndCopyExtended.  

  

      DBCOPY\_DEST\_IS\_DB2      -  Destination is DB2 database. Only supported
for NSFDbCreateAndCopy and NSFDbCreateAndCopyExtended.  

  

      DBCOPY\_OVERRIDE\_DEST            -  Destination should override default if
able to. Only supported for NSFDbCreateAndCopy and NSFDbCreateAndCopyExtended.  

  

>    DBCOPY\_COMPACT\_REPLICA       -  Create Db for copy style compaction.  

  




**Description :**



These
options are specified in the Flags parameter for NSFDbCopyExtended.
NSFDbCreateAndCopy, and NSFDbCreateAndCopyExtended.


 **See Also :**


**[NSFDbCopyExtended](NSFDbCopyExtended.md)**


**[NSFDbCreateAndCopy](NSFDbCreateAndCopy.md)**


**[NSFDbCreateAndCopyExtended](NSFDbCreateAndCopyExtended.md)**



----------------------------------------------------------------------------------------------------------


 





