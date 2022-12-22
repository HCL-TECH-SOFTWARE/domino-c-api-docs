




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



**NSFDbCreateObjectStore** **- Create a
Note Object store.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



STATUS
LNPUBLIC **NSFDbCreateObjectStore(**  

      const char far \*PathName,  

      BOOL  ForceCreation**);**



**Description :**



A Note
Object Store allows maintaining a single copy of large notes (for example, a
note with large amounts of attached data).  Entries in standard Domino
databases can be linked to a note in a Note Object Store.  This function is
used to create the Note Object Store.


 


The notes in
a Note Object Store are accessed using the NSF routines - for example,
NSFDbOpen() (or NSFDbOpenExtended()), NSFNoteOpen(), etc.


 


**Parameters :**



Input :  

PathName  -  Null-terminated file name for the Note Object Store.  

  

ForceCreation  -  If TRUE and the Note Object Store already exists, a new,
empty store will replace the existing store.  

  




Output :  

(routine)  -  (routine)  -  Return status from this call -- indicates either
success, or what the error is.  The return codes include:  

  

NOERROR  

ERR\_EXISTS  

ERR\_DBCLASS  

  

  




 **See Also :**


**[NSFDbGetObjectStoreID](NSFDbGetObjectStoreID.md)**


**[NSFDbSetObjectStoreID](NSFDbSetObjectStoreID.md)**



----------------------------------------------------------------------------------------------------------


 





