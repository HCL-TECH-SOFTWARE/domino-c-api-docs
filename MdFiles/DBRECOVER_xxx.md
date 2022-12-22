




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




**Initial Release 5.0**



**Symbolic Value : Backup**



**DBRECOVER\_xxx** **-** Flags to
control how databases are recovered.


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**


 **Symbolic Values :**      DBRECOVER\_WAIT             -  Indicates the recovery should
wait for resources to become available, instead of returning with a error of
ERR\_RM\_SCAN\_IN\_PROGRESS. The most common busy resource is another recovery in
progress.  

  

      DBRECOVER\_ZAP\_ID          -  Indicates the databases instance id (DBIID)
should be refreshed with a new value after the recovery, thus allowing access
to the original DB as well as this recovered version. This is a new instance,
i.e. you will have to create a new backup after the recovery if you want the
ability to recover the new instance.  

  

      DBRECOVER\_REFRESH\_BACKUP              -  Indicates you want to
"roll-forward" the backup but keep it as a backup. This would be used
to keep backups current if the cost of doing the backup is higher than the cost
of a refresh. This option cannot be used with DBRECOVER\_ZAP\_ID.  

  

      DBRECOVER\_POINT\_IN\_TIME        -  Indicates you want recover a database,
not to the current time but to a selected time passed in the recoveryTime
parameter. All updates completed prior to the selected time will appear in the
recovered database but no latter ones. This option will always assign a new
DBIID (see DBRECOVER\_ZAP\_ID). This option cannot be used with
DBRECOVER\_REFRESH\_BACKUP.  

  

      DBRECOVER\_ZAP\_REPLICAID       -  Indicates you want the replica ID to be
reset on the recovered database so it is will not conflict with the original
database when replicating. This option will always assign a new DBIID (see
DBRECOVER\_ZAP\_ID). This option cannot be used with DBRECOVER\_REFRESH\_BACKUP.  

  

      DBRECOVER\_ZAP\_ID\_IF\_NECESSARY       -  Make recovered DB a new instance
if another copy of the DB with the same instance ID is on-line. Otherwise use
the same instance ID, thus avoiding the need for creating a new backup.  

  

      DBRECOVER\_ALT\_RETRIEVE\_PATH          -  Enables restoration of previously
archived transaction log extent files to an alternate location during Media
Recovery, when ARCHIVE style transaction logging is being used. Normally, the
archived transaction log extent files are restored directly to the transaction
log directory. Use of this flag can improve performance during database
recovery . When this flag is specified, the LogSegmentPathName parameter of the
LOGRESTORECALLBACKFUNCTION is filled in with the path location where previously
archived extents are to be placed. The code which calls NSFRecoverDatabases
should specifiy this location by setting the TRANSLOG\_RECOVER\_PATH value in
NOTES.INI .   

  

Note: Although a path relative to the Domino directory is valid, to avoid
ambiguity, specifying an absolute path for the TRANSLOG\_RECOVER\_PATH value is
recommended.  

  




**Description :**



Flags to
control how databases are recovered using NSFRecoverDatabases.


 **See Also :**


**[NSFRecoverDatabases](NSFRecoverDatabases.md)**



----------------------------------------------------------------------------------------------------------


 





