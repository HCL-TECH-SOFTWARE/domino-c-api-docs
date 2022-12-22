




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



**MailLookupUser** **- Returns
mail information for a specified user name.**


**----------------------------------------------------------------------------------------------------------**



**#include <mailserv.h>**



STATUS
LNPUBLIC **MailLookupUser(**  

      char far \*UserName,  

      char far \*FullName,  

      char far \*MailServerName,  

      char far \*MailFileName,  

      char far \*MailAddress,  

      char far \*ShortName**);**



**Description :**



This
function returns the following mail information for a specified user name: 
Full Name, Mail Server Name, Mail File Name, Forwarding Address, and Short
Name.  Other than Short Name, this information is rarely needed by gateway
programs.  

  

This function looks in the local copy of the Domino Directory (Server's Address
book) and does not look to the mail server for this information.  This function
is designed to be used in mail gateway programs that run on a Lotus Domino
Server replicating the Domino Directory, rather than on a Notes workstation
machine.


 


**Parameters :**



Input :  

UserName  -  User name string pointer (null-terminated).  The UserName string
can be any one of the following:  FullName, FirstName, LastName, ShortName.  

  




Output :  

(routine)  -   Return status from the call -- indicates either success
(NOERROR), specified username not found in the Domino Directory
(ERR\_ROUTER\_NOSUCHUSER), or specified username has more than one match in the
Domino Directory (ERR\_ROUTER\_NOTUNIQUE).  

  

  

FullName  -  Full user name string (null-terminated) up to MAXUSERNAME+1 in
length (includes null terminator).  First entry if multiple FullName values. 
Optional - specify NULL if not to be returned.  

  

MailServerName  -  Mail server name string (null-terminated) up to
MAXUSERNAME+1 in length (includes null terminator).  Optional - specify NULL if
not to be returned.  

  

MailFileName  -  Mail file name string (null-terminated) up to MAXPATH in
length.  Optional - specify NULL if not to be returned.  

  

MailAddress  -  Forwarding address string (null-terminated) up to
MAXRECIPIENTNAME+1 in length (includes null terminator).  Optional - specify
NULL if not to be returned.  

  

ShortName  -  Short name string (null-terminated) up to MAXUSERNAME+1 in length
(includes null terminator).  Optional - specify NULL if not to be returned.  

  




 **See Also :**


**[MailLookupAddress](MailLookupAddress.md)**



----------------------------------------------------------------------------------------------------------


 





