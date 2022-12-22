




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



**Function : LDAP**



**ldap\_search** **-
Asynchronous search of the LDAP directory.**


**----------------------------------------------------------------------------------------------------------**



**#include <ldap.h>**



int
LNPUBLIC **ldap\_search(**  

      LDAP \*ld,  

      const char \*base,  

      int  scope,  

      const char \*filter,  

      char \*\*attrs,  

      int  attrsonly**);**



**Description :**



This
function performs an asynchronous search of the LDAP directory and returns a
requested set of attributes for each entry matched.


 


Implemented
as a macro:


 


#define
ldap\_search(ld, base, scope, filter, attrs, attrsonly)    ND\_ldap\_search((ld),
(base), (scope), (filter), (attrs), (attrsonly))


 


**Parameters :**



Input :  

ld  -  The LDAP session handle.  

  

base  -  The distinguished name of the entry at which to start the search.  

  

scope  -  The search scope.  See LDAP\_SCOPE\_xxx.  

  

filter  -  A character string representing the search filter (e.g. "(
|(cn=bob)(sn=bob))" ).  NULL can be passed to represent the filter
"(objectclass=\*)" which will match all entries.  

  

attrs  -  A NULL-terminated array of strings indicating which attributes to
return for each matching entry.  Passing NULL for this parameter causes all
available user attributes to be retrieved.  See LDAP\_xxx\_ATTRS for additional
attribute return requests.  

  

attrsonly  -  A boolean value that MUST be zero if both attribute types and
values are to be returned, and non-zero if only types are wanted.  

  




Output :  

(routine)  -  Message ID - This ID can be used in subsequent calls to
ldap\_result to obtain the result(s) of the operation.  

  

-1 - If an error occurs.  

  

  




 **Sample Usage :**



char    \*attrs[]
= { "mail", "title", 0 };


msgid =
ldap\_search( ld, "c=us@o=UM", LDAP\_SCOPE\_SUBTREE,
"cn~=bob", attrs, attrsonly );


 **See Also :**


**[LDAP\_SCOPE\_xxx](LDAP_SCOPE_xxx.md)**


**[LDAP\_xxx\_ATTRS](LDAP_xxx_ATTRS.md)**



----------------------------------------------------------------------------------------------------------


 





