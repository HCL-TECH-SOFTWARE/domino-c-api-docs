




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



**ldap\_simple\_bind** **- Initiate
an asynchronous simple bind operation**


**----------------------------------------------------------------------------------------------------------**



**#include <ldap.h>**



int
LNPUBLIC **ldap\_simple\_bind(**  

      LDAP \*ld,  

      const char \*who,  

      const char \*credentials**);**



**Description :**



This
function initiates an asynchronous bind operation to bind to the ldap server
using simple authentication.


 


Implemented
as a macro:


 


#define
ldap\_simple\_bind(ld, who, passwd)              ND\_ldap\_simple\_bind((ld), (who),
(passwd))


 


**Parameters :**



Input :  

ld  -  The LDAP session handle.  

  

who  -  The distinguished name of the entry to bind as.  

  

credentials  -  Password of the entry to which to bind.  

  




Output :  

(routine)  -  Message ID - This ID can be used in subsequent calls to
ldap\_result to obtain the result(s) of the operation.  

  

-1 - If an error occurs.  

  

  




 **Sample Usage :**


ldap\_simple\_bind( ld,
"cn=manager, o=university of michigan, c=us",
"ManagerPassword" )


 **See Also :**


**[ldap\_simple\_bind\_s](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/83B177C9401D75A585256F5C00488A8A)**



----------------------------------------------------------------------------------------------------------


 





