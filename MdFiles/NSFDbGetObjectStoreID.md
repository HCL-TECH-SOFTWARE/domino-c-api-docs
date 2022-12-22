




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



**Function : Database**



**NSFDbGetObjectStoreID** **- Get the
replica ID of a Note Object Store.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



STATUS
LNPUBLIC **NSFDbGetObjectStoreID(**  

      DBHANDLE  dbhandle,  

      BOOL far \*Specified,  

      DBID far \*ObjStoreReplicaID**);**



**Description :**



If a Note
Object Store is associated with this database, return the replica ID for the
object store.


 


**Parameters :**



Input :  

dbhandle  -  Handle of the database.  

  




Output :  

(routine)  -  (routine)  -  Return status from this call -- indicates either
success, or what the error is.  The return codes include:  

  

NOERROR  

  

  

  

Specified  -  If a Note Object Store is associated with this database, this
value is set to TRUE.  

  

ObjStoreReplicaID  -  If a Note Object Store is associated with this database,
the replica ID of the object store is placed at this address.  

  




 **See Also :**


**[NSFDbCreateObjectStore](NSFDbCreateObjectStore.md)**


**[NSFDbSetObjectStoreID](NSFDbSetObjectStoreID.md)**



----------------------------------------------------------------------------------------------------------


 





