##### Function : LDAP
##### ldap_parse_result - Check for an error of an asynchronous function.
---
```
#include <ldap.h>
int LNPUBLIC ldap_parse_result(

	LDAP *ld,
	LDAPMessage *result,
	int *errorcodep,
	char **matcheddnp,
	char **errmsgp,
	char ***referralsp,
	LDAPControl ***serverctrlsp,
	int  freeit);
```
**Description :**

This function will extract information from results and handle errors returned 
by other LDAP API routines.  

Note that ldap_parse_sasl_bind_result() and ldap_parse_extended_result must 
typically be used in addition to ldap_parse_result to retrieve all the result 
information from SASL Bind and Extended Operations respectively.  The 
ldap_parse_result, ldap_parse_sasl_bind_result, and
ldap_parse_extended_result functions all skip over messages of type 
LDAP_RES_SEARCH_ENTRY and LDAP_RES_SEARCH_REFERENCE when looking for a result 
message to parse.  See LDAP_RES_xxx.  If a chain of messages that contains more 
than one result message is passed to these routines they always operate on the 
first result in the chain.

Implemented as a macro:

#define ldap_parse_result(ld, result, errcodep, matcheddnp, errmsgp, 
referralsp, serverctrlsp, freeit) \
	        ND_ldap_parse_result((ld), (result), (errcodep), (matcheddnp), 
(errmsgp), (referralsp), (serverctrlsp), (freeit))

**Parameters :**
Input :
ld  -  The LDAP session handle.

result  -  The result of an LDAP operation as returned by ldap_result or one of the synchronous API operation calls.

errorcodep  -  NULL, to ignore this field.

matcheddnp  -  NULL, to ignore this field.

errmsgp  -   NULL, to ignore this field.

referralsp  -  NULL, to ignore this field.

serverctrlsp  -  NULL, to ignore this field.

freeit  -  A boolean that determines whether the result parameter is  disposed of or not.  If freeit is non-zero, the entire chain of messages represented by result is disposed of after extracting the requested information. This is provided as a convenience; zero can also be passed, to not free the messages, and ldap_msgfree can be used to free the result later.

Output :
(routine)  -  LDAP_SUCCESS  - If the request was successfully sent, or another LDAP result code if not.


errorcodep  -  The LDAP  resultCode field from the LDAPMessage message.  This is the indication from the server of the outcome of the operation.

matcheddnp  -  If the server returned a matchedDN string to indicate how much of a name passed in a request was recognized, this result parameter will be filled in with that matchedDN string.  The matched DN string SHOULD be freed by calling ldap_memfree.  Note that the server may return a zero length matchedDN (in which case *matchednp is set to an allocated copy of "") which is different than not returning a value at all (in which case *matcheddnp is set to NULL).

errmsgp  -  This result parameter will be filled in with the contents of the error message field from the LDAPMessage message.  The error message string SHOULD be freed by calling ldap_memfree. 

referralsp  -  This result parameter will be filled in with the contents of the referrals field from the LDAPMessage message, indicating zero or more alternate LDAP servers where the request is to be retried.  The referrals array SHOULD be freed by calling ldap_value_free.   If no referrals were returned, *referralsp is set to NULL.

serverctrlsp  -  This result parameter will be filled in with an allocated array of controls copied out of the LDAPMessage message.  The control array SHOULD be freed by calling ldap_controls_free.  If no controls were returned, *serverctrlsp is set to NULL.


**See Also :**
[ldap_controls_free](/reference/Func/ldap_controls_free)
[ldap_memfree](/reference/Func/ldap_memfree)
[ldap_parse_extended_result](/reference/Func/ldap_parse_extended_result)
[ldap_parse_sasl_bind_result](/reference/Func/ldap_parse_sasl_bind_result)
[ldap_result](/reference/Func/ldap_result)
[LDAP_RES_xxx](/reference/Symb/LDAP_RES_xxx)
[ldap_value_free](/reference/Func/ldap_value_free)
---
