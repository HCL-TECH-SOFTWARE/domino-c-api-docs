




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




**Initial Release 5.0**



**Function : Extension Manager**



**NSFNoteUpdateMailboxEMCallback** **- Extension
Manager callback for EM\_NSFNOTEUPDATEMAILBOX**


**----------------------------------------------------------------------------------------------------------**



**Note:** This function is only available as an Extension Manager callback
-- you cannot call this function directly.


 


**#include <extmgr.h>**



STATUS
LNPUBLIC **NSFNoteUpdateMailboxEMCallback(**  

      NOTEHANDLE  note\_handle,  

      WORD  update\_flags**);**



**Description :**



EM\_NSFNOTEUPDATEMAILBOX
occurs when a NSFNoteUpdate is performed on any and all mailbox databases (e.g.
a mail.box file).  This is true even if multiple mailboxes are enabled in the
server configuration document.  The arguments are identical to those used for
EM\_NSFNOTEUPDATE.


 


**Parameters :**



Input :  

note\_handle  -  The handle of the note to be updated.  

  

update\_flags  -  Flags that control the manner in which the note update is
done. The flags are defined in UPDATE\_xxx and may be or'ed together to combine
functionality.  

  




Output :  

(routine)  -    

ERR\_EM\_CONTINUE  

  

  




 **See Also :**


**[EM\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/CCB2911F1DF6C7AF8525681000480140)**


**[UPDATE\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/85255D56004D3F6385255B4A0056976E)**



----------------------------------------------------------------------------------------------------------


 





