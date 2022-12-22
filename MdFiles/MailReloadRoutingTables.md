




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



**MailReloadRoutingTables** **- Reload
routing tables from the Domino Directory (Server's Address book).**


**----------------------------------------------------------------------------------------------------------**



**#include <mailserv.h>**



STATUS
LNPUBLIC **MailReloadRoutingTables(**  

      DHANDLE  hTables,  

      BOOL  EnableTrace,  

      BOOL  EnableDebug,  

      BOOL far \*retAddressBookModified**);**



**Description :**



Refresh the
in-memory routing tables from the  Domino Directory (Server's Address book).


 


**Parameters :**



Input :  

hTables  -  Handle to the memory block containing the mail routing tables.  

  

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

  

  

retAddressBookModified  -  TRUE if the  Domino Directory (Server's Address
book) has been modified since the routing tables were loaded or refreshed.  

  




 **See Also :**


**[MailLoadRoutingTables](MailLoadRoutingTables.md)**


**[MailUnloadRoutingTables](MailUnloadRoutingTables.md)**



----------------------------------------------------------------------------------------------------------


 





