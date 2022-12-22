




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



**MailFindNextHopToServer** **- Find next
hop to the specified server.**


**----------------------------------------------------------------------------------------------------------**



**#include <mailserv.h>**



STATUS
LNPUBLIC **MailFindNextHopToServer(**  

      DHANDLE  hTables,  

      char far \*DestDomain,  

      char far \*DestServer,  

      char far \*NextHopServer,  

      char far \*NextHopMailbox,  

      DWORD far \*NextHopFlags,  

      WORD far \*ActualCost**);**



**Description :**



Given a
handle to a set of routing tables, the name of the originator's domain, and the
name of the destination server, obtain the server name and mailbox file name
for the next step in routing a message.


 


**Parameters :**



Input :  

hTables  -  Handle to routing tables to search.  

  

DestDomain  -  Reserved - must be set to NULL.  

  

DestServer  -  Null-terminated string containing the name of the destination
server.  

  




Output :  

(routine)  -  Return status from this call -- indicates either sucess or what
the error is. The return codes include:  

  

NOERROR - Next hop located.  

  

ERR\_xxx - Errors returned by lower level functions.  There are so many possible
causes, that it is best to use the code in a call to OSLoadString and
display/log the error for the user.   

  

  

NextHopServer  -  Null-terminated string containing the name of the next server
to route the message to.  The maximum length (in bytes) for this parameter is
MAXUSERNAME.  

  

NextHopMailbox  -  Null-terminated string containing the mailbox file name on
the next hop server.  The maximum length (in bytes) for this parameter is
MAXPATH.  

  

NextHopFlags  -  Additional flags describing the next server.  If
NEXTHOP\_INTRANET bit is set, the next server is on the same network as the
current server.  If NEXTHOP\_USESMTP           bit is set, SMTP will be used to
reach the next server.  

  

ActualCost  -  Actual cost to the destination server.  This value is computed
from the cost information stored in the routing tables.  

  




 **See Also :**


**[MailLoadRoutingTables](MailLoadRoutingTables.md)**


**[MailReloadRoutingTables](MailReloadRoutingTables.md)**


**[MailResetAllDynamicCosts](MailResetAllDynamicCosts.md)**


**[MailSetDynamicCost](MailSetDynamicCost.md)**


**[MailUnloadRoutingTables](MailUnloadRoutingTables.md)**



----------------------------------------------------------------------------------------------------------


 





