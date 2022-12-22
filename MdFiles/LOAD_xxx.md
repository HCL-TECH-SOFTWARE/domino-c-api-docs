




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



**Symbolic Value : Mail Gateway**



**LOAD\_xxx** **-** MailLoadRoutingTablesExt
- LoadFlags


**----------------------------------------------------------------------------------------------------------**



**#include <mailserv.h>**


 **Symbolic Values :**      LOAD\_INTERNALSMTP       -  Support internal SMTP transfer
thread and DNS.  

  

      LOAD\_EXTERNALSMTP      -  Support SMTP transfer out of local domain.  

  

      LOAD USEDNS        -  Use DNS when resolving names.  

  

      LOAD\_USEHOSTS   -  Use host's file when resolving names.  

  

      LOAD\_SERVERREACHABLE            -  Need to be in same named network.  

  

      LOAD\_INTERNALSMTPALWAYS     -  Support internal SMTP even for non MIME
messages.  

  

      LOAD\_NOSERVERCACHE   -  Disable server cache.  

  

      LOAD\_NODOMAINCACHE   -  Disable domain cache.  

  

      LOAD\_NOFOREIGNSMTPDOMAINS            -  Disable Foreign SMTP Domains when
SMTP External is enabled.  

  

      LOAD\_NOSKIPDNSQUERY              -  Do not skip the DNS query for domains
without a ".".  

  

      LOAD\_ORDERCONNECTIONSBYDEST       -  Order and search connections by
destination domain/server name.  

  

      LOAD\_LIMITNRPCROUTING           -  TRUE to limit routing algorithm to
smtp external routing logic for internet domains.  

  

      LOAD\_COSTBIASDECISION            -  TRUE to cause routing algorithm to
use raw cost bias as an additional decision point  

  




**Description :**



These
symbols are optional load flags for MailLoadingRoutingTablesExt.


 **See Also :**


**[MailLoadRoutingTablesExt](MailLoadRoutingTablesExt.md)**



----------------------------------------------------------------------------------------------------------


 





