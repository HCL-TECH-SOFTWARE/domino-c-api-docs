




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



**MailFindNextHopToDomain** **- Find next
hop to the destination domain.**


**----------------------------------------------------------------------------------------------------------**



**#include <mailserv.h>**



STATUS
LNPUBLIC **MailFindNextHopToDomain(**  

      DHANDLE  hTables,  

      char far \*OriginatorsDomain,  

      char far \*DestDomain,  

      char far \*NextHopServer,  

      char far \*NextHopMailbox,  

      DWORD far \*NextHopFlags,  

      char far \*ErrorServer**);**



**Description :**



Given a
handle to a set of routing tables, the name of the originator's domain, and the
name of the destination domain, obtain the server name and mailbox file name
for the next step in routing a message to the destination domain.


 


**Note:**  This
function assumes that the destination domain is **not** the domain for the
local server.


 


**Parameters :**



Input :  

hTables  -  Handle to routing tables to search.  

  

OriginatorsDomain  -  Null-terminated string containing the name of the domain
for the originator of the message.  

  

DestDomain  -  Null-terminated string containing the name of the destination
domain.  

  




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

  

NextHopFlags  -  Additional flags describing the next hop server.  If
NEXTHOP\_INTRANET bit is set, the next hop server is on the same network as the
current server.  If NEXTHOP\_USESMTP bit is set, SMTP will be used to reach the
next hop server.  

  

ErrorServer  -  If no route to the specified destination domain is found, the
null-terminated name of the error server is stored at this address.  The
maximum length (in bytes) for this parameter is MAXSPRINTF.  

  




 **See Also :**


**[MailFindNextHopToDomainExt](MailFindNextHopToDomainExt.md)**


**[MailReloadRoutingTables](MailReloadRoutingTables.md)**


**[MailUnloadRoutingTables](MailUnloadRoutingTables.md)**


**[NEXTHOP\_xxx (Output)](notes:///852584E300582C9D/61FD4E9848264AD28525620B006BA8BD/5D3DE63ACA2E854A852563790049FDA4)**



----------------------------------------------------------------------------------------------------------


 





