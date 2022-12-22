




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



**ldap\_search\_ext\_s** **-
Synchronous search of the LDAP directory with controls.**


**----------------------------------------------------------------------------------------------------------**



**#include <ldap.h>**



int
LNPUBLIC **ldap\_search\_ext\_s(**  

      LDAP \*ld,  

      const char \*base,  

      int  scope,  

      const char \*filter,  

      char \*\*attrs,  

      int  attrsonly,  

      LDAPControl \*\*serverctrls,  

      LDAPControl \*\*clientctrls,  

      timeval  \*timeout,  

      int  sizelimit,  

      LDAPMessage \*\*res**);**



**Description :**



This
function performs a synchronous search, with controls, of the LDAP directory
and returns a requested set of attributes for each entry matched.


 


Implemented
as a macro:


 


#define
ldap\_search\_ext\_s(ld, base, scope, filter, attrs, attrsonly, serverctrls,
clientctrls, timeoutp, sizelimit, res) \   

              ND\_ldap\_search\_ext\_s((ld), (base), (scope), (filter), (attrs),
(attrsonly), (serverctrls), (clientctrls), (timeoutp), (sizelimit), (res))


 


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

  

serverctrls  -  Pointer to a list of LDAP server controls.  NULL if no server
controls are to be used.  

  

clientctrls  -  Pointer to a list of LDAP client controls.  NULL if no client
controls are to be used.  

  

\*timeout  -  Specifies both the local search timeout value and the operation
time limit that is sent to the server within the search request.  Passing a
NULL value for timeout causes the default timeout stored in the LDAP session
handle (set by using ldap\_set\_option() with the LDAP\_OPT\_TIMELIMIT parameter)
to be sent to the server with the request but an infinite local search timeout
to be used.  If a zero timeout (where tv\_sec and tv\_usec are both zero - see
timeval) is passed in, API implementations SHOULD return LDAP\_PARAM\_ERROR.  If
a zero value for tv\_sec is used but tv\_usec is non-zero, an operation time
limit of 1 SHOULD be passed to the LDAP server as the operation time limit. 
For other values of tv\_sec, the tv\_sec value itself SHOULD be passed to the
LDAP server.  

  

sizelimit  -  A limit on the number of entries to return from the search.  A
value of LDAP\_NO\_LIMIT means no limit.  

  




Output :  

(routine)  -  LDAP\_SUCCESS  - If the request was successfully sent, or another
LDAP result code if not.  

  

  

res  -  The results of the search upon completion of the call.  The results
opaque to the caller.  Entries, attributes, values, etc., can be extracted by
calling the parsing routines. The results contained in res SHOULD be freed when
no longer in use by calling ldap\_msgfree.    

  

If an API error occurs or no results are returned, \*res is set to NULL.  

  




 **See Also :**


**[LDAP\_NO\_LIMIT](LDAP_NO_LIMIT.md)**


**[LDAP\_OPT\_xxx](LDAP_OPT_xxx.md)**


**[LDAP\_SCOPE\_xxx](LDAP_SCOPE_xxx.md)**


**[LDAP\_xxx\_ATTRS](LDAP_xxx_ATTRS.md)**



----------------------------------------------------------------------------------------------------------


 





