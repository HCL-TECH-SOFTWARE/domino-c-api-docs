




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




**Initial Release 5.0.3**



**Function : Extension Manager;
Folders; Views**



**NSFAddToFolderEMCallback** **- Extension
Manager callback for EM\_NSFADDTOFOLDER**


**----------------------------------------------------------------------------------------------------------**



**Note:** This function is only available as an Extension Manager callback
-- you cannot call this function directly.


 


**#include <extmgr.h>**



STATUS
LNPUBLIC **NSFAddToFolderEMCallback(**  

      DBHANDLE  hViewDB,  

      DBHANDLE  hDataDB,  

      NOTEID  FolderNoteID,  

      NOTEID  NoteID,  

      UNID \*NoteUNID,  

      BOOL  IsAddOperation,  

      TIMEDATE \*RevisionTime**);**



**Description :**



EM\_NSFADDTOFOLDER
is called when a note is being added or removed  from a folder.  The
IsAddOperation flag should be checked to determine if this note is being added
or removed from the folder.


 


This
notification is useful in the implementation of Unified Messaging functionality
in the Domino and Notes environment.  See the Chapter on Unified Messaging
Solutions in the User Guide for more information.


 


**Note:** You must not
call NSFFolderGetIDTable in this routine with the same Folder ID.  When this
notification is trapped, the database semaphore is locked.  NSFFolderGetIDTable
cannot acquire the database semaphore.  Attempting to call NSFFolderGetIDTable
will result in a deadlock.


 


**Parameters :**



Input :  

hViewDB  -  Handle of database containing folder  

  

hDataDB  -  Handle of database containing notes being added to folder  

  

FolderNoteID  -  NoteID of the folder note  

  

NoteID  -  NoteID of the note being added to (removed from) the folder  

  

NoteUNID  -  UNID of the note being added to (removed from) the folder  

  

IsAddOperation  -  TRUE if note being added to the folder, FALSE if note being
removed  

  

RevisionTime  -  Time of original folder addition (OPTIONAL - may be NULL)  

  




Output :  

(routine)  -  ERR\_EM\_CONTINUE  

  

  




 **See Also :**


**[EM\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/CCB2911F1DF6C7AF8525681000480140)**


**[NSFMarkReadEMCallback](NSFMarkReadEMCallback.md)**



----------------------------------------------------------------------------------------------------------


 





