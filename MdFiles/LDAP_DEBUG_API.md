




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



**Symbolic Value : LDAP**



**LDAP\_DEBUG\_API** **-** LDAP debug
option.


**----------------------------------------------------------------------------------------------------------**



**#include <ldap.h>**



**Description :**



This is the
value  for LDAP\_OPT\_DEBUG\_LEVEL which can be set using the ldap\_set\_option
function.  Setting this option will cause the ldap api debug information to be
written out to the screen, and to a log file by specifying
"DEBUG\_OUTFILE=" and "LDAPDEBUG=1" parameters in the
notes.ini.


 **Sample Usage :**



WORD           ldap\_debug\_level
= 0;


 


ldap\_debug\_level
= LDAP\_DEBUG\_API;


ldap\_set\_option
(NULL, LDAP\_OPT\_DEBUG\_LEVEL, &ldap\_debug\_level);


 **See Also :**


**[LDAP\_OPT\_xxx](LDAP_OPT_xxx.md)**


**[ldap\_set\_option](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/9E2625CD7E72282B85256F5C00488A88)**



----------------------------------------------------------------------------------------------------------


 





