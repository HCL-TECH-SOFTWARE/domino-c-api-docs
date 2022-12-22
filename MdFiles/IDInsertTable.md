




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



**IDInsertTable** **- Insert a
given set of IDs into an ID Table.**


**----------------------------------------------------------------------------------------------------------**



**#include <idtable.h>**



STATUS
LNPUBLIC **IDInsertTable(**  

      DHANDLE  hTable,  

      DHANDLE  hIDsToAdd**);**



**Description :**



This
function inserts a given set of IDs from one ID Table into a source ID Table. 
If an ID in the given set of IDs to be inserted already exists in the source ID
Table, it is ignored.


 


The
IDTABLE\_MODIFIED flag is set if at least one ID was inserted into the ID Table.
  

  

ID Tables are ordered by ID value. IDInsert stores the ID in the table
according to its value.


 


This
function is similar to IDInsert.  IDInsert can insert only one ID at a time. 
This function can be used to insert a set of IDs.


 


**Parameters :**



Input :  

hTable  -  Handle to the source ID Table.  This table will contain these IDs as
well as the additional IDs upon successful completion of this function.  

  

hIDsToAdd  -  Handle to the table of IDs to be inserted into  hTable.   

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR - Success.  

  

ERR\_IDTABLE\_INVALID - An invalid ID Table was specified.  

  

ERR\_xxx - Errors returned by lower level functions. Call to OSLoadString and
display/log the error for the user.  

  

  

hTable  -  The resulting table.  The source ID Table is replaced by the
resulting ID Table.  

  




 **See Also :**


**[IDCreateTable](IDCreateTable.md)**


**[IDDeleteTable](IDDeleteTable.md)**


**[IDInsert](IDInsert.md)**



----------------------------------------------------------------------------------------------------------


 





