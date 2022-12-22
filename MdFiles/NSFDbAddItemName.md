




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




**Initial Release 6**



**Function : Database**



**NSFDbAddItemName** **- Adds an
item to a database's Item Definition Table**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



STATUS
LNPUBLIC **NSFDbAddItemName(**  

      DBHANDLE  hDB,  

      WORD  type,  

      char \*string,  

      WORD  length,  

      DWORD \*rtnItemNumber**);**



**Description :**



This
function takes a database handle, an item name to be added to a database's Item
Definition Table, the length of the item name and the type of item that is
being named. It returns the item number of the item added to the Item
Definition Table. 


 


**Parameters :**



Input :  

hDB  -  Handle to the open database in which to add the item.  

  

type  -  Item data type. See TYPE\_xxx.  

  

string  -  Name of item to be added.  

  

length  -  Length of item name.  

  




Output :  

(routine)  -  Return status from this call:   

  

NOERROR - Successfully added an item to the Item Definition Table.  

  

ERR\_xxx - Errors returned by lower level functions. Call OSLoadString to obtain
a string to display to the user.  

  

  

rtnItemNumber  -  The item number of the item added to the Item Definition Table.
  

  




 **See Also :**


**[NSFDbItemDefTable](NSFDbItemDefTable.md)**



----------------------------------------------------------------------------------------------------------


 





