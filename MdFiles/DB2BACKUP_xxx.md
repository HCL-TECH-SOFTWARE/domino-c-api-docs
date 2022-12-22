




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




**Initial Release 7.0**



**Symbolic Value : Backup; DB2**



**DB2BACKUP\_xxx** **-** NSFDB2
reconnect flags.


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**


 **Symbolic Values :**      DB2BACKUP\_FASTCONNECT         -  Does not attempt to
regenerate access views, tables, and add function and trigger definitions for
access tables and views. This is useful if the caller knows that this work is
unnecessary as the row data hasn't changed since the NSFDB2 database was taken
offline.  

  

      DB2BACKUP\_NEWREPLICA            -  Modifies replica ID of targetNSF in an
effort to permanently disable replication for this Notes database.  

  

      DB2BACKUP\_COPY\_REPLACE        -  Indicates that the caller is
intentionally going to erase and replace the table data currently in use for
targetNSF. Otherwise, if targetNSF exists, the error ERR\_DB2NSF\_SCHEMA\_INUSE
will be returned.  

  

  

      DB2BACKUP\_COPY\_DELETE\_SRC             -  Deletes NSFDB2 data for
sourceNSF and removes the reference to the NSFDB2 database.  

  

      DB2BACKUP\_COPY\_ISOLATE         -  The groupName argument is ignored.
targetNSF is placed in its own NSFDB2 group. The group (tablespace) name will
be generated.  

  

      DB2BACKUP\_COPY\_CLOSE            -  Closes the NSFDB2 "database
group" now containing targetNSF such that it can no longer receive
additional NSFDB2 databases. This can be used in conjunction with groupName to
effectively move or copy an NSFDB2 database into a DB2 tablespace (NSFDB2
group) by itself.  

  

      DB2BACKUP\_COPY\_NONRECOVERABLE   -  Performs a non-recoverable load into
targetNSF. The load will be recoverable by default. See loadCopyLocation.  

  

      DB2BACKUP\_COPY\_IGNORE\_NIF   -  Do not copy table data associated with
views (NIF).  

  

      DB2BACKUP\_COPY\_VENDOR\_LOAD          -  Use this option to treat
loadParameter as the vendor supplied DB LOAD module.  

  

      DB2BACKUP\_NONSFID       -  Pass this to NSFDB2ReconnectNotesDatabase to
defer to the NSFID matching the FullPath stored in the properties table of the
tablespace instead of the NSFID passed to this function.  

  




**Description :**



These values
are optional values for the flags parameter of NSFDB2ReconnectNotesDatabase.  


 **See Also :**


**[NSFDB2FastCopy](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/57EBAEBF5D94B22F8525705A0011D760)**


**[NSFDB2ReconnectNotesDatabase](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/F551E2856602672185256E600054B6EC)**



----------------------------------------------------------------------------------------------------------


 





