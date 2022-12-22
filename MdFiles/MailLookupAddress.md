




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



**MailLookupAddress** **- Returns
the full mail address of the specified user.**


**----------------------------------------------------------------------------------------------------------**



**#include <mailserv.h>**



STATUS
LNPUBLIC **MailLookupAddress(**  

      char far \*UserName,  

      char far \*MailAddress**);**



**Description :**



This
function returns the full mail address of the specified user.  This function is
typically used by gateways to translate an inbound recipient name to his or her
Domino mail address.  The mail address consists of the user name and the domain
name,  for example:  "John Smith @ Iris".  If the user has a
Forwarding Address specified, the forwarding address will be returned instead.  

  

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

(routine)  -  Return status from the call -- indicates either success
(NOERROR), specified username not found in the Domino Directory.
(ERR\_ROUTER\_NOSUCHUSER), or specified username has more than one match in the
Domino Directory (ERR\_ROUTER\_NOTUNIQUE).  

  

  

MailAddress  -  Mail address string (null-terminated) up to MAXRECIPIENTNAME+1
in length (includes null terminator).  

  




 **See Also :**


**[MailLookupUser](MailLookupUser.md)**


**[MailAddRecipientsItem](MailAddRecipientsItem.md)**



----------------------------------------------------------------------------------------------------------


 





