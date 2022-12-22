




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



**Function : Mail Gateway**



**MailGetMessageSize** **- Returns
the size of a message in bytes**


**----------------------------------------------------------------------------------------------------------**



**#include <mailserv.h>**



STATUS
LNPUBLIC **MailGetMessageSize(**  

      DARRAY far \*MessageList,  

      WORD  Message,  

      DWORD far \*MessageSize**);**



**Description :**



This
functions returns the size, in bytes, of a message in a message list.


 


**Parameters :**



Input :  

MessageList  -  Message list pointer.  

  

Message  -  Message number (0-n).  

  




Output :  

(routine)  -  Return status of the call - indicates either success or what the
error is. The return codes include:  

  

NOERROR  

  

ERR\_xxx - Error returned by lower level functions. Call OSLoadString to
interpret the code.  

  

  

MessageSize  -  Size of message in bytes.  

  




 **See Also :**


**[MailGetMessageInfo](MailGetMessageInfo.md)**



----------------------------------------------------------------------------------------------------------


 





