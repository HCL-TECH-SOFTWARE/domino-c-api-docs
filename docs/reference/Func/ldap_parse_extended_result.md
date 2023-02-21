##### Function : LDAP
##### ldap_parse_extended_result - Check for an error of an asynchronous function.
---
```
#include <ldap.h>
int LNPUBLIC ldap_parse_extended_result(

	LDAP *ld,
	LDAPMessage *res,
	char **resultoidp,
	struct berval **resultdata,
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

#define ldap_parse_extended_result(ld, res, resultoidp, resultdata, freeit) \
         ND_ldap_parse_extended_result ((ld), (res), (resultoidp), 
(resultdata), (freeit))

**Parameters :**
Input :
ld  -  The LDAP session handle.

res  -  The result of an LDAP operation as returned by ldap_result or one of the synchronous API operation calls.

resultoidp  -  NULL, to ignore this field.

resultdata  -  NULL, to ignore this field.

freeit  -  A boolean that determines whether the result parameter is  disposed of or not.  If freeit is non-zero, the entire chain of messages represented by result is disposed of after extracting the requested information. This is provided as a convenience; zero can also be passed, to not free the messages, and ldap_msgfree can be used to free the result later.

Output :
(routine)  -  LDAP_SUCCESS  - If the request was successfully sent, or another LDAP result code if not.


resultoidp  -  The dotted-OID text representation of the name of the extended operation response.  This string SHOULD be disposed of by calling ldap_memfree.  If no OID was returned,  *resultoidp is set to NULL.

resultdata  -  A pointer to a struct berval containing the data in the extended operation response.  It SHOULD be disposed of by calling ber_bvfree.  If no data is returned, *resultdatap is set to NULL.


**See Also :**
[ber_bvfree](/domino-c-api-docs/reference/Func/ber_bvfree)
[ldap_memfree](/domino-c-api-docs/reference/Func/ldap_memfree)
[ldap_parse_result](/domino-c-api-docs/reference/Func/ldap_parse_result)
[ldap_parse_sasl_bind_result](/domino-c-api-docs/reference/Func/ldap_parse_sasl_bind_result)
---
