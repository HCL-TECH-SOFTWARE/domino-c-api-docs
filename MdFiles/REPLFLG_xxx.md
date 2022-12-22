




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




 


**Symbolic Value : Database;
Replication**



**REPLFLG\_xxx** **-** Replication
Flags.


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdata.h>**


 **Symbolic Values :**      REPLFLG\_DISABLE             -  If set, the Server's
Replicator Task ignores this database. Enable replication by clearing this bit.  

  

      REPLFLG\_IGNORE\_DELETES         -  If set, don't propogate deleted notes
(deletion stubs), when replicating from this database. Enable propogation by
clearing this bit.  

  

      REPLFLG\_HIDDEN\_DESIGN            -  If set, hide the design of this
database. Disable hide design by clearing this bit.  

  

      REPLFLG\_DO\_NOT\_CATALOG       -  If set, Server's Catalog Task will not
add this database to CATALOG.NSF. Enable cataloging by clearing this bit.  

  

      REPLFLG\_CUTOFF\_DELETE           -  If set, the Server's Replicator Task
automatically deletes notes that are older than the cutoff date. Disable
automatic document deletions by clearing this bit.  

  

      REPLFLG\_NEVER\_REPLICATE       -  If set, the Server's Replicator Task
Ignores this database. Enable replication by clearing this bit. Since this can
only be done programatically, it is a more bullet-proof method than
REPLFLG\_DISABLE, which can be modified from the user interface.  

  

      REPLFLG\_ABSTRACT         -  If set, truncate large documents and remove
attachments. Disable truncation by clearing this bit.  

  

      REPLFLG\_DO\_NOT\_BROWSE         -  If set, do not list in Open Database
dialog box. Enable listing in Open Database dialog box by clearing this bit.  

  

      REPLFLG\_NO\_CHRONOS   -  If set, disable background macros for this
database. Enable background macros by clearing this bit.  

  

      REPLFLG\_IGNORE\_DEST\_DELETES          -  If set, don't replicate deleted
notes  

 into destination database.  

  

      REPLFLG\_MULTIDB\_INDEX            -  Include in Multi Database indexing.  

  

      REPLFLG\_PRIORITY\_LOW              -  If set, replicator has low priority.  

  

      REPLFLG\_PRIORITY\_MED              -  If set, replicator has medium
priority.  

  

      REPLFLG\_PRIORITY\_HI      -  If set, replicator has high priority.  

  

      REPLFLG\_PRIORITY\_SHIFT            -  Shift count for prioirty field
within the WORD member.  

  

      REPLFLG\_PRIORITY\_MASK            -  Mask for priority field after
shifting.  

  

      REPLFLG\_PRIORITY\_INVMASK      -  Mask for clearing the priority field.  

  

      REPLFLG\_USED\_MASK       -  Mask for determining whether any of the
replication flags are set.  

  

      REPLFLG\_UNREADIFFNEW            -  If set, modified documents are not
marked as unread.  

  




**Description :**



These flags
are used by the Server's Replicator Task to control just what is done and not
done during the replication process on a per-database level.  

  

Note that you cannot set the replicate database title, categories, and template
option with the C API.  

  

The flags REPALFLG\_DO\_NOT\_CATALOG, REPALFLG\_HIDDEN\_DESIGN,
REPLFLG\_DO\_NOT\_BROWSE, and REPALFLG\_NO\_CHRONOS refer to the Database
Information, Other Settings options.  

  

Note the distinction between REPLFLG\_DISABLE and REPLFLG\_NEVER\_REPLICATE. The
former is used to temporarily disable replication.  The latter is used to
indicate that this database should NEVER be replicated.  The former may be set
and cleared by the Notes user interface. The latter is intended to be set
programmatically and SHOULD NEVER be able to be cleared by the user interface. 
The latter was invented to avoid having to set the replica ID to the known
value of REPLICA\_ID\_NEVERREPLICATE.  This latter method has the failing that
databases  that use it cannot have DocLinks to them.


 **See Also :**


**[NSFDbReplicaInfoGet](NSFDbReplicaInfoGet.md)**


**[NSFDbReplicaInfoSet](NSFDbReplicaInfoSet.md)**


**[DBREPLICAINFO](DBREPLICAINFO.md)**



----------------------------------------------------------------------------------------------------------


 





