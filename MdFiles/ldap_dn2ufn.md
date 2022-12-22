




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



**Function : LDAP**



**ldap\_dn2ufn** **- Convert
the distinguished name into a more "user friendly" format.**


**----------------------------------------------------------------------------------------------------------**



**#include <ldap.h>**



char
\*LNPUBLIC **ldap\_dn2ufn(**  

      const char \*dn**);**



**Description :**



This
function is used to convert the distinguished name into a more "user
friendly" format.


 


Implemented
as a macro:


 


#define
ldap\_dn2ufn(dn)      ND\_ldap\_dn2ufn((dn)) 


 


**Parameters :**



Input :  

dn  -  The dn to convert, such as returned by ldap\_get\_dn.  

  




Output :  

(routine)  -  A newly allocated space containing the name in "user
friendly format" (UFN).  This space SHOULD be freed by a call to
ldap\_memfree when no longer in use.  

  

  




 **See Also :**


**[ldap\_get\_dn](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/BDD0B880523CEAF385256F5C00488A63)**


**[ldap\_memfree](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/F11748459A77A7EE85256F5C00488A7A)**



----------------------------------------------------------------------------------------------------------


 





