




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
 /\* List Definitions \*/
 ol
 {margin-bottom:0cm;}
ul
 {margin-bottom:0cm;}
-->




**Initial Release 7.0**



**Function : Backup; Database; DB2**



**NSFDB2ReconnectNotesDatabase** **- Make sure
that Domino can access NSFDB2 data for FullPath or rename the NSFDB2 database
within the Domino server** 


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



STATUS
LNPUBLIC **NSFDB2ReconnectNotesDatabase(**  

      const char far \*FullPath,  

      const char far \*String1,  

      DWORD  nsfid,  

      DWORD  flags**);**



**Description :**



A utility
function to make sure the infrastructure is in place such that Domino can
access NSFDB2 data for FullPath.   This can also be used to effectively rename
the NSFDB2 database within the Domino server by assigning a new FullPath if
nsfid is provided.


 


String1
defines a logical grouping of NSFDB2 databases.  For DB2 UDB on LUW, the *groupName* 
should be synonymous with DB2 tablespace name.   If FullPath is NULL or an
empty string, and DB2BACKUP\_NONSFID is passed as nsfid, all NSFDB2 databases
specified by *String1* will be reconnected.  This will be useful for UDB
9.1 where a missing tablespace could be restored to the current DB2 database or
another DB2 database.


 


This
function will only affect the current server's data directory.  It can not be
executed on a remote server.


 


**Algorithm :**


*       
If *FullPath*  or *nsfid*  is provided, scan all
properties tables in the tablespace specified by *string1,* until we find
one in a schema that claims to containing data for *FullPath*. or *nsfid*


*       
Iff one row is found:


*       
Extract the NSFID from the properties table found in the above
step.


*       
Update Domino's CATALOG table.


*       
Make sure link file on  Domino server's file system exists.


*       
If DB2BACKUP\_FASTCONNECT is not specified as an option, restore
function and trigger definitions for access tables & views, removing old
values if necessary.


*       
If DB2BACKUP\_NOREPLICA is specified in flags, regenerate the
REPLICA ID of this database.


*       
Else return ERR\_DB2NSF\_IDENTIFIER\_INVALID.


*       
If FullPath and nsfid was not provided


*       
Reconnect NSFDB2 databases discovered in the DB2 tablespace by
scanning PROPERTIES table in *groupName* for NSFDB2 data and verifying the
data actually exists.  Reconnect the NSFDB2 database as described above.


 


 


**Parameters :**



Input :  

FullPath  -  Relative to the Domino server's data directory.  This does not
have to be the same as the original path.  

  

String1  -  NSFDB2 group (DB2 tablespace) containing the NSFDB2 database you
wish to reconnect.  

  

  

nsfid  -  (optional) Normally pass DB2BACKUP\_NONSFID so parameter is ignored. 
Otherwise, Domino unique internal identifier for FullPath..  

  

flags  -  optional.    

          See DB2BACKUP\_xxx.  

  




Output :  

(routine)  -  STATUS, including the following:  

NOERROR  

ERR\_DB2NSF\_CLI\_ERROR - Internal DB2/CLI error.  

ERR\_DB2NSF\_NOT\_ENABLED\_FOR\_DB2 - The Domino server is not enabled for DB2.  

ERR\_DB2NSF\_IDENTIFIER\_INVALID  - If the tablespace (or schema for iSeries)
specified is invalid or doesn't contain data for the NSFDB2 database specified
by FullPath  

ERR\_EXISTS - The file specified by FullPath already exists and is not a link
file for a NSFDB2 database, or it exists in another DB2 tablespace or schema.  

  

  




 **See Also :**


**[DB2BACKUP\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/4D455E10ABF8DF9F85256E85004A2764)**


**[NSFDB2GetInfo](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/406189AFDCB6E04385256E60004A00D1)**


**[NSFDB2GetServerInfo](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/F4041BDF22D5C4B585256E60004CAE77)**


**[NSFDB2ListNSFDB2Databases](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/A57AF7CF730AA01685256E6000560BE5)**


**[NSFDB2RegenerateLinks](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/986F1A03FA32C49985256E600055985D)**



----------------------------------------------------------------------------------------------------------


 





