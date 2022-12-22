




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




 


**Function : ID Table**



**IDCreateTable** **- Creates
an ID Table.**


**----------------------------------------------------------------------------------------------------------**



**#include <idtable.h>**



STATUS
LNPUBLIC **IDCreateTable(**  

      DWORD  Alignment,  

      DHANDLE far \*rethTable**);**



**Description :**



This
function allocates an empty ID Table, and returns a handle to it.


 


ID Tables
should be released with IDDestroyTable().


 


**Parameters :**



Input :  

Alignment  -  The alignment value is used in a compression algorithm that
allows continuous "adjacent" IDs to be stored in a compressed
fashion.  Pass in 0 for this parameter in order for Domino or Notes to
determine the proper value for this parameter.  For ID tables containing
"NoteIDs", you may use the value "sizeof(NOTEID)".  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR - If ID Table was successfully created.  

  

ERR\_xxx - Errors returned by lower level functions.  There are so many possible
causes, that It is best to use the code in a call to OSLoadString and
display/log the error for the user.  

  

  

rethTable  -  The address of a HANDLE variable in which the handle to an ID
Table structure will be returned.  The caller is responsible for disposing of
this memory object with IDDestroyTable when through with it.  

  




 **Sample Usage :**


  

          if (error\_status = IDCreateTable(sizeof(NOTEID),  

                                  &arctable\_handle))  

               goto Exit;  

           else  

               cleanup\_state += FREE\_ARCTABLE;  

  




 **See Also :**


**[IDDelete](IDDelete.md)**


**[IDDeleteAll](IDDeleteAll.md)**


**[IDEntries](IDEntries.md)**


**[IDEnumerate](IDEnumerate.md)**


**[IDInsert](IDInsert.md)**


**[IDIsPresent](IDIsPresent.md)**


**[IDScan](IDScan.md)**


**[IDTableCopy](IDTableCopy.md)**


**[IDTableSize](IDTableSize.md)**


**[IDDestroyTable](IDDestroyTable.md)**



----------------------------------------------------------------------------------------------------------


 





