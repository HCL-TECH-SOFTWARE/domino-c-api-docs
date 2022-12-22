




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



**NSFDbReplicaInfoSet** **- Set the
database's DBREPLICAINFO structure.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



STATUS
LNPUBLIC **NSFDbReplicaInfoSet(**  

      DBHANDLE  hDB,  

      DBREPLICAINFO far \*ReplicationInfo**);**



**Description :**



This
function sets the given database's DBREPLICAINFO structure.  

  

Use this function to set specific values, such as the replica ID, in the header
data of a database.  To create a new replica copy of a given database, for
example, you must first create the new database using the NSFDbCreate, then get
the replica ID of the source database via NSFDbReplicaInfoGet, then set this
replica ID into the new database via NSFDbReplicaInfoSet.  

  

You may also use NSFDbReplicaInfoSet to set values such as the replication
flags in the header of the database.  See the symbolic value REPLFLG\_xxx for
specific replication settings.


 


**Parameters :**



Input :  

hDB  -  DBHANDLE obtained from a call to NSFDbOpen or NSFDbOpenExtended.  

  

ReplicationInfo  -  A pointer to a DBREPLICAINFO structure that contains the
database's new Replica ID, Purge Interval, Cutoff Date, and Replica flags.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR - Successfully set replica information.  

  

ERR\_xxx - Errors returned by lower level functions.  There are so many possible
causes, that It is best to use the code in a call to OSLoadString and
display/log the error for the user.  

  

  




 **Sample Usage :**


   

   /\* Cast the changes in stone \*/  

   

  if (error\_status = NSFDbReplicaInfoSet(db\_handle\_dst,  

                                          &replica\_info\_dst))  

       goto Exit;  

  




 **See Also :**


**[NSFDbReplicaInfoGet](NSFDbReplicaInfoGet.md)**



----------------------------------------------------------------------------------------------------------


 





