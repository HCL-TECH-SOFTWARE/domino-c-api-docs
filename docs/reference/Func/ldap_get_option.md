##### Function : LDAP
##### ldap_get_option - Used to get LDAP session preferences.
---
```
#include <ldap.h>
int LNPUBLIC ldap_get_option(

	LDAP *ld,
	int  optionToGet,
	void *optionValue);
```
**Description :**

This function is used to access the current value of various session-wide 
parameters.

Note that if automatic referral following is enabled (the default), any 
connections created during the course of following referrals will inherit the 
options associated with the session that sent the original request that caused 
the referrals to be returned.

Implemented as a macro:

#define ldap_get_option(ld, optionToGet, optionValue) ND_ldap_get_option((ld), 
(optionToGet), (optionValue))

**Parameters :**
Input :
ld  -  The session handle.

optionToGet  -  The name of the option being accessed.  See LDAP_OPT_xxx.

Output :
(routine)  -  0 - Success: The implementation MUST NOT change the state of the LDAP session handle or the state of the underlying implementation in a way that affects the behavior of future LDAP API calls.  When a call to ldap_get_option fails, the only session handle change permitted is setting the LDAP result code (as returned by the LDAP_OPT_RESULT_CODE option.)

-1 - Error: If -1 is returned by this function, a specific result code MAY be retrieved by calling ldap_get_option() with an option
value of LDAP_OPT_RESULT_CODE.  Note that there is no way to retrieve a more specific result code if a call to ldap_get_option() with an option
value of LDAP_OPT_RESULT_CODE fails. 


optionValue  -  The address of a place to put the value of the option. The actual type of this parameter depends on the setting of the option parameter.  For optionValues of type char ** and LDAPControl **, a copy of the data that is associated with the LDAP session ld is returned; callers should dispose of the memory by    calling ldap_memfree or ldap_controls_free, depending on the type of data returned.


**See Also :**
[ldap_controls_free](/domino-c-api-docs/reference/Func/ldap_controls_free)
[ldap_memfree](/domino-c-api-docs/reference/Func/ldap_memfree)
[ldap_set_option](/domino-c-api-docs/reference/Func/ldap_set_option)
[LDAP_xxx_INFO_VERSION](/domino-c-api-docs/reference/Symb/LDAP_xxx_INFO_VERSION)
---
