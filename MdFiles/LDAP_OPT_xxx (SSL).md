




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



**LDAP\_OPT\_xxx (SSL)** **-** LDAP
options.


**----------------------------------------------------------------------------------------------------------**



**#include <ldap.h>**


 **Symbolic Values :**      LDAP\_OPT\_REFERRALS     -  Determines whether the LDAP
library automatically follows referrals returned by LDAP servers or not. It MAY
be set to one of the constants LDAP\_OPT\_ON or LDAP\_OPT\_OFF (see
LDAP\_OPT\_xxx(on/off)); any non-NULL pointer value passed to ldap\_set\_option
enables this option. When reading the current setting using ldap\_get\_option, a
zero value means OFF and any non-zero value means ON. By default, this option
is ON. Set optionValue type to int \* for ldap\_get\_option. Set optionValue type
to void \* (LDAP\_OPT\_ON or LDAP\_OPT\_OFF) for ldap\_set\_option.  

  

      LDAP\_OPT\_RESTART         -  Determines whether LDAP I/O operations are
automatically restarted if they abort prematurely. It MAY be set to one of the
constants LDAP\_OPT\_ON or LDAP\_OPT\_OFF (see LDAP\_OPT\_xxx(on/off)); any non-NULL
pointer value passed to ldap\_set\_option() enables this option. When reading the
current setting using ldap\_get\_option, a zero value means OFF and any non-zero
value means ON. This option is useful if an LDAP I/O operation can be
interrupted prematurely, for example by a timer going off, or other interrupt.
By default, this option is OFF. Set optionValue type to int \* for
ldap\_get\_option. Set optionValue type to void \* (LDAP\_OPT\_ON or LDAP\_OPT\_OFF)
for ldap\_set\_option.  

  

      LDAP\_OPT\_SSL       -  Use SSL for client connections.  

  




**Description :**



LDAP options
that can be accessed or set using the functions ldap\_get\_option and
ldap\_set\_option.  Type may differ dependant on whether option is to be accessed
or set.


 **See Also :**


**[ldap\_get\_option](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/611E3525171346C185256F5C00488A5E)**


**[LDAP\_OPT\_xxx](LDAP_OPT_xxx.md)**


**[LDAP\_OPT\_xxx (on/off)](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/F10E0AB16DF5B1E985256ACC007084E6)**


**[LDAP\_OPT\_xxx (SSL)](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/8127200C14817DC185256ACD004F8C5A)**


**[ldap\_set\_option](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/9E2625CD7E72282B85256F5C00488A88)**



----------------------------------------------------------------------------------------------------------


 





