




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



**MailAddMessageAttachment** **- Adds a
file attachment to a message.**


**----------------------------------------------------------------------------------------------------------**



**#include <mailserv.h>**



STATUS
LNPUBLIC **MailAddMessageAttachment(**  

      DHANDLE  hMessage,  

      char far \*FileName,  

      char far \*OriginalFileName**);**



**Description :**



This
function adds a file attachment to a message.  This function is usually used by
gateways to handle inbound messages with file attachments.


 


**Parameters :**



Input :  

hMessage  -  Open message handle.  

  

FileName  -  The address of a null-terminated file name string which contains
the fully qualified file path specification for the file being attached.  

  

OriginalFileName  -  The address of a null-terminated string containing a
filename that will be stored internally with the attachment, displayed with the
atttachment icon when the document is viewed in the Notes user interface, and
subsequently used when selecting which attachment to Extract or Detach and what
path to create for an Extracted file.  It is recommended that you use a
meaningful filename as opposed to a random one whenever possible.  If attaching
mulitiple files that have the same filename but different content to a single
document, make sure this variable is unique in each call to
MailAddMessageAttachment().  

  




Output :  

(routine)  -  Return status from the call -- indicates either success (NOERROR)
or what the error is.  

  

  




 **See Also :**


**[MailCreateMessage](MailCreateMessage.md)**


**[MailExtractMessageAttachment](MailExtractMessageAttachment.md)**


**[MailGetMessageAttachmentInfo](MailGetMessageAttachmentInfo.md)**



----------------------------------------------------------------------------------------------------------


 





