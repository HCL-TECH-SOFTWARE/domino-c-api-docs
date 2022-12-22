




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



**Function : Extension Manager**



**JournalMessageEMCallback** **- Extension
Manager callback for EM\_ROUTERJOURNALMESSAGE**


**----------------------------------------------------------------------------------------------------------**



**Note:** This function is only available as an Extension Manager callback
-- you cannot call this function directly.


 


**#include <extmgr.h>**



STATUS
LNPUBLIC **JournalMessageEMCallback(**  

      DBHANDLE  hMailBoxHandle,  

      NOTEID  NoteID**);**



**Description :**



EM\_ROUTERJOURNALMESSAGE
occurs when the router has received a message that has been marked to be
journalled. It can be called only when: 1) the server has mail journalling
enabled and 2) there is a system mail rule that has "Journal this
message" for some selected set of e-mail messages.


 


Journaling
does not disrupt the normal routing of a message. It saves a copy of the
selected messages to configured journal database for later review/retrieval.


 


**Parameters :**



Input :  

hMailBoxHandle  -  Handle of the mail box.  

  

NoteID  -  Note ID of the message.  

  




Output :  

(routine)  -  ERR\_EM\_CONTINUE -  Continue processing.    

  

  

  




 **See Also :**


**[EM\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/CCB2911F1DF6C7AF8525681000480140)**



----------------------------------------------------------------------------------------------------------


 





