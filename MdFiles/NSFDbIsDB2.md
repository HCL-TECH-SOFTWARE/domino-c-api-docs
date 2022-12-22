




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




**Initial Release 7.0**



**Function : Backup**



**NSFDbIsDB2** **-
Determines whether a Domino database is a DB2 database or an NSF database.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



STATUS
LNPUBLIC **NSFDbIsDB2(**  

      DBHANDLE  hDb,  

      BOOL &  isDB2**);**



**Description :**



This
function determines whether a Domino database is a DB2 database or an NSF
database.


 


**Parameters :**



Input :  

hDb  -  A handle to an open Notes database.  

  




Output :  

(routine)  -  Return status from this call:   

  

NOERROR - Successful.  

  

ERR\_xxx - Errors returned by lower level functions: (memory management, file
operations, network errors, etc.).  There are so many possible causes, that it
is best to use the code in a call to OSLoadString and display/log the error for
the user as your default error handling.  

  

  

isDB2  -  TRUE if this Domino database is a DB2 database.  FALSE if this Domino
database is an NSF database.  

  




 




----------------------------------------------------------------------------------------------------------


 





