##### Symbolic Value : LDAP
##### LDAP_OPT_xxx - LDAP options.
---
```
#include <ldap.h>
```

**Symbolic Values :**

	LDAP_OPT_API_INFO	  -  Used to retrieve some basic information about the LDAP API implementation at execution time. Set optionValue type to LDAPAPIInfo * for ldap_get_option. This option is READ-ONLY and cannot be set using ldap_set_option. See LDAPAPIInfo.

	LDAP_OPT_DEREF	  -  Determines how aliases are handled during search. See LDAP_DEREF_xxx. Set optionValue type to int * for ldap_get_option. Set optionValue type to int * for ldap_set_option.

	LDAP_OPT_SIZELIMIT	  -  A limit on the number of entries to return from a search. The default value for this option is LDAP_NO_LIMIT (see LDAP_NO_LIMIT.) Set optionValue type to int * for ldap_get_option. Set optionValue type to int * for ldap_set_option.

	LDAP_OPT_TIMELIMIT	  -  A limit on the number of seconds to spend on a search. The default value for this option is LDAP_NO_LIMIT(see LDAP_NO_LIMIT.) This value is passed to the server in the search request only; it does not affect how long the API implementation itself will wait locally for search results. Note that the timeout parameter passed to the ldap_search_ext_s or ldap_result functions can be used to specify a limit on how long the API implementation will wait for results. Set optionValue type to int * for ldap_get_option. Set optionValue type to int * for ldap_set_option.

	LDAP_OPT_PROTOCOL_VERSION	  -  This option indicates the version of the LDAP protocol used when communicating with the primary LDAP server. It SHOULD be one of the constants LDAP_VERSION2 (2) or LDAP_VERSION3 (3). If no version is set the default is LDAP_VERSION2 (2). Set optionValue type to int * for ldap_get_option. Set optionValue type to int * for ldap_set_option.

	LDAP_OPT_SERVER_CONTROLS	  -  A default list of LDAP server controls to be sent with each request. Set optionValue type to LDAPControl *** for ldap_get_option. Set optionValue type to LDAPControl ** for ldap_set_option.

	LDAP_OPT_CLIENT_CONTROLS	  -  A default list of client controls that affect the LDAP session. Set optionValue type to LDAPControl *** for ldap_get_option. Set optionValue type to LDAPControl ** for ldap_set_option.

	LDAP_OPT_API_FEATURE_INFO	  -  Used to retrieve version information about LDAP API extended features at execution time. Set optionValue type to LDAPAPIFeatureInfo * for ldap_get_option. This option is READ-ONLY and cannot be set using ldap_set_option.

	LDAP_OPT_HOST_NAME	  -  The host name (or list of hosts) for the primary LDAP server (see ldap_init for the definition of the hostname parameter for the allowed syntax.) Set optionValue type to char ** for ldap_get_option. Set optionValue type to char * for ldap_set_option.

	LDAP_OPT_RESULT_CODE	  -  The most recent local (API generated) or server returned LDAP result code that occurred for this session. Set optionValue type to int * for ldap_get_option. Set optionValue type to int * for ldap_set_option.

	LDAP_OPT_ERROR_STRING	  -  The message returned with the most recent LDAP error that occurred for this session. Set optionValue type to char ** for ldap_get_option. Set optionValue type to char * for ldap_set_option.

	LDAP_OPT_MATCHED_DN	  -  The matched DN value returned with the most recent LDAP error that occurred for this session. Set optionValue type to char ** for ldap_get_option. Set optionValue type to char * for ldap_set_option.

	LDAP_OPT_DEBUG_LEVEL	  -  The debug level to be set. See LDAP_DEBUG_API.

	LDAP_OPT_PRIVATE_EXTENSION_BASE	  -  Specify a new private or experimental option. Putting this new option in the specified range (0x4000 to 0x7FFF inclusive) will guarantee not to disturb any existing or new standards track options.


**Description :**

LDAP options that can be accessed or set using the functions ldap_get_option and ldap_set_option.  Type may differ dependant on whether option is to be accessed or set.


**See Also :**
[LDAP_DEBUG_API](/domino-c-api-docs/reference/Symb/LDAP_DEBUG_API)
[LDAP_DEREF_xxx](/domino-c-api-docs/reference/Symb/LDAP_DEREF_xxx)
[ldap_get_option](/domino-c-api-docs/reference/Func/ldap_get_option)
[LDAP_OPT_xxx](/domino-c-api-docs/reference/Symb/LDAP_OPT_xxx)
[LDAP_OPT_xxx (on/off)](/domino-c-api-docs/reference/Symb/LDAP_OPT_xxx (on/off))
[LDAP_OPT_xxx (SSL)](/domino-c-api-docs/reference/Symb/LDAP_OPT_xxx (SSL))
[ldap_set_option](/domino-c-api-docs/reference/Func/ldap_set_option)
---
