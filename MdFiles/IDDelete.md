




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




 


**Function : ID Table**



**IDDelete** **- Delete an
ID from the specified ID Table.**


**----------------------------------------------------------------------------------------------------------**



**#include <idtable.h>**



STATUS
LNPUBLIC **IDDelete(**  

      DHANDLE  hTable,  

      DWORD  id,  

      BOOL far \*retfDeleted**);**



**Description :**



This
function deletes an ID from the specified ID Table.  It returns a BOOL value in
the \*retfInserted parameter indicating whether or not the note ID was
successfully deleted from the ID Table.  If the specified ID does not initially
reside in the table, FALSE is returned in the \*retfDeleted parameter.  This
function also sets the IDTABLE\_MODIFIED flag if the ID was successfully
deleted, that is if the returned \*retfDeleted value is TRUE.


 


**Parameters :**



Input :  

hTable  -  A handle to the ID table.  

  

id  -  The ID to delete from the ID Table.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR - ID successfully deleted from the table.  

  

ERR\_xxx - Errors returned by lower level functions.  Call to OSLoadString to
interpret the error code for display.  

  

  

retfDeleted  -  The address of a BOOL variable in which the outcome of the call
to IDDelete is placed.   TRUE - if the specified ID was deleted from the ID
Table. FALSE if the ID did not previously reside in the table.  Can be NULL if
no return value is required.  

  




 **See Also :**


**[IDCreateTable](IDCreateTable.md)**


**[IDInsert](IDInsert.md)**



----------------------------------------------------------------------------------------------------------


 





