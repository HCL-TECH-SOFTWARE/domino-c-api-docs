




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



**MailGetMessageBody** **- Returns a
copy of the Body field text from an open message.**


**----------------------------------------------------------------------------------------------------------**



**#include <mailserv.h>**



STATUS
LNPUBLIC **MailGetMessageBody(**  

      DHANDLE  hMessage,  

      DHANDLE far \*hBody,  

      DWORD far \*BodyLength**);**



**Description :**



This function
returns a copy of the text of the Body field from an open message.  

  

The Body field is converted to a series of 78 or less character lines.  Each
line is terminated by a null character ('\0').   

  

This function can only handle plain text and can only return the text when it
is 64 KB or less.  See the MailGetMessageBodyText function for handling text
greater than 64KB.


 


**Parameters :**



Input :  

hMessage  -  Open message handle.  

  




Output :  

(routine)  -  Return status from the call -- indicates either success (NOERROR)
or what the error is.  

  

  

hBody  -  Body text handle.  

  

BodyLength  -  Length of text in body (0-64K).  

  




 **See Also :**


**[MailGetMessageBodyText](MailGetMessageBodyText.md)**


**[MailGetMessageBodyComposite](MailGetMessageBodyComposite.md)**



----------------------------------------------------------------------------------------------------------


 





