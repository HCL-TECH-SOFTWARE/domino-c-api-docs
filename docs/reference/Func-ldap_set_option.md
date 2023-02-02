##### Function : LDAP
##### ldap_set_option - Used to set LDAP session preferences.
---
##### #include <ldap.h>
int LNPUBLIC **ldap_set_option(**

	LDAP *ld,
	int  optionToSet,
	void *optionValue);
**Description :**
This function is used to set the current value of various session-wide 
parameters.

Note that if automatic referral following is enabled (the default), any 
connections created during the course of following referrals will inherit the 
options associated with the session that sent the original request that caused 
the referrals to be returned.

Implemented as a macro:

#define ldap_set_option(ld, optionToSet, optionValue) ND_ldap_set_option((ld), 
(optionToSet), (optionValue))
**Parameters :**
Input :
ld  -  The session handle.  If this is NULL, a set of global defaults is accessed.  New LDAP session handles created with ldap_init or ldap_open inherit their characteristics from these global defaults.

optionToSet  -  The name of the option being accessed.  See LDAP_OPT_xxx.

optionValue  -  A pointer to the value the option is to be given. The actual type of this parameter depends on the setting of the option parameter.

Output :
(routine)  -  0 - Success.

-1 - Error: If -1 is returned by this function, a specific result code MAY be retrieved by calling ldap_get_option() with an option
value of LDAP_OPT_RESULT_CODE.  Note that there is no way to retrieve a more specific result code if a call to ldap_get_option() with an option
value of LDAP_OPT_RESULT_CODE fails. When a call to ldap_set_option() fails, it MUST NOT change the state of the LDAP session handle or the state of the underlying implementation in a way that affects the behavior of future LDAP API calls.


**Sample Usage :**
```
    WORD ldap_debug_level = 0;

    ldap_debug_level = LDAP_DEBUG_API;
    ldap_set_option (NULL, LDAP_OPT_DEBUG_LEVEL, &ldap_debug_level);
```
**See Also :**
[ldap_get_option](D:/md_files/ldap_get_option.md)
[LDAP_OPT_xxx](D:/md_files/LDAP_OPT_xxx.md)
---
