




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



**MailFindNextHopViaRules** **- Find next
hop to recipient using domain routing rules.**


**----------------------------------------------------------------------------------------------------------**



**#include <mailserv.h>**



STATUS
LNPUBLIC **MailFindNextHopViaRules(**  

      DHANDLE  hTables,  

      char far \*RecipientAddress,  

      char far \*retDestServer,  

      char far \*retDestDomain**);**



**Description :**



Given a
handle to a set of routing tables and the distinguished name of the desired
recipient, obtain either the server name or domain name for the next hop.


 


**Parameters :**



Input :  

hTables  -  Handle to routing tables to search.  

  

RecipientAddress  -  Null-terminated string containing the distinguished name
of the recipient.  

  




Output :  

(routine)  -  Return status from this call -- indicates either sucess or what
the error is. The return codes include:  

  

NOERROR - Next hop located.  

  

ERR\_xxx - Errors returned by lower level functions.  There are so many possible
causes, that it is best to use the code in a call to OSLoadString and
display/log the error for the user.   

  

  

retDestServer  -  If the destination is a server, the null-terminated name of
that server.  If the destination is a domain, this is set to the empty string
("").  The maximum length (in bytes) for this parameter is
MAXUSERNAME.  

  

retDestDomain  -  If the destination is a domain, the null-terminated name of
that domain.  If the destination is a server, this is set to the empty string
("").  The maximum length (in bytes) for this parameter is
MAXDOMAINPATH.  

  




 **See Also :**


**[MailLoadRoutingTables](MailLoadRoutingTables.md)**


**[MailReloadRoutingTables](MailReloadRoutingTables.md)**


**[MailUnloadRoutingTables](MailUnloadRoutingTables.md)**



----------------------------------------------------------------------------------------------------------


 





