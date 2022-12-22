




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




**Initial Release 8.5**



**Function : Security**



**SECidvResetUserPassword** **- Set a
password associated with a user's ID file stored in the ID vault.** 


**----------------------------------------------------------------------------------------------------------**



**#include <idvault.h>**



STATUS
LNPUBLICFUNC **SECidvResetUserPassword(**  

      char \*pServer,  

      char \*pUserName,  

      char \*pPassword,  

      WORD  wDownloadCount,  

      DWORD  ReservedFlags,  

      void \*pReserved**);**



**Description :**



This
password is required by the user when they recover their ID file from the ID
vault.


 


**Parameters :**



Input :  

pServer  -  Name of server to contact to request the password reset. Can be
NULL if executed from a program or agent on a server. Does NOT have to be a
vault server. But must be running Domino 8.5 or later.   

  

pUserName  -  Name of user to reset their vault id file password.  

  

pPassword  -  New password to set in the vault record for pUserName.  

  

wDownloadCount  -  If this user's effective policy setting document has
"allow automatic ID downloads" set to no, then this parameter
specifies how many downloads the user an now perform. If downloads are
automatic this setting should be zero.  

  

ReservedFlags  -  Must be set to zero.  

  

pReserved  -  Must be set to NULL.  

  




 


 




----------------------------------------------------------------------------------------------------------


 





