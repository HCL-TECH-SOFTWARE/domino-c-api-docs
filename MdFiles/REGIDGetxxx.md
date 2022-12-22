




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



**Symbolic Value : User Registration**



**REGIDGetxxx** **-** Information
type codes for ID files.


**----------------------------------------------------------------------------------------------------------**



**#include <reg.h>**


 **Symbolic Values :**      REGIDGetUSAFlag   -  Return a Boolean value of size
sizeof(BOOL) that is TRUE if the ID is North American.  

  

      REGIDGetHierarchicalFlag   -  Return a Boolean value of size sizeof(BOOL)
that is TRUE if the ID is hierarchical.  

  

      REGIDGetSafeFlag   -  Return a Boolean value of size sizeof(BOOL) that is
TRUE if the ID is a safe copy.  

  

      REGIDGetCertifierFlag         -  Return a Boolean value of size
sizeof(BOOL) that is TRUE if the ID is a certifier.  

  

      REGIDGetNotesExpressFlag            -  Return a Boolean value of size
sizeof(BOOL) that is TRUE if the ID is a Notes Express ID.  

  

      REGIDGetDesktopFlag         -  Return a Boolean value of size sizeof(BOOL)
that is TRUE if the ID is desktop only.  

  

      REGIDGetName       -  Return the name from the ID file. The name may be 0
to MAXUSERNAME bytes in length.  

  

      REGIDGetPublicKey             -  Return the public key from the ID file.  

  

      REGIDGetPrivateKey            -  Return the private key from the ID file.  

  

      REGIDGetIntlPublicKey        -  Return the international public key from
the ID file.  

  

      REGIDGetIntlPrivateKey       -  Return the international private key from
the ID file.  

  




**Description :**



Information
type codes used by REGGetIDInfo() to identify the data items to be obtained
from an ID file.  

  

When an ID is made Safe, the Certifier, NotesExpress, and Desktop flags are
cleared, so these flags will always be FALSE in a Safe copy.  

  

Flat IDs do not distinguish between users and certifiers, so the Certifier flag
will always be FALSE if the Hierarchical flag is FALSE.


 **See Also :**


**[REGGetIDInfo](REGGetIDInfo.md)**



----------------------------------------------------------------------------------------------------------


 





