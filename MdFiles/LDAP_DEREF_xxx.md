




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



**LDAP\_DEREF\_xxx** **-** Dereferencing
aliases


**----------------------------------------------------------------------------------------------------------**



**#include <ldap.h>**


 **Symbolic Values :**      LDAP\_DEREF\_NEVER         -  Aliases never dereferrenced.  

  

      LDAP\_DEREF\_SEARCHING             -  Aliases should be dereferenced during
the search, but not when locating the base object of the search.  

  

      LDAP\_DEREF\_FINDING       -  Aliases should be dereferenced when locating
the base object of the search, but not during the search.  

  

      LDAP\_DEREF\_ALWAYS       -  Aliases always dereferrenced.  

  




**Description :**



Dereferencing
aliases relating to LDAP\_OPT\_DEREF.  See LDAP\_OPT\_xxx.


 **See Also :**


**[LDAP\_OPT\_xxx](LDAP_OPT_xxx.md)**



----------------------------------------------------------------------------------------------------------


 





