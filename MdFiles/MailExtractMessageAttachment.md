




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



**MailExtractMessageAttachment** **- Extracts
a file attachment from a message into a disk file.**


**----------------------------------------------------------------------------------------------------------**



**#include <mailserv.h>**



STATUS
LNPUBLIC **MailExtractMessageAttachment(**  

      DHANDLE  hMessage,  

      BLOCKID  bhItem,  

      char far \*FileName**);**



**Description :**



This
function extracts a file attachment from a message into a disk file.  The file
is usually a temporary file used to contain the file data while the gateway
transfers the data to the recipients.  

  

If an attachment has been compressed, it will be decompressed as it is
extracted.  

  

Since a gateway never has access to a recipient's private key, if an attachment
has been encrypted, it cannot be extracted.  If an attachment is encrypted, the
ERR\_NOEXTRACT\_ENCRYPTED error is returned.  

  

The modification date on the file is set to the attached file's modification
date.


 


**Parameters :**



Input :  

hMessage  -  Open message handle.  

  

bhItem  -  Block ID of the attachment (returned by MailGetAttachmentInfo)  

  

FileName  -  File name string pointer (null-terminated).  

  




Output :  

(routine)  -  Return status from the call -- indicates either success (NOERROR)
or what the error is.  

  

  




 **See Also :**


**[MailGetMessageAttachmentInfo](MailGetMessageAttachmentInfo.md)**



----------------------------------------------------------------------------------------------------------


 





