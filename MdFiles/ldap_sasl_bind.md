




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



**ldap\_sasl\_bind** **- Initiate
an asynchronous SASL bind operation**


**----------------------------------------------------------------------------------------------------------**



**#include <ldap.h>**



int
LNPUBLIC **ldap\_sasl\_bind(**  

      LDAP \*ld,  

      const char \*who,  

      const char \*mechanism,  

      struct berval \*cred,  

      LDAPControl \*\*serverctrls,  

      LDAPControl \*\*clientctrls,  

      int \*msgidp**);**



**Description :**



This
function initiates an asynchronous bind operation to bind to the ldap server
using SASL authentication.


 


Implemented
as a macro:


 


#define
ldap\_sasl\_bind(ld, who, mechanism, cred, serverctrls, clientctrls, msgidp) \  

             ND\_ldap\_sasl\_bind((ld), (who), (mechanism), (cred), (serverctrls),
(clientctrls), (msgidp))


 


**Parameters :**



Input :  

ld  -  The LDAP session handle.  

  

who  -  The distinguished name of the entry to bind as.  

  

mechanism  -  The method to use for authentication.  Either LDAP\_SASL\_SIMPLE
(NULL) to get simple authentication, or a text string identifying the SASL
method.  See LDAP\_SASL\_xxx.  

  

cred  -  The credentials with which to authenticate. Arbitrary credentials can
be passed using this parameter. The format and content of the credentials
depends on the setting of the mechanism parameter.  If the cred parameter is
NULL and the mechanism is LDAP\_SASL\_SIMPLE, a zero-length octet string is sent
to the server in the simple credentials field of the bind request.  If the cred
parameter is NULL and the mechanism is anything else, no credentials are sent
to the server in the bind request.  

  

serverctrls  -  Pointer to a list of LDAP server controls.  NULL if no server
controls are to be used.  

  

clientctrls  -  Pointer to a list of LDAP client controls.  NULL if no client
controls are to be used.  

  




Output :  

(routine)  -  LDAP\_SUCCESS  - If the request was successfully sent, or another
LDAP result code if not.  

  

  

msgidp  -  Pointer to the message id of the request if the call succeeds. The
value is undefined if a value other than LDAP\_SUCCESS is returned.   This ID
can be used in subsequent calls to ldap\_result to obtain the result(s) of the
operation.  

  




 **See Also :**


**[ldap\_sasl\_bind\_s](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/77A8C62045FB561785256F5C00488A9E)**


**[LDAP\_SASL\_xxx](LDAP_SASL_xxx.md)**



----------------------------------------------------------------------------------------------------------


 





