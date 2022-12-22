




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



**Symbolic Value : LDAP**



**mod\_xxx** **-** The values
to add, delete, or replace.


**----------------------------------------------------------------------------------------------------------**



**#include <ldap.h>**


 **Symbolic Values :**      mod\_values   -  NULL terminated array of zero-terminated
strings.  

  

      mod\_bvalues            -  NULL terminated array of berval structures that
can be used to pass binary values such as images.  

  




**Description :**



The values
to add, delete, or replace.  Only one of the mod\_values or mod\_bvalues variants
can be used, selected by ORing the mod\_op field (see LPADMod) with the constant
LDAP\_MOD\_BVALUES (see LDAP\_MOD\_xxx).


 **See Also :**


**[LDAPMod](LDAPMod.md)**


**[mod\_vals\_u\_t](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/2D5C8D20A4DE48C185256ACE006AE3DF)**



----------------------------------------------------------------------------------------------------------


 





