




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



**MailLoadRoutingTables** **- Load
routing tables from the Domino Directory (Server's Address book).**


**----------------------------------------------------------------------------------------------------------**



**#include <mailserv.h>**



STATUS
LNPUBLIC **MailLoadRoutingTables(**  

      DBHANDLE  hAddressBook,  

      char far \*LocalServerName,  

      char far \*LocalDomainDomain,  

      char far \*TaskName,  

      BOOL  EnableTrace,  

      BOOL  EnableDebug,  

      DHANDLE far \*rethTables**);**



**Description :**



Load the set
of routing tables from the Domino Directory (Server's Address book) into
memory.  The caller is responsible for freeing memory used for the routing
tables by calling MailUnloadRoutingTables ().


 


**Parameters :**



Input :  

hAddressBook  -  Handle to the open Domino Directory (Server's Address book).  

  

LocalServerName  -  Null-terminated string containing the name of the local
server - the server where this function call is taking place, in upper case.  

  

LocalDomainDomain  -  Null-terminated string containing the domain of the local
server - the domain of the server where this function call is taking place.  

  

TaskName  -  Null-terminated string containing the name of the calling task. 
This string uniquely identifies the different mail routing services on a given
server.  

  

EnableTrace  -  If TRUE, tracing of mail routings is enabled.  

  

EnableDebug  -  If TRUE, mail routing debug information is generated in the
debugging log.  

  




Output :  

(routine)  -  Return status from this call -- indicates either sucess or what
the error is. The return codes include:  

  

NOERROR - Routing tables loaded.  

  

ERR\_xxx - Errors returned by lower level functions.  There are so many possible
causes, that it is best to use the code in a call to OSLoadString and
display/log the error for the user.   

  

  

rethTables  -  Handle to the memory block containing the mail routing tables. 
The caller must free this memory using MailUnloadRoutingTables ().  

  




 **See Also :**


**[MailFindNextHopToDomain](MailFindNextHopToDomain.md)**


**[MailFindNextHopToRecipient](MailFindNextHopToRecipient.md)**


**[MailFindNextHopToServer](MailFindNextHopToServer.md)**


**[MailFindNextHopViaRules](MailFindNextHopViaRules.md)**


**[MailReloadRoutingTables](MailReloadRoutingTables.md)**


**[MailResetAllDynamicCosts](MailResetAllDynamicCosts.md)**


**[MailSetDynamicCost](MailSetDynamicCost.md)**


**[MailUnloadRoutingTables](MailUnloadRoutingTables.md)**


**[MailLoadRoutingTablesExt](MailLoadRoutingTablesExt.md)**



----------------------------------------------------------------------------------------------------------


 





