




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



**NSFDbSetObjectStoreID** **- Set the
replica ID of a Domino Object Store in a Domino database.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



STATUS
LNPUBLIC **NSFDbSetObjectStoreID(**  

      DBHANDLE  dbhandle,  

      DBID far \*ObjStoreReplicaID**);**



**Description :**



Store the
specified replica ID for a Domino Object Store into the specified Domino
database.  This creates an association between the database and the Object
Store.


 


**Parameters :**



Input :  

dbhandle  -  Handle of the Domino database to associate with the Domino Object
Store.  

  

ObjStoreReplicaID  -  Replica ID of the Domino Object Store.  

  




Output :  

(routine)  -  (routine)  -  Return status from this call -- indicates either
success, or what the error is.  The return codes include:  

  

NOERROR  

ERR\_IS\_OBJSTORE - The replica ID for a Domino Object Store cannot be written
into a Domino Object Store (only into a Domino database).  

  

  




 **See Also :**


**[NSFDbCreateObjectStore](NSFDbCreateObjectStore.md)**


**[NSFDbGetObjectStoreID](NSFDbGetObjectStoreID.md)**



----------------------------------------------------------------------------------------------------------


 





