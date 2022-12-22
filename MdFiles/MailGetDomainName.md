




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



**MailGetDomainName** **- Returns
the domain name of the local IBM Domino Server.**


**----------------------------------------------------------------------------------------------------------**



**#include <mailserv.h>**



STATUS
LNPUBLIC **MailGetDomainName(**  

      char far \*Domain**);**



**Description :**



This
function returns the domain name of the local IBM Domino Server.  The domain
name is obtained from the DomainName field from the Server entry in the Domino
Directory (Server's Address book).  The domain name is always returned in all
upper case.


 


**Parameters :**




Output :  

(routine)  -  Return status from the call -- indicates either success (NOERROR)
or what the error is.  

  

  

Domain  -  Domain name string (null-terminated).    

  




 **See Also :**


**[MailLookupAddress](MailLookupAddress.md)**


**[MailLookupUser](MailLookupUser.md)**



----------------------------------------------------------------------------------------------------------


 





