




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




**Initial Release 5.0.2**



**Function : Database**



**NSFDbCreateNoteID** **- Allocate
a Note ID.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



STATUS
LNPUBLIC **NSFDbCreateNoteID(**  

      DBHANDLE  hDB,  

      BOOL  fData,  

      NOTEID \*retNoteID**);**



**Description :**



This
function ensures that the returned Note ID is unique to the database.  A likely
use for this routine is by an Extension Manager DLL to create a unique ID for
an object in an external database.  


 


This
function works for a local databases only.


 


**Parameters :**



Input :  

hDB  -  Database handle.  

  

fData  -  TRUE if the Note ID to be allocated is for the note class DATA.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success, or what
the error is.  

  

  

retNoteID  -  Pointer at which the new Note ID is returned.  

  




 




----------------------------------------------------------------------------------------------------------


 





