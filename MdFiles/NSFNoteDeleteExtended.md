




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Courier;
 panose-1:2 7 4 9 2 2 5 2 4 4;}
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




**Initial Release 5.0**



**Function : Note**



**NSFNoteDeleteExtended** **- Deletes a
note from a database.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfnote.h>**



STATUS
LNPUBLIC **NSFNoteDeleteExtended(**  

      DBHANDLE  hDB,  

      NOTEID  NoteID,  

      DWORD  UpdateFlags**);**



**Description :**



This
function takes a database handle, note ID, and a DWORD of UPDATE\_xxx flag(s) as
input and deletes the specified note from the specified database.  This
function allows using extended 32-bit DWORD update options, as described in the
entry UPDATE\_xxx.  

  

It deletes the specified note by updating it with a nil body, and marking the
note as a deletion stub.  The deletion stub identifies the deleted note to
other replica copies of the database.  This allows the replicator to delete
copies of the note from replica databases.   

  

The deleted note may be of any NOTE\_CLASS\_xxx.  The active user ID must have
sufficient user access in the databases's Access Control List (ACL) to carry
out a deletion on the note or the function will return an error code.


 


**Parameters :**



Input :  

hDB  -  The handle of the database that contains the note.  

  

NoteID  -  The ID of the note that you want to delete.  

  

UpdateFlags  -  Flags that control the manner in which the database is
updated.  See UPDATE\_xxx for further information.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR - The note was successfully deleted.  

ERR\_DIRECTORY - This function is inappropriate for directories.  

ERR\_NOACCESS - You are not authorized to perform that operation.  

ERR\_xxx - STATUS returned from a lower level Notes function.  This value can be
passed to OSLoadString to obtain a text string that can be presented in a
dialog box or log entry.  

  

  




 **Sample Usage :**


  

if (error = NSFNoteDeleteExtended (db\_handle, note\_id, UPDATE\_SHARE\_SECOND))  

{   

    NSFDbClose (db\_handle);  

    return (ERR(error));  

}


 **See Also :**


**[NSFNoteClose](NSFNoteClose.md)**


**[NSFNoteOpen](NSFNoteOpen.md)**


**[NSFNoteUpdate](NSFNoteUpdate.md)**


**[UPDATE\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/85255D56004D3F6385255B4A0056976E)**



----------------------------------------------------------------------------------------------------------


 





