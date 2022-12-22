




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:"Tms Rmn";
 panose-1:2 2 6 3 4 5 5 2 3 4;}
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




 


**Function : Mail Gateway**



**MailCreateMessage** **- Creates
an in-memory message.**


**----------------------------------------------------------------------------------------------------------**



**#include <mailserv.h>**



STATUS
LNPUBLIC **MailCreateMessage(**  

      DBHANDLE  hFile,  

      DHANDLE far \*rethMessage**);**



**Description :**



This
function creates an in-memory message.  This function is usually used by
gateways for creating inbound messages from foreign mail systems.  A handle to
the open message is returned for use in other message object function calls. 
Use MailCloseMessage to close the message handle and deallocate the memory
associated with it.


 


**Parameters :**



Input :  

hFile  -  Open message file handle.  

  




Output :  

(routine)  -  Return status from the call -- indicates either success (NOERROR)
or what the error is.  

  

  

rethMessage  -  Open message handle.  

  




 **See Also :**


**[MailCloseMessage](MailCloseMessage.md)**



----------------------------------------------------------------------------------------------------------


 





