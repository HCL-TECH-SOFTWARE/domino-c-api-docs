




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



**ldap\_extended\_operation** **- Allow
asychronous extended LDAP operations to be passed to the server.**


**----------------------------------------------------------------------------------------------------------**



**#include <ldap.h>**



int
LNPUBLIC **ldap\_extended\_operation(**  

      LDAP \*ld,  

      const char \*exoid,  

      const struct berval \*exdata,  

      LDAPControl \*\*serverctrls,  

      LDAPControl \*\*clientctrls,  

      int \*msgidp**);**



**Description :**



This
function will allow asychronous extended LDAP operations to be passed to the
server, providing a general protocol extensibility mechanism.


 


Implemented
as a macro:


 


#define
ldap\_extended\_operation(ld, exoid, exdata, serverctrls, clientctrls, msgidp) \  

              ND\_ldap\_extended\_operation((ld), (exoid), (exdata),
(serverctrls), (clientctrls), (msgidp)) 


 


**Parameters :**



Input :  

ld  -  The LDAP session handle.  

  

exoid  -  The dotted-OID text string naming the request.  

  

exdata  -  The arbitrary data needed by the operation (if NULL, no data is sent
to the server).  

  

serverctrls  -  Pointer to a list of LDAP server controls. NULL if no server
controls are to be used.  

  

clientctrls  -  Pointer to a list of LDAP client controls.  NULL if no server
controls are to be used.  

  




Output :  

(routine)  -  LDAP\_SUCCESS  - If the request was successfully sent, or another
LDAP result code if not.  

  

  

msgidp  -  Pointer to the message id of the request if the
ldap\_extended\_operation call succeeds. The value is undefined if a value other
than LDAP\_SUCCESS is returned.   This ID can be used in subsequent calls to
ldap\_result to obtain the result(s) of the operation.  

  




 




----------------------------------------------------------------------------------------------------------


 





