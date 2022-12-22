




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



**NSFDbDirGet** **- Get the
database directory.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



STATUS
LNPUBLIC **NSFDbDirGet(**  

      DBHANDLE  hDB,  

      char \*retDir**);**



**Description :**



This
function gets the path to the database directory, without the database name,
relative to the Domino data directory.


 


**Parameters :**



Input :  

hDB  -  Handle to a database.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR - Successfully got the path to the database directory.  

  

  

retDir  -  Pointer to a buffer in which the path of the database directory,
relative to the Domino data directory, associated with hDB is returned. 
Declared buffer must be at least MAXPATH characters in length.  

  




 




----------------------------------------------------------------------------------------------------------


 





