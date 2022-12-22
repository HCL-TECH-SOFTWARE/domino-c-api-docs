




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



**ldap\_search\_st** **-
Synchronous timed search of the LDAP directory.**


**----------------------------------------------------------------------------------------------------------**



**#include <ldap.h>**



int
LNPUBLIC **ldap\_search\_st(**  

      LDAP \*ld,  

      const char \*base,  

      int  scope,  

      const char \*filter,  

      char \*\*attrs,  

      int  attrsonly,  

      timeval  \*timeout,  

      LDAPMessage \*\*res**);**



**Description :**



This
function performs a synchronous search of the LDAP directory, with a specified
timeout value, and returns a requested set of attributes for each entry
matched.


 


Implemented
as a macro:


 


#define
ldap\_search\_st(ld, base, scope, filter, attrs, attrsonly, timeout, res) \  

              ND\_ldap\_search\_st((ld), (base), (scope), (filter), (attrs),
(attrsonly), (timeout), (res))


 


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

  

\*timeout  -  Specifies the local search timeout value (if it is NULL, the
timeout is infinite).  If a zero timeout (where tv\_sec and tv\_usec are both
zero - see timeval) is passed, API implementations SHOULD return
LDAP\_PARAM\_ERROR.  

  




Output :  

(routine)  -  LDAP\_SUCCESS  - If the request was successfully sent, or another
LDAP result code if not.  

  

  

res  -  The results of the search upon completion of the call.  The results
opaque to the caller.  Entries, attributes, values, etc., can be extracted by
calling the parsing routines. The results contained in res SHOULD be freed when
no longer in use by calling ldap\_msgfree.    

  

If an API error occurs or no results are returned, \*res is set to NULL.  

  




 **See Also :**


**[LDAP\_SCOPE\_xxx](LDAP_SCOPE_xxx.md)**


**[LDAP\_xxx\_ATTRS](LDAP_xxx_ATTRS.md)**


**[timeval](timeval.md)**



----------------------------------------------------------------------------------------------------------


 





