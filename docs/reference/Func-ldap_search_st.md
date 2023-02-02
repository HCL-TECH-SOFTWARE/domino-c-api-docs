##### Function : LDAP
##### ldap_search_st - Synchronous timed search of the LDAP directory.
---
##### #include <ldap.h>
int LNPUBLIC **ldap_search_st(**

	LDAP *ld,
	const char *base,
	int  scope,
	const char *filter,
	char **attrs,
	int  attrsonly,
	timeval  *timeout,
	LDAPMessage **res);
**Description :**
This function performs a synchronous search of the LDAP directory, with a 
specified timeout value, and returns a requested set of attributes for each 
entry matched.

Implemented as a macro:

#define ldap_search_st(ld, base, scope, filter, attrs, attrsonly, timeout, res) 
\
         ND_ldap_search_st((ld), (base), (scope), (filter), (attrs), 
(attrsonly), (timeout), (res))
**Parameters :**
Input :
ld  -  The LDAP session handle.

base  -  The distinguished name of the entry at which to start the search.

scope  -  The search scope.  See LDAP_SCOPE_xxx.

filter  -  A character string representing the search filter (e.g. "( |(cn=bob)(sn=bob))" ).  NULL can be passed to represent the filter "(objectclass=*)" which will match all entries.

attrs  -  A NULL-terminated array of strings indicating which attributes to return for each matching entry.  Passing NULL for this parameter causes all available user attributes to be retrieved.  See LDAP_xxx_ATTRS for additional attribute return requests.

attrsonly  -  A boolean value that MUST be zero if both attribute types and values are to be returned, and non-zero if only types are wanted.

*timeout  -  Specifies the local search timeout value (if it is NULL, the timeout is infinite).  If a zero timeout (where tv_sec and tv_usec are both zero - see timeval) is passed, API implementations SHOULD return LDAP_PARAM_ERROR.

Output :
(routine)  -  LDAP_SUCCESS  - If the request was successfully sent, or another LDAP result code if not.


res  -  The results of the search upon completion of the call.  The results opaque to the caller.  Entries, attributes, values, etc., can be extracted by calling the parsing routines. The results contained in res SHOULD be freed when no longer in use by calling ldap_msgfree.  

If an API error occurs or no results are returned, *res is set to NULL.

**See Also :**
[LDAP_SCOPE_xxx](D:/md_files/LDAP_SCOPE_xxx.md)
[LDAP_xxx_ATTRS](D:/md_files/LDAP_xxx_ATTRS.md)
[timeval](D:/md_files/timeval.md)
---
