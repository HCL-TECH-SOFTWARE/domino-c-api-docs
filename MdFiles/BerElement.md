




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



**Data Type : Basic Encoding Rules;
LDAP**



**BerElement** **-** Holds date
and state information about encoded data.


**----------------------------------------------------------------------------------------------------------**



**#include
<lber.h>**



**Definition :**



typedef struct
berelement BerElement;


 


**Description :**



BerElement
represents data encoded using the Basic Encoding Rules (BER). BerElement is not
completely defined in ldap.h because the fields within the structure are not
intended to be accessible to clients. The BerElement structure is an opaque
structure. It contains not only a copy of the encoded value, but also state
information used in encoding or decoding.  Applications cannot allocate their
own BerElement structures.  The internal state is neither thread-specific nor
locked, so two threads should not manipulate the same BerElement value
simultaneously.  

  

A single BerElement value cannot be used for both encoding and decoding.


 **See Also :**


**[ldap\_first\_attribute](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/59B5D64DDCE3D2C085256F5C00488A67)**



----------------------------------------------------------------------------------------------------------


 





