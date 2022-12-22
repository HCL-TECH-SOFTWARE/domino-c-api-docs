




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



**Function : Extension Manager; Note**



**NSFNoteOpenExtendedEMCallback** **- Extension
Manager callback for EM\_NSFNOTEOPENEXTENDED**


**----------------------------------------------------------------------------------------------------------**



**Note:** This function is only available as an Extension Manager callback
-- you cannot call this function directly.


 


**#include <extmgr.h>**



STATUS
LNPUBLIC **NSFNoteOpenExtendedEMCallback(**  

      DBHANDLE  hDB,  

      NOTEID  NoteID,  

      DWORD  flags,  

      DWORD  SinceSeqNum,  

      BYTE \*pKey,  

      HANDLE \*rtn**);**



**Description :**



EM\_NSFNOTEOPENEXTENDED
is a Notes internal, extended form of NSFNoteOpen and NSFNoteOpenExt.


 


**Parameters :**



Input :  

hDB  -  The handle of the open database that contains the note.  

  

NoteID  -  The ID of the note you want to open.  

  

flags  -  Flags that control the manner in which the note is opened.  The flags
are defined in OPEN\_xxx (note) and may be or'ed together to combine
functionality.  

  

SinceSeqNum  -  This parameter is used to return only those items stored after
it's sequence value and is used by the replicator.  

  

pKey  -  This parameter is needed to open a link note stored by the mail router
for single message store.  

  




Output :  

(routine)  -    

ERR\_EM\_CONTINUE  

  

  

rtn  -  A handle to the open note.  

  




 **See Also :**


**[EM\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/CCB2911F1DF6C7AF8525681000480140)**



----------------------------------------------------------------------------------------------------------


 





