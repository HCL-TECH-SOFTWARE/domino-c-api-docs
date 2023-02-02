##### Function : LDAP
##### ldap_result - Obtain the result of a previous asynchronously initiated operation.
---
##### #include <ldap.h>
int LNPUBLIC **ldap_result(**

	LDAP *ld,
	int  msgid,
	int  all,
	struct timeval *timeout,
	LDAPMessage **result);
**Description :**
This function is used to obtain the result of a previous asynchronously 
initiated operation. 

Note that depending on how it is called, ldap_result can actually return a list 
or "chain" of result messages. The ldap_result function only returns messages 
for a single request, so for all LDAP operations other than search, only one 
result message is expected; that is, the only time the "result chain" can 
contain more than one message is if results from a search operation are 
returned.  Once a chain of messages has been returned to the caller, it is no 
longer tied in any caller-visible way to the LDAP request that produced it.  
However, it MAY be tied to the session handle.  Therefore, a chain of messages 
returned by calling ldap_result or by calling a synchronous search routine will 
never be affected by subsequent LDAP API calls except for ldap_msgfree (which 
is used to dispose of a chain of messages) and the unbind calls (which dispose 
of a session handle): ldap_unbind, ldap_unbind_s, or ldap_unbind_ext, or 
functions defined by extensions of this API.

Implemented as a macro:

#define ldap_result(ld, msgid, all, timeout, result) ND_ldap_result((ld), 
(msgid), (all), (timeout), (result))
**Parameters :**
Input :
ld  -  The LDAP session handle.

msgid  -  The message id of the operation whose results are to be returned.  See LDAP_RES_xxx.

all  -  Specifies how many messages will be retrieved in a single call  to ldap_result.  This parameter only has meaning for search results.  See LDAP_MSG_xxx.

timeout  -  A timeout specifying how long to wait for results to be returned.  A NULL value causes ldap_result to block until results are available.  A timeout value of zero seconds specifies a polling behavior.

Output :
(routine)  -  0 - If the timeout expired. 

-1 - If an error occurs, in which case the error parameters of the LDAP session handle will be set accordingly.


result  -  A result parameter that will contain the result(s) of the operation.  See LDAP_RES_xxx.  If an API error occurs or no results are returned, *result is set to NULL.

**See Also :**
[ldap_msgfree](D:/md_files/ldap_msgfree.md)
[ldap_msgid](D:/md_files/ldap_msgid.md)
[ldap_msgtype](D:/md_files/ldap_msgtype.md)
[LDAP_MSG_xxx](D:/md_files/LDAP_MSG_xxx.md)
[LDAP_RES_xxx](D:/md_files/LDAP_RES_xxx.md)
---
