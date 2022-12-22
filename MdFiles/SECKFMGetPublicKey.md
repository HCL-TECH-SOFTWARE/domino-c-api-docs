




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




**Initial Release 4.0**



**Function : User**



**SECKFMGetPublicKey** **- Get the
certified public key for a  user.**


**----------------------------------------------------------------------------------------------------------**



**#include <kfm.h>**



STATUS
LNPUBLIC **SECKFMGetPublicKey(**  

      char far \*pName,  

      WORD  Function,  

      WORD  Flags,  

      DHANDLE far \*rethPubKey**);**



**Description :**



Retrieve the
certified public key for a given user name from the Address book or from the
Domino directory.  The function code is used to specify whether to retrieve the
certified public key for primary or international encryption.  The certified
public key is placed in a memory object allocated by Domino or Notes;  the
application is responsible for freeing this memory object.


 


The
certified public key includes the Public Key Certifier, the public key and the
Certifier Type.  If you just want to retrieve the public key that is stored in
the user's id file, use REGGetIDInfo.


 


**Parameters :**



Input :  

pName  -  Pointer to the null-terminated user name.  

  

Function  -  Function code specifying which public key to retrieve;  must be
one of the KFM\_pubkey\_xxx values.  

  

Flags  -  Reserved;  must be 0.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR - action successful  

ERR\_USER\_NOT\_FOUND - cannot find an Address book entry or Domino Directory
(Server's Address book) entry for that name.  

  

  

rethPubKey  -  The handle to the memory object containing the public key is
stored at this address.  

  




 **See Also :**


**[KFM\_pubkey\_xxx](KFM_pubkey_xxx.md)**


**[REGGetIDInfo](REGGetIDInfo.md)**



----------------------------------------------------------------------------------------------------------


 





