




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



**Symbolic Value : User**



**KFM\_pubkey\_xxx** **-** Specification
for the type of public key.


**----------------------------------------------------------------------------------------------------------**



**#include <kfm.h>**


 **Symbolic Values :**      KFM\_pubkey\_Primary           -  Primary key.  

  

      KFM\_pubkey\_International    -  International key.  

  




**Description :**



One of these
symbols is specified in the call to SECKFMGetPublicKey.  Every user (North
American and International) has both a Primary (long) and International (short)
key.  The Primary key is always used for authentication and signing.  The
International key is used if the encryptor or decryptor is an International
user.  The Primary key is used if both the encryptor and decryptor are North
American users.


 **See Also :**


**[SECKFMGetPublicKey](SECKFMGetPublicKey.md)**



----------------------------------------------------------------------------------------------------------


 





