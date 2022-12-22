




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



**ldap\_delete\_ext** **- Initiate
an asynchronous ldap delete operation with controls.**


**----------------------------------------------------------------------------------------------------------**



**#include <ldap.h>**



int
LNPUBLIC **ldap\_delete\_ext(**  

      LDAP \*ld,  

      const char \*dn,  

      LDAPControl \*\*serverctrls,  

      LDAPControl \*\*clientctrls,  

      int \*msgidp**);**



**Description :**



This
function will initiate an asynchronous ldap delete operation with controls.


 


Note that
the entry to delete must be a leaf entry (i.e., it must have no children).
Deletion of entire subtrees in a single operation is not supported by LDAP.


 


Implemented
as a macro:


 


#define
ldap\_delete\_ext(ld, dn, sctrls, cctrls, msgidp)\


             
ND\_ldap\_delete\_ext((ld), (dn), (sctrls), (cctrls), (msgidp)) 


 


**Parameters :**



Input :  

ld  -  The LDAP session handle.  

  

dn  -  The distinguished name of the entry to delete.  If NULL, a zero length
DN is sent to the server.  

  

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

  




 




----------------------------------------------------------------------------------------------------------


 





