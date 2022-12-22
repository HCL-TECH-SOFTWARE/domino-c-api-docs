




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




**Initial Release 6**



**Function : LDAP**



**ldap\_modrdn2** **- Initiate
an asynchronous ldap modify RDN operation.**


**----------------------------------------------------------------------------------------------------------**



**#include <ldap.h>**



int
LNPUBLIC **ldap\_modrdn2(**  

      LDAP \*ld,  

      const char \*dn,  

      const char \*newrdn,  

      int  deleteoldrdn**);**



**Description :**



This
function initiates an asynchronous modify RDN operation.


 


Implemented
as a macro:


 


#define
ldap\_modrdn2(ld, dn, newrdn, deleteoldrdn)              ND\_ldap\_modrdn2((ld),
(dn), (newrdn), (deleteoldrdn))


 


**Parameters :**



Input :  

ld  -  The LDAP session handle.  

  

dn  -  The name of the entry whose RDN is to be changed.  If NULL, a zero
length DN is sent to the server.  

  

newrdn  -  The new RDN to give the entry.  

  

deleteoldrdn  -  Boolean value: non-zero indicates that the old RDN value(s) is
to be removed, zero indicates that the old RDN value(s) is to be retained as
non-distinguished values of the entry.  

  




Output :  

(routine)  -  Message ID - This ID can be used in subsequent calls to
ldap\_result to obtain the result(s) of the operation.  

  

-1 - If an error occurs.  

  

  




 




----------------------------------------------------------------------------------------------------------


 





