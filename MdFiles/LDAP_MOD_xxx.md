




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



**LDAP\_MOD\_xxx** **-** Determine
which values to add, delete, or replace.


**----------------------------------------------------------------------------------------------------------**



**#include <ldap.h>**


 **Symbolic Values :**      LDAP\_MOD\_ADD     -  Values are added to the entry, creating
the attribute if necessary.  

  

      LDAP\_MOD\_DELETE           -  Values are deleted from the entry, removing
the attribute if no values remain. If the entire attribute is to be deleted,
the mod\_vals field can be set to NULL.  

  

      LDAP\_MOD\_REPLACE         -  Attribute will have the listed values after
the modification, having been created if necessary, or removed if the mod\_vals
field is NULL. All modifications are performed in the order in which they are
listed.  

  

      LDAP\_MOD\_BVALUES         -  BER values.  

  




**Description :**



Determine
which values to add, delete, or replace.


 **See Also :**


**[LDAPMod](LDAPMod.md)**



----------------------------------------------------------------------------------------------------------


 





