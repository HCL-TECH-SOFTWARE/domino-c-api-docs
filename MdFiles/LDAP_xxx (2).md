




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



**LDAP\_xxx(2)** **-** Possible
error codes that can be returned.  (Continued)


**----------------------------------------------------------------------------------------------------------**



**#include <ldap.h>**


 **Symbolic Values :**      LDAP\_OTHER          -  Other.  

  

      LDAP\_SERVER\_DOWN        -  Server is down.  

  

      LDAP\_LOCAL\_ERROR         -  Local error.  

  

      LDAP\_ENCODING\_ERROR              -  Encoding error.  

  

      LDAP\_DECODING\_ERROR              -  Decoding error.  

  

      LDAP\_TIMEOUT      -  Timeout.  

  

      LDAP\_AUTH\_UNKNOWN     -  Auth unknown.  

  

      LDAP\_FILTER\_ERROR        -  Filter error.  

  

      LDAP\_USER\_CANCELLED   -  User has cancelled operation.  

  

      LDAP\_PARAM\_ERROR        -  Parameter error.  

  

      LDAP\_NO\_MEMORY            -  No memory.  

  

      LDAP\_CONNECT\_ERROR   -  Connect error.  

  

      LDAP\_NOT\_SUPPORTED    -  Not supported.  

  

      LDAP\_CONTROL\_NOT\_FOUND       -  Not found.  

  

      LDAP\_NO\_RESULTS\_RETURNED   -  No results returned.  

  

      LDAP\_MORE\_RESULTS\_TO\_RETURN        -  More results to return.  

  

      LDAP\_CLIENT\_LOOP           -  Client loop.  

  

      LDAP\_REFERRAL\_LIMIT\_EXCEEDED         -  Referral limit exceeded.  

  

      LDAP\_WILDCARD\_MINIMUM\_ERROR         -  Wildcard minimum error.  

  




**Description :**



Many of the
LDAP API routines return result codes, some of which indicate local API errors
and some of which are LDAP resultCodes that are returned by servers.  All of
the result codes are non-negative integers.


 




----------------------------------------------------------------------------------------------------------


 





