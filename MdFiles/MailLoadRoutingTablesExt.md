




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




**Initial Release 4.5**



**Function : Mail Gateway**



**MailLoadRoutingTablesExt** **- Load
routing tables from the Domino Directory (Server's Address book) with
additional options.**


**----------------------------------------------------------------------------------------------------------**



**#include <mailserv.h>**



STATUS
LNPUBLIC **MailLoadRoutingTablesExt(**  

      DBHANDLE  hAddressBook,  

      char far \*LocalServersName,  

      char far \*LocalServersDomain,  

      char far \*LocalServersInternetDomain,  

      char far \*TaskName,  

      BOOL  EnableTrace,  

      BOOL  EnableDebug,  

      DWORD  LoadFlags,  

      DHANDLE far \*rethTables**);**



**Description :**



Load the set
of routing tables from the Domino Directory (Server's Address book) into
memory.  The caller is responsible for freeing memory used for the routing
tables by calling MailUnloadRoutingTables ().


 


This
function is similar to MailLoadRoutingTables with the additional ability to
specify the calling server's Internet domain name and the ability to specify a
load flag.


 


**Parameters :**



Input :  

hAddressBook  -  Handle to the open Domino Directory (Server's Address book).  

  

LocalServersName  -  Null-terminated string containing the name of the local
server - the server where this function call is taking place, in upper case.  

  

LocalServersDomain  -  Null-terminated string containing the domain of the
local server - the domain of the server where this function call is taking
place.  

  

LocalServersInternetDomain  -  Null-terminated string containing the Internet
domain name of the local server - the Internet domain name of the server where
this function call is taking place.  

  

TaskName  -  Null-terminated string containing the name of the calling task. 
This string uniquely identifies the different mail routing services on a given
server.  

  

  

EnableTrace  -  If TRUE, tracing of mail routings is enabled.  

  

EnableDebug  -  If TRUE, mail routing debug information is generated in the
debugging log.  

  

LoadFlags  -  Optional.  See LOAD\_xxx for possible values.  

  




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


**[MailLoadRoutingTables](MailLoadRoutingTables.md)**


**[MailUnloadRoutingTables](MailUnloadRoutingTables.md)**


**[LOAD\_xxx](notes:///852584E300582C9D/61FD4E9848264AD28525620B006BA8BD/6310576CE0615B7A85256678005ED854)**



----------------------------------------------------------------------------------------------------------


 





