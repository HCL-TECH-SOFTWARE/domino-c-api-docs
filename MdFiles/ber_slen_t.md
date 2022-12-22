




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



**ber\_slen\_t** **-** Used for
passing lengths to/from the API.


**----------------------------------------------------------------------------------------------------------**



**#include
<lber.h>**



**Definition :**



typedef long
ber\_slen\_t;


 


**Description :**



The
ber\_slen\_t type is the signed variant of the ber\_len\_t integral type. Note that
ber\_slen\_t is not used directly in the LDAP C API but is provided for the
convenience of application developers and for use by extensions to the API.


 **See Also :**


**[ber\_len\_t](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/5E4AA411D51AEE8685256ACB0066FB61)**



----------------------------------------------------------------------------------------------------------


 





