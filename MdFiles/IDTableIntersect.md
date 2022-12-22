




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




**Initial Release 4.5**



**Function : ID Table**



**IDTableIntersect** **- Returns
the ID's that are common to two ID Tables.**


**----------------------------------------------------------------------------------------------------------**



**#include <idtable.h>**



STATUS 
LNPUBLIC **IDTableIntersect(**  

      DHANDLE  hSrc1Table,  

      DHANDLE  hSrc2Table,  

      DHANDLE \*rethDstTable**);**



**Description :**



This function
creates the intersection of two ID Tables.  The resulting table contains those
IDs that are common to both source tables.


 


**Parameters :**



Input :  

hSrc1Table  -  Handle to the first of two ID Tables that will be compared.  

  

hSrc2Table  -  Handle to the second of two ID Tables that will be compared.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR - Success.  

  

ERR\_IDTABLE\_INVALID - An invalid ID Table was specified.  

  

ERR\_xxx - Errors returned by lower level functions. Call to OSLoadString and
display/log the error for the user.  

  

  

rethDstTable  -  Pointer to the handle of the resulting ID Table.  This table
contains the IDs that are common to hSrc1Table and hSrc2Table.  If the handle
of the resulting table is specified as NULLHANDLE, then the resulting table
will be created and populated.  Otherwise the specified resulting table will be
replaced.  You need to make sure that the handle pointed to by rethDstTable is
either NULLHANDLE or a valid handle to an ID Table.  You also need to detroy
the resulting table when done with it with IDDestroyTable.  

  




 **See Also :**


**[IDCreateTable](IDCreateTable.md)**


**[IDAreTablesEqual](IDAreTablesEqual.md)**


**[IDDestroyTable](IDDestroyTable.md)**



----------------------------------------------------------------------------------------------------------


 





