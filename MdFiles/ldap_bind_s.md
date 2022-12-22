




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Courier;
 panose-1:2 7 4 9 2 2 5 2 4 4;}
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



**ldap\_bind\_s** **- Initiate
a synchronous bind operation**


**----------------------------------------------------------------------------------------------------------**



**#include <ldap.h>**



int
LNPUBLIC **ldap\_bind\_s(**  

      LDAP \*ld,  

      const char \*who,  

      const char \*passwd,  

      int  authmethod**);**



**Description :**



This
function initiates a synchronous bind operation to bind to the ldap server.


 


Implemented
as a macro:


 


#define
ldap\_bind\_s(ld, who, cred, method)  ND\_ldap\_bind\_s((ld), (who), (cred),
(method))


 


**Parameters :**



Input :  

ld  -  The LDAP session handle.  

  

who  -  The distinguished name of the entry to bind as.  

  

passwd  -  Password of the entry to which to bind, depending on authentication
method.  

  

authmethod  -  Authentication method.  See LDAP\_AUTH\_xxx.  

  




Output :  

(routine)  -  LDAP\_SUCCESS  - If the request was successfully sent, or another
LDAP result code if not.  

  

  




 **Sample Usage :**


ldap\_bind\_s( ld,
"cn=manager, o=university of michigan, c=us", "secret",
LDAP\_AUTH\_SIMPLE )


 **See Also :**


**[ldap\_bind](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/3844B80F7F75E54985256F5C00488A50)**



----------------------------------------------------------------------------------------------------------


 





