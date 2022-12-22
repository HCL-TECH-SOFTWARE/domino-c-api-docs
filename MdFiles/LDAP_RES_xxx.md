




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



**LDAP\_RES\_xxx** **-** Possible
result types a server can return.


**----------------------------------------------------------------------------------------------------------**



**#include <ldap.h>**


 **Symbolic Values :**      LDAP\_RES\_BIND     -  Result from a bind request.  

  

      LDAP\_RES\_SEARCH\_ENTRY          -  A single entry matched a previously
initiated search result.  

  

      LDAP\_RES\_SEARCH\_REFERENCE             -  When the search result is a
reference. (This was added in LDAP Version 3).  

  

      LDAP\_RES\_SEARCH\_RESULT        -  Either a result indicating the final
outcome of a previously initiated search operation or an entire chain of
entries matching the search operation along with a final outcome.  

  

      LDAP\_RES\_MODIFY            -  Result from a modify request.  

  

      LDAP\_RES\_ADD      -  Result from an add request.  

  

      LDAP\_RES\_DELETE            -  Result from a delete request.  

  

      LDAP\_RES\_MODRDN          -  Result from a modify relative distiguished
name request.  

  

      LDAP\_RES\_MODDN            -  Result from a modify distiguished name
request.  

  

      LDAP\_RES\_COMPARE        -  Result from a compare request.  

  

      LDAP\_RES\_EXTENDED       -  Result from an extended request.  

  

      LDAP\_RES\_ANY      -  Any other result.  

  




**Description :**



Possible
result types a server can return.  Upon successful completion, ldap\_result
returns the type of the first result. This will be one of the following
constants.


 **See Also :**


**[ldap\_result](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/D5FCB8AF5BD5605D85256F5C00488A6F)**



----------------------------------------------------------------------------------------------------------


 





