




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



**MailFindNextHopToRecipient** **- Find next
hop to the specified recipient.**


**----------------------------------------------------------------------------------------------------------**



**#include <mailserv.h>**



STATUS
LNPUBLIC **MailFindNextHopToRecipient(**  

      DHANDLE  hTables,  

      char far \*OriginatorsDomain,  

      char far \*RecipientAddress,  

      MAIL\_ROUTING\_ACTIONS far \*Action,  

      char far \*NextHopServer,  

      char far \*NextHopMailbox,  

      char far \*ForwardAddress,  

      char far \*ErrorText,  

      DWORD far \*NextHopFlags**);**



**Description :**



Given a
handle to a set of routing tables, the name of the originator's domain, and the
distinguished name of the desired recipient, obtain the server name and mailbox
file name for the next step in routing a message.


 


**Parameters :**



Input :  

hTables  -  Handle to routing tables to search.  

  

OriginatorsDomain  -  Null-terminated string containing the name of the domain
for the originator of the message.  

  

RecipientAddress  -  Null-terminated string containing the distinguished name
of the recipient.  

  




Output :  

(routine)  -  Return status from this call -- indicates either sucess or what
the error is. The return codes include:  

  

NOERROR - Next hop located.  

  

ERR\_xxx - Errors returned by lower level functions.  There are so many possible
causes, that it is best to use the code in a call to OSLoadString and
display/log the error for the user.  

  

  

Action  -  Flag indicating the type of connection represented by the next hop. 
The values that may be returned and their meanings are described in the entry
MAIL\_ROUTING\_ACTIONS.  

  

NextHopServer  -  Null-terminated string containing the name of the next server
to route the message to.  The maximum length (in bytes) for this parameter is
MAXUSERNAME.  

  

NextHopMailbox  -  Null-terminated string containing the mailbox file name on
the next hop server.  The maximum length (in bytes) for this parameter is
MAXPATH.  

  

ForwardAddress  -  If the Action output value is MAIL\_FORWARD, a
null-terminated string containing the recipient's forwarding mail address.  The
maximum length (in bytes) for this parameter is MAXUSERNAME + MAXDOMAINNAME +
3.  

  

ErrorText  -  If an error occurs, a formatted null-terminated string describing
the problem.  This message is intended to be returned to the originator.  The
maximum length (in bytes) for this parameter is MAXSPRINTF.  

  

NextHopFlags  -  Additional flags describing the next hop server.  If
NEXTHOP\_INTRANET bit is set, the next hop server is on the same network as the
current server.  If NEXTHOP\_USESMT bit is set, SMTP will be used to reach the
next hop server.  

  




 **See Also :**


**[MailFindNextHopToRecipientExt](MailFindNextHopToRecipientExt.md)**


**[MailLoadRoutingTables](MailLoadRoutingTables.md)**


**[MailReloadRoutingTables](MailReloadRoutingTables.md)**


**[MailUnloadRoutingTables](MailUnloadRoutingTables.md)**



----------------------------------------------------------------------------------------------------------


 





