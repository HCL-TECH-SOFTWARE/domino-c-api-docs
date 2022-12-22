




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



**Function : Extension Manager; Mail**



**MailSendNoteEMCallback** **- Extension
Manager callback for EM\_MAILSENDNOTE**


**----------------------------------------------------------------------------------------------------------**



**Note:** This function is only available as an Extension Manager callback
-- you cannot call this function directly.


 


**#include <extmgr.h>**



STATUS
LNPUBLIC **MailSendNoteEMCallback(**  

      HANDLE  hNote,  

      void \*internalViewDesc,  

      WORD  Flags,  

      BOOL \*Modified,  

      void \*SendNoteCtx**);**



**Description :**



EM\_MAILSENDNOTE
is called when the Mailer sends an open note to recipients listed in the note's
header items.


 


**Parameters :**



Input :  

hNote  -  Handle to open note.  

  

internalViewDesc  -  Used by alternate mail to find the form for the note.  

  

Flags  -  Note:  MSN\_xxx Flags are not currently exposed.   

  




Output :  

(routine)  -  Return status from the call   

ERR\_EM\_CONTINUE  

  

  

Modified  -  Set to True if note is modified, otherwise it is set to False.   

  

SendNoteCtx  -  Note:  The structure of this data is not currently exposed.  

  




 **See Also :**


**[EM\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/CCB2911F1DF6C7AF8525681000480140)**



----------------------------------------------------------------------------------------------------------


 





