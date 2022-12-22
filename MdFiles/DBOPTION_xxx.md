




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



**DBOPTION\_xxx** **-** Database
option flags.


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**


 **Symbolic Values :**      DBOPTION\_FT\_INDEX        -  Enable full text indexing.  

  

      DBOPTION\_IS\_OBJSTORE             -  TRUE if database is being used as an
object store.  

  

      DBOPTION\_USES\_OBJSTORE        -  TRUE if database has notes which refer
to an object store.  

  

      DBOPTION\_OBJSTORE\_NEVER     -  TRUE if notes in this database never use
an object store.  

  

      DBOPTION\_IS\_LIBRARY     -  TRUE if database is a library.  

  

      DBOPTION\_UNIFORM\_ACCESS      -  TRUE if uniform access control should be
enforced across all replicas.  

  

      DBOPTION\_OBJSTORE\_ALWAYS   -  TRUE if NoteUpdate of notes in this
database should always try to use an object store.  

  

      DBOPTION\_NO\_BGAGENT             -  TRUE if database has no background
agent.  

  

      DBOPTION\_OUT\_OF\_SERVICE       -  TRUE if database is out-of-service, no
new opens allowed.  

  

      DBOPTION\_IS\_PERSONALJOURNAL          -  TRUE if database is a personal
journal.  

  

      DBOPTION\_MARKED\_FOR\_DELETE           -  TRUE if database is marked for
delete. No new opens are allowed; the database will be deleted when the
reference count = 0.  

  

      DBOPTION\_HAS\_CALENDAR          -  TRUE if database stores calendar
events.  

  

      DBOPTION\_IS\_CATALOG\_INDEX    -  TRUE if database is a catalog index.  

  

      DBOPTION\_IS\_ADDRESS\_BOOK    -  TRUE if database is an Address book or
Domino Directory.  

  

      DBOPTION\_IS\_SEARCH\_SCOPE    -  TRUE if database is a
"multi-db-search" repository.  

  

      DBOPTION\_IS\_UA\_CONFIDENTIAL             -  TRUE if database's user
activity log is confidential, only.  

  

      DBOPTION\_RARELY\_USED\_NAMES           -  TRUE if item names are to be
treated as if the ITEM\_RARELY\_USED\_NAME flag is set.  

  

      DBOPTION\_IS\_SITEDB       -  TRUE if db is a "multi-db-site"
repository.  

  




**Description :**



These option
flags apply to the whole database.  These flags may be read using
NSFDbGetOptions() and modified using NSFDbSetOptions().


 


NSFDbGetOptions
will not return the DBOPTION\_OBJSTORE\_xxx flags (even if any are set in the
database) if the specified database is a remote database.  NSFDbSetOptions will
not set the DBOPTION\_OBJSTORE\_xxx flags if the specified database is a remote
database. 


 **See Also :**


**[NSFDbGetOptions](NSFDbGetOptions.md)**


**[NSFDbSetOptions](NSFDbSetOptions.md)**



----------------------------------------------------------------------------------------------------------


 





