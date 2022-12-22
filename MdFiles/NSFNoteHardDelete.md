




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



**Function : Note**



**NSFNoteHardDelete** **- Hard
deletes a soft deleted note from a database.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfnote.h>**



STATUS
LNPUBLIC **NSFNoteHardDelete(**  

      DBHANDLE  hDB,  

      NOTEID  NoteID,  

      DWORD  Reserved**);**



**Description :**



This
function takes a database handle and note ID as input and permanently deletes
the specified "soft deleted" note from the specified database.   

  

The deleted note may be of any NOTE\_CLASS\_xxx.  The active user ID must have
sufficient user access in the databases's Access Control List (ACL) to carry
out a deletion on the note or the function will return an error code.


 


**Parameters :**



Input :  

hDB  -  The handle of the database that contains the note.  

  

NoteID  -  The ID of the note that you want to delete.  

  

Reserved  -  Not used.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR - The note was successfully deleted.  

ERR\_DIRECTORY - This function is inappropriate for directories.  

ERR\_NOACCESS - You are not authorized to perform that operation.  

ERR\_xxx - STATUS returned from a lower level Notes function.  This value can be
passed to OSLoadString to obtain a text string that can be presented in a
dialog box or log entry.  

  

  




 **See Also :**


**[NSFNoteClose](NSFNoteClose.md)**


**[NSFNoteOpenSoftDelete](NSFNoteOpenSoftDelete.md)**



----------------------------------------------------------------------------------------------------------


 





