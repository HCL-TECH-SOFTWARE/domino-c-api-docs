




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



**Function : Extension Manager**



**NSFMarkReadEMCallback** **- Extension
Manager callback for EM\_NSFMARKREAD**


**----------------------------------------------------------------------------------------------------------**



**Note:** This function is only available as an Extension Manager callback
-- you cannot call this function directly.


 


**#include <extmgr.h>**



STATUS
LNPUBLIC **NSFMarkReadEMCallback(**  

      DBHANDLE  hDB,  

      HANDLE  hNote,  

      NOTEID  NoteID**);**



**Description :**



EM\_NSFMARKREAD
is called when a note is opened for reading by the Notes client.  It is called
every time a note is opened for reading by the Notes client, not just when a
document changes from UNREAD to READ.  Note that this does not include other
mechanisms that could result in a note being marked read.  For example,
EM\_NSFMARKREAD is not called when a message is marked READ via the
<INSERT> key or Edit/Unread Marks.  It is also not called
when a message is read or when a message is marked READ from a C API program.


 


This
notification is useful in the implementation of Unified Messaging functionality
in the Domino and Notes environment.  See the Chapter on Unified Messaging
Solutions in the User Guide for more information.


 


**Note:** You must not
call NSFDbGetUnreadNoteTable in this routine.  When this notification is trapped,
the database semaphore is locked.  NSFDbGetUnreadNoteTable cannot acquire the
database semaphore.  Attempting to call NSFDbGetUnreadNoteTable will result in
a deadlock.


 


**Parameters :**



Input :  

hDB  -  Handle of database containing note being marked  

  

hNote  -  Handle to note being marked read  

  

NoteID  -  NoteID of the note being marked read  

  




Output :  

(routine)  -  ERR\_EM\_CONTINUE  

  

  




 **See Also :**


**[EM\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/CCB2911F1DF6C7AF8525681000480140)**


**[NSFAddToFolderEMCallback](NSFAddToFolderEMCallback.md)**



----------------------------------------------------------------------------------------------------------


 





