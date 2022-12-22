




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



**NSFDbItemDefTable** **- Get the
database's Item Definition Table.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



STATUS
LNPUBLIC **NSFDbItemDefTable(**  

      DBHANDLE  hDB,  

      ITEMDEFTABLEHANDLE far \*retItemNameTable**);**



**Description :**



The Item
Definition Table for a database contains the name and type of all the names and
labels defined in that database.  Examples are field names, form names, and
formula labels.  Applications can obtain a copy of the Item Definition Table by
calling NSFDbItemDefTable, which returns a memory handle for the copy of the
table.  The application must call OSLock to lock the table in memory and obtain
the memory address.  The application is responsible for de-allocating the
memory by calling OSMemFree.  

  

For details on the structure of the Item Definition Table, please see the
descriptions for ITEM\_DEFINITION\_TABLE and ITEM\_DEFINITION.


 


   
NSFDbItemDefTable is the older version of NSFDbItemDefTableExt, which is
designed to run on pre-R5 databases.  In order to process large UNK tables, API
developers need to use NSFDbItemDefTableExt instead of NSFDbItemDefTable.  API
developers useNSFDbItemDefTable. 


 


**Parameters :**



Input :  

hDB  -  A handle to a Domino database.  

  




Output :  

(routine)  -  Return status from this call -- indicates either sucess or what
the error is. The return codes include:  

  

NOERROR - Operation succeeded.  

  

  

retItemNameTable  -  The address of an ITEMDEFTABLEHANDLE where the handle for
the Item Definition Table for the database is returned.  

  




 **Sample Usage :**


ITEMDEFTABLEHANDLE   
table\_handle;  

  

   /\* Get the Item Definition Table \*/  

   

  if (error\_status = NSFDbItemDefTable(db\_handle, &table\_handle))  

       goto Exit;  

  




 **See Also :**


**[ITEM\_DEFINITION](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/0589662B342324B585256059004CA5E3)**


**[ITEM\_DEFINITION\_TABLE](ITEM_DEFINITION_TABLE.md)**


**[NSFDbAddItemName](NSFDbAddItemName.md)**



----------------------------------------------------------------------------------------------------------


 





