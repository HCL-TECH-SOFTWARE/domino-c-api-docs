




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




 


**Symbolic Value : Note**



**ENCRYPT\_xxx** **-** NSFNoteCopyAndEncrypt()
- EncryptFlags


**----------------------------------------------------------------------------------------------------------**



**#include <nsfnote.h>**


 **Symbolic Values :**      ENCRYPT\_WITH\_USER\_PUBLIC\_KEY        -  Encrypt the message
with the key in the user's ID. This flag is not for outgoing mail messages
because recipients, other than the sender, will not be able to decrypt the
message. This flag can be useful to encrypt documents in a local database to
keep them secure or to encrypt documents that can only be decrypted by the same
user.  

  

      ENCRYPT\_SMIME\_IF\_MIME\_PRESENT      -  Encrypt SMIME if MIME present.  

  

      ENCRYPT\_SMIME\_NO\_SENDER     -  Encrypt SMIME no sender.  

  

      ENCRYPT\_SMIME\_TRUST\_ALL\_CERTS     -  Encrypt SMIME trusting all
certificates.  

  




**Description :**



Optional
flag for NSFNoteCopyAndEncrypt.


 **See Also :**


**[NSFNoteCopyAndEncrypt](NSFNoteCopyAndEncrypt.md)**



----------------------------------------------------------------------------------------------------------


 





