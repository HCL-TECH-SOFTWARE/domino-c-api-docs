




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



**MailGetMessageOriginatorDomain** **- Gets
message originator domain string.**


**----------------------------------------------------------------------------------------------------------**



**#include <mailserv.h>**



STATUS
LNPUBLIC **MailGetMessageOriginatorDomain(**  

      DARRAY far \*MessageList,  

      WORD  Message,  

      char far \*OriginatorDomain,  

      WORD  OriginatorDomainSize,  

      WORD far \*OriginatorNameLength**);**



**Description :**



This
function parses the specified message to yield the originator's domain.  The
message is parsed to yield the rightmost domain in the "@" separated
list.


 


**Parameters :**



Input :  

MessageList  -  Message list pointer.  

  

Message  -  Message number (0-n).  

  

OriginatorDomainSize  -  Size of originator domain string buffer.  

  




Output :  

(routine)  -   Return status from the call -- indicates either success
(NOERROR) or what the error is.  

  

  

  

OriginatorDomain  -  Pointer to returned originator domain string (not
null-terminated).  It is up to the caller to allocate space for this buffer.  

  

OriginatorNameLength  -  Pointer to returned string lengh of the originator
domain.  

  




 **See Also :**


**[MailGetMessageOriginator](MailGetMessageOriginator.md)**



----------------------------------------------------------------------------------------------------------


 





